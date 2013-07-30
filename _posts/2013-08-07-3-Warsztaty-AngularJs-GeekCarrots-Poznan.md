---
layout: default
category: warsztaty
title: 3 Warsztaty AngularJs - GeekCarrots Poznań
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

```html
<quote ws-unselectable>Copyright protected piece of thought</quote>
```

```js
return {
  restrict: 'A',
  link: function postLink(scope, element, attrs) {
    element.bind('mousedown', function(e) {
      e.preventDefault();
    }); 
    element.bind('selectstart', function(e) {
      e.preventDefault();
    }); 
  }
```

## Kontrolka w directive
* git checkout slide-2
* użycie: app/views/shortcuts.html
* directive z reużywajną kontrolką

```html
<div ws-shortcut-input ws-label="Special key + 1"></div>
<div ws-shortcut-input ws-label="Special key + 2"></div>
```

## Nieizolowane scopy
* git checkout slide-3
* chrome: #/shortcuts
* wszystkie kontrolki działają na tym samym modelu
* pliki: app/scripts/directives/ws-shortcut-input.js

```js
return {
  template: '{{label}}: <input ng-model="number" />',
  restrict: 'A',
  link: function (scope, element, attrs)  {
    scope.label = attrs.wsLabel;
  }
```

## Izolowane scopy
* git checkout slide-4
* Każdy element żyje w swoim świecie
* nie mamy kolizji między tymi samymi elementami w tym samym scopie
* do komunikacji ze światem zewnętrznym
 * @ - podstawia wartość atrybutu z elementu
 * = - wiąże dwustronnie wewnętrzną i zewnętrzną wartość
* pliki: app/scripts/directives/ws-shortcut-input.js +9

```js
return {
  template: '{{label}}: <input ng-model="number" />',
  restrict: 'A',
  scope: {
    label: '@wsLabel',
    number: '=ngModel'
  }
```

## Zadanie 1: kontrolka dla filtru przedziału
* git checkout todo-1
* użycie: app/views/showContacts.html +8
* implementacja: app/scripts/directives/ws-interval.js
* enkapsulacja dwóch suwaków w reużywalną kontrolkę

```html
<fieldset ws-interval min="20" max="40" ng-model="interval">
</fieldset>
```

## Rozwiązanie 1
* git add .
* git commit -m '(commit message)'
* git checkout done-1
* Pytania?

```js
return {
  template: 'Min: <input type="range" max="{{max}}" min="{{min}}" ng-model="model.min"> {{model.min}}' +
      ' <br> Max: <input type="range" max="{{max}}" min="{{min}}" ng-model="model.max"> {{model.max}}',
    scope: {
    min: '@',
    max: '@',
    model: '=ngModel'
  },
  restrict: 'A',
  link: function (scope, element, attrs) {
    scope.model = {
      min: scope.min,
      max: scope.max
    };
  }
```

## Hack
* git checkout slide-5
* hack żeby nie dało się min przekroczyć max
* implementacja: app/scripts/directives/ws-interval.js +9

```js
template: 'Min: <input type="range" max="{{model.max}}" min="{{min}}" ng-model="model.min"> {{model.min}}' +
          ' <br> Max: <input type="range" max="{{max}}" min="{{model.min}}" ng-model="model.max"> {{model.max}}'
```





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

## TODO Zadanie 4 z 



## Koncepcje
1. directives
 * izolowanie scope - wywoływanie funcji
  * &

2. Unit testy
 * runner page
3. angular-ui
 * mask (slide)
 * key-pres (slide)
 * scroll fix (slide)
 * nested routes (zadanie 3)
4. Angular bootstrap
 * pagination
 * tooltip
 * dialog

## ngPoznan
* grupa mailingowa
* info o eventach w pobliżu
* wymiana doświadczeń
* semi regularne spotkania w ramacha hacking Poznań


5. digest & apply
6. yeoman
 * przejście na serwer yeomana
 * karma



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
