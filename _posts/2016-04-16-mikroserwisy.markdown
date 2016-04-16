---
published: false
title: Mikroserwisy
layout: post
tags: [typescript]
---
# Problem: Jak wymusić statyczne pole w klasie?
Do fabryki przekazuję klasę. Fabryka będzie produkowała egzemplarze (obiekty) danej klasy. Potrzebuję jednak dodatkowych "parametrów" - np. nazwy związanej z daną klasą. Taka sytuacja zaistniała gdy stworzyłem sobie abstrakcyjną klasę modułu (Angular), do której przekazywałem klasę serwisu. Otrzymała ona postać:

`addService(serviceName :string; serviceClass :Function) void;`

Wygląda to dokładnie tak jak rejestracja serwisu w JavaScripcie. Chciałem jednak by nazwa serwisu była bardziej związana z klasą serwisu - w związku z tym powinna być deklarowana w samej klasie serwisu. Potrzebowałbym również jakiegoś mechanizmu wymuszającego dodanie nazwy w klasie serwisu. W idealnym świecie wyglądałoby to mniej więcej tak:

```typescript
interface IService {
  static $name :string;
}

class MyService implements IService {
  $name :string; 
}

module.addService(MyService);
```

Niestety świat nie jest idealny i TypeScript nie dopuszcza statycznych pól w interfejsie. Możemy jedna je wymóc w ten sposób:

```typescript
interface IService {
  $name :string;
}
class MyService {
  static $name :string; 
}

class Module {
  addService(sercieClass :IService) :void {
  }
}

let module = new Module();
module.addService(MyService);
```
Powyższy kod wymusza na MyService aby miał statyczne pole `$name` - w przypadku jego braku zwracany jest błąd. Jak widać wymuszamy pole statyczne nie w samej klasie `MyService` -  w której chcielibyśmy je wymusić ale w klasach, które z niej korzystają. 

A oto skompilowany kod z przykładem:

https://gist.github.com/krzyjez/e3a2c116499ed958b7f4.js
