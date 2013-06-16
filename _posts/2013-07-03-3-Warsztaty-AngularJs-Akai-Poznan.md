---
layout: default
category: warsztaty
title: Warsztaty AngularJs Akai Poznań
published: false
tags: [AngularJs, Akai, Poznań]
---
# AngularJs: Warsztaty - stopień 3


## Podpinanie js do html
* zawsze korzystamy z directive!

## Directive blokujący zaznaczanie i klikanie na element
* git checkout slide-1
* użycie: app/views/page.html +3
* implementacja: app/scripts/directives/ws-unselectable.js

## Kontrolka w directive
* git checkout slide-2
* użycie: app/views/shortcuts.html
* directive z reużywajną kontrolką

## Nieizolowane scopy
* git checkout slide-3
* chrome: #/shortcuts
* wszystkie kontrolki działają na tym samym modelu

## Izolowane scopy
* git checkout slide-4
* Każdy element żyje w swoim świecie
* nie mamy kolizji między tymi samymi elementami w tym samym scopie
* do komunikacji ze światem zewnętrznym
 * @ - podstawia wartość atrybutu z elementu
 * = - wiąże dwustronnie wewnętrzną i zewnętrzną wartość

## Zadanie 1: kontrolka dla filtru przedziału
* git checkout todo-1
* użycie: app/views/showContacts.html
* implementacja: app/scripts/directives/ws-interval.js
* enkapsulacja dwóch suwaków w reużywalną kontrolkę

## Rozwiązanie 1
* git add .
* git commit -m '(commit message)'
* git checkout done-1
* Pytania?

## Hack
* git checkout slide-5
* hack żeby nie dało się min przekroczyć max
* implementacja: app/scripts/directives/ws-interval.js +9


## Serwer yeomanowy
* TODO sprawdzić instalacje na czystym linuxie
* TODO sprawdzić instalacje na czystym windowsie

## Unit testy - idea
* trywialne sprawdzanie działania kody
* weryfikujemy wyizolowaną logikę
* razem z code review bardzo skuteczny mechanizm łapanie błędów

## Unit testy - Angular
* karma test runner
* page runner

## TODO Zadanie 2 z unit testami

## angular-ui

## TODO Zadanie 3 z nested routes



## Koncepcje
1. directives
 * izolowanie scope - wywoływanie funcji
  * &
2. yeoman
 * przejście na serwer yeomana

3. Unit testy
 * runner page
 * karma
4. angular-ui
 * mas (slide)
 * key-pres (slide)
 * scroll fix (slide)
 * nested routes (zadanie 3)
5. Angular bootstrap
 * pagination
 * tooltip
 * dialog

## ngPoznan
* grupa mailingowa
* info o eventach w pobliżu
* wymiana doświadczeń


6. digest & apply



## Co dalej?

Pierwsze warsztaty będą wprowadzeniem do świata frontendowych aplikacji. Następne spotkania będą poruszać takie tematy jak:

* webstorage i inne js api
* komunikacja z 'backendem'
* optymalne środowsko programistyczne
* unit testy i testowalność aplikacji

## Temat 
* htmlowy silnik do gier:
http://news.turbulenz.com/post/49430669886/turbulenz-engine-goes-open-source

* indexDb
 * key-value
 * transaction
 * indexed properties
 * http://www.html5rocks.com/en/tutorials/indexeddb/todo/
* webworker
 * heavy computation
* websocket
 * http://www.html5rocks.com/en/tutorials/frameworks/angular-websockets/
 * http://www.netmagazine.com/tutorials/angularjs-collaboration-board-socketio

* full screen api
* cache manifest

* pointer locking api
* loading local data api
* geolokalizacja
* battery status
* chrome application (package app)
* Chromium Embedded Framewor
* commertial apps:
  * spotify? access to music
* no backend - firebase:
 http://ngmodules.org/modules/angularFire

## Project
1. książka kontaktów
 * lista
 * paginacja
 * search
 * dodawanie
