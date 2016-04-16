---
published: true
title: Mikroserwisy
layout: post
---
Inspiracja
--------------

Ostatnio wpadła mi w ręce książka Sam’a Newman’a “Building Microservices”. Odnosi się ona do architektury systemów rozporoszonych, których głównym elementem są tytułowe mikroservisy. Autor definiuje je jako osobne procesy systemowe uruchamiane na tym samym komputerze lub komputerze lub na odrębnych komputerach w sieci lokalnej lub w chmurze. Zaletą tej architektury jest skalowalność, łatwość rozbudowy i modyfikacji, odporność na awarie. Dla mnie kluczową zaletą jest łatwość percepcyjna. Wydaje mi się, że łatwiej jest zrozumieć system w którym mamy do czynienia z niewielkimi, stosunkowo prostymi, precyzyjnie wydzielonymi “jednostkami działania” (mikrousługami) komunikującymi się między sobą wg. ściśle określonego api niż wielki monolityczny system z wieloma nieoczywistymi zależnościami wewnętrznymi. Konieczność utworzenia interfejsu API komunikacji między mikroserwisami wymusza klarowność interakcji. W systemie monolitycznym mamy wprawdzie klasy - które można by uznać za analogiczne “cegiełki”. Jednak łatwość z jaką klasy mogą się między sobą komunikować sprawia, że relacji zależności robi się bardzo dużo i mogą być bardzo zagmatwane. 