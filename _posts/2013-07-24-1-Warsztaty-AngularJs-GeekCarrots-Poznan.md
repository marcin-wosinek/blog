---
layout: default
category: warsztaty
title: Warsztaty AngularJs 1 - GeekCarrots Poznań
tags: [AngularJs, GeekCarrots, Poznań]
---
# AngularJs: Warsztaty - stopień 1
## Start
* treść slajdów: [http://bit.ly/angular-workshop-1](http://bit.ly/angular-workshop-1)
* git clone [https://github.com/marcin-wosinek/workshop-1.git](https://github.com/marcin-wosinek/workshop-1.git)
* chrome:
 * linux: chromium-browser --disable-web-security
 * windows - skopiować link do chroma i edytować: "(originalny link) --disable-web-security"
* git config --global alias.tree "log --oneline --graph --decorate --all"

## AngularJs "Hello world"
* git checkout slide-1
* dwu stronne bindowanie
* działający, nie trywialny kod oparty o sam widok
* pliki: index.html +8

## ng-include
* git checkout slide-2
* wczytywanie cześci widoku dynamicznie
* pliki: views/main.html & index.html +7

## Kontroler
* wiąże 'swój' widok z resztą aplikacji
* zawiera prostą logikę, związaną z samym wyświetlaniem

## $scope
* obiekt wiążący kontroler z widokiem
* $scope.title będzie dostępny jako {{title}} w widoku
* ng-model - wiąże elementy formularza z modelem
* ng-repeat - pozwala interować po tablicach zdefiniowanych na $scope

## ng-controller
* git checkout slide-3
* podpięcie kontrolera do częsci widoku
* $scope działa tylko wewnątrz tagu na którym jest kontroler
* pliki: views/hello.html & script/script.js

## Zadanie 1
* git checkout todo-1
* dodanie kontrolera zawierajacego menu
* dodanie i wyświetlenie menu w index.html
* implementacja: index.html & script/script.js

## Rozwiązanie 1
* git add .
* git commit -m '(commit message)'
* git checkout done-1

## $routeProvider
* git checkout slide-4
* definije ścieżki w aplikacji
* pliki: scripts/script.js

## ng-repeat
* directive pętla

```js
<ul>
  <li ng-repeat="project in projects">
    <a href="{{project.site}}">{{project.name}}</a>: {{project.description}}
  </li>
</ul>
```

## Zadanie 2
* git checkout todo-2
* zbudować menu zawierające linki do wszystkich ścieżek
* implementacja: index.html & script/script.js

```js
var object = {};
var array = [];

var arrayOfObjects = [
  {
    lorem: 1,
    ipsum: 2
  },
  {
    test: 4
  }
]
```

## Rozwiązanie 2
* git add .
* git commit -m '(commit message)'
* git checkout done-2

## Zadanie 3
* git checkout todo-3
* zbudować własną podstronę, z wyświletaniem listy danych podanych w kontrolerzę
* implementacja: script/script.js & nowy plik widoku

## Rozwiązanie 3
* git add .
* git commit -m '(commit message)'
* git checkout done-3

## OrderBy
* git checkout slide-5
* pliki: views/list.html

```html
<ul>
  <li ng-repeat="product in products | orderBy:'price'">
</ul>
```

## Zadanie 4
* git checkout todo-4
* wymień hardkodowany parametr na pochodzący ze zmiennej
* użyj ng-model + kilka input type="radio"
* implementacja: views/list.html +4

## Rozwiązanie 4
* git add .
* git commit -m '(commit message)'
* git checkout done-4

## filter
* git checkout slide-6
* składnia filter: {experesion}
* pliki: views/list.html +7

```html
<tr ng-repeat="person in list | orderBy:orderKey | filter:'oo'"
```

## filter - argumenty
{expresion} zwraca:

* string 'Lorem ipsum' - szukamy stringu w całych obiektach na liście
* obiekt {key: 'value'} - szukamy obietków które pod *key* mają wartośc pasującą do _value_ 
* obiekt {$: 'value'} - szukamy obietków które gdziekolwiek mają wartośc pasującą do _value_ 

## Zadanie 5
* git checkout todo-5
* zmienić filter na wyszukiwarkę z 3 polami: szukanie po firstName, lastName lub wszędzie
* implementacja: views/list.html +5

## Rozwiązanie 5
* git add .
* git commit -m '(commit message)'
* git checkout done-5

## Funkcje w modelu
* git checkout slide-7
* pliki: views/main.html +7 & script/script.js + 37

```html
<p>{ {displayValueReturnedByFunction()} }</p>

<input ng-change="fireFunctionWhenChangeHappen()">
```

## Validowanie formularza
* git checkout slide-8
* pliki: views/main.html +10

## Zadanie 6
* git checkout todo-6
* dodać formularz z danym osoby - obiekt newPerson
* skorzystać z _ng-click_ do obsługi dodanie
  * dodać do listy newPerson ( nazwaListy.push(nowyElement) )
  * podstawić pusty obiekt za ten podstawiony
* implementacja: script/script.js +46 & views/list.html +10

## Rozwiązanie 6
* git add .
* git commit -m '(commit message)'
* git checkout done-6

## Trzymanie danych w controlerze
* git checkout slide-9
* strata danych przy przejściu na inną podstronę
* użycie tego samego controlera 2 razy - jak na #/main
* pliki: script/script.js +29 & views/main.html +1

## Services
* git checkout slide-10
* nowy serwis - dla kontrolera co 2 razy wystepuje
* stan jest globalny dla aplikacji
* pliki: script/script.js +62 & views/hello.html +4 & views/main.html +7

## Zadanie 7
* git checkout todo-7
* dodanie własnego serwisu, People do użytku przez ListCtrl
* implementacja: script/script.js +42

## Rozwiązanie 7
* git add .
* git commit -m '(commit message)'
* git checkout done-7

## Json - obiekty

```json
{
  "about": "I'm an object",
  "structure": {
    "key": "value"
  },
  "arrays": [ "I", "can", "keep", "them", "too" ]
}
```

## Json - tablice

```json
[
  {
    "objectId": 1
  },
  {
    "objectId": 2
  },
  {
    "objectId": 3
  }
]
```

## Rest
* dane dostepne pod url
* ładne url:
 * http://example.com/products - lista produktów
 * http://example.com/products/1 - pierwszy product
* na ogół dane w json

## $resource
* query - pobieranie tablicy
* get - pobiernie objektu
* parametry

```js
var userResource = $resource('/user/:userId', {});
userResource.get({userId: 1});
```

## Dane do json
* git checkout slide-11
* pliki:
 * nowa zależność: index.html & script/angular/angular-resource.js
 * dane: data/people
 * pobieranie: script/script.js +42

## Podsumowanie
* kontroler?
* widok?
* route?
* serice?

## Materiały do nauki
* [http://docs.angularjs.org/tutorial/](http://docs.angularjs.org/tutorial/)
* [http://egghead.io/](http://egghead.io/)

## Co dalej?

Pierwsze warsztaty będą wprowadzeniem do świata frontendowych aplikacji. Następne spotkania będą poruszać takie tematy jak:

* webstorage i inne js api
* komunikacja z 'backendem'
* optymalne środowsko programistyczne
* unit testy i testowalność aplikacji

## Stay tuned
* [http://akai.org.pl/](http://akai.org.pl/)
* [http://poznan.gtug.pl/](http://poznan.gtug.pl/)
* [http://www.meetup.com/Hacking-Poznan/](http://www.meetup.com/Hacking-Poznan/)
