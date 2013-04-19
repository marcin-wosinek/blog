---
layout: default
category: warsztaty
title: Warsztaty AngularJs Akai Poznań
tags: [AngularJs, Akai, Poznań]
---
# AngularJs: Warsztaty - stopień 1
## Start
* treść slajdów: http://bit.ly/angular-workshop
* git clone https://github.com/marcin-wosinek/angular-workshop.git
* chrome:
 * linux: chromium-browser --disable-web-security
 * windows - skopiować link do chroma i edytować: "(originalny link) --disable-web-security"
* TODO git config alias

## AngularJs "Hello world"
* git checkout slide-1
* dwu stronne bindowanie
* działający, nie trywialny kod oparty o sam widok

## ng-include
* git checkout slide-2
* wczytywanie cześci widoku dynamicznie

## Kontroler
* wiąże 'swój' widok z resztą aplikacji
* zawiera prostą logikę, związaną z samym wyświetlaniem

## $scope
* obiekt wiążący kontroler z widokiem
* $scope.title będzie dostępny jako {{title}} w widoku
* ng-model - wiąże elementy formularza z modelem
* ng-repeat - pozwala interować po tablicach zdefiniowanych na $scope
(slide z prezentacji)

## ng-controller
* git checkout slide-3
* podpięcie kontrolera do częsci widoku
* $scope działa tylko wewnątrz kodu

## Zadanie 1
* git checkout todo-1
* dodanie kontrolera zawierajacego menu
* dodanie i wyświetlenie menu w index.html

## Rozwiązanie 1
* git add .
* git commit -m '(commit message)'
* git checkout done-1

## $routeProvider
* git checkout slide-4

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
* zbudować własną podstronę, z wyświletaniem listy danych podanych w kontrolerze

## Rozwiązanie 3
* git add .
* git commit -m '(commit message)'
* git checkout done-3

## OrderBy
* git checkout slide-5

```html
<ul>
  <li ng-repeat="product in products | orderBy:'price'">
</ul>
```

## Zadanie 4
* git checkout todo-4
* wymień hardkodowany parametr na pochodzący ze zmiennej

## Rozwiązanie 4
* git add .
* git commit -m '(commit message)'
* git checkout done-4

## filter
* git checkout slide-6
* składnia filter: {experesion}

```html
<tr ng-repeat="person in list | orderBy:orderKey | filter:'oo'"
```

## filter - argumenty
{expresion} zwraca:

* string 'Lorem ipsum' - szukamy stringu w całych obiektach na liście
* obiekt {key: 'value'} - szukamy obietków które pod *key* mają wartośc pasującą do _value_ 
* obiekt {$: 'value'} - szukamy obietków które gdziekolwkiem mają wartośc pasującą do _value_ 

## Zadanie 5
* git checkout todo-5
* zmienić filter na wyszukiwarkę z 3 polami: szukanie po firstName, surName lub wszędzie

## Rozwiązanie 5
* git add .
* git commit -m '(commit message)'
* git checkout done-5

## Funkcje w modelu
* git checkout slide-7

```html
{{displayValueReturnedByFunction()}}

<input ng-change="fireFunctionWhenChangeHappen()">
```

## Zadanie 6
* git checkout todo-6
* dodać formularz z danym osoby - obiekt newPerson
* skorzystać z _ng-click_ do obsługi dodanie
  * dodać do listy newPerson ( nazwaListy.push(nowyElement) )
  * podstawić pusty obiekt za ten podstawiony

## Rozwiązanie 6
* git add .
* git commit -m '(commit message)'
* git checkout done-6



TODO:

## Validowanie formularza

## Trzymanie danych w controlerze
* strata danych przy przejściu na inną podstronę
* użycie tego samego controlera 2 razy

## Services
* nowy serwis - dla kontrolera co 2 razy wystepuje

## Zadanie  7
* dodanie własnego servius, dla list

## Omówienie resta
* obiekty
* tablice

## $resource
* query
* get
* parametry

## przesunięcie danych do json

## dygresja przykład 2000 elementów w danych

## Zadanie 8
* wyświetlanie danych zbiorczych i indywidualnych z jsona













# 1 Warsztaty AngularJs
Pierwszę z cylku warsztaty prezentujące nowoczesne tworzenie aplikacji frontendowych na przykładzie AngularJs. Zapoznamy się podstawowymi koncepcjami istniejącymi w frameworkach js:

* kontroler
* widok
* router
* service

i ich implementacją w angularze.

## Z jakiej wiedzy będziemy korzystać
Warsztaty są kierowane do osób które miały stycznośc z programowanie i technologiami webowymi. Poniżej jest lista koncepcji których znajomość i rozumienie będzie potrzebne do pełnego uczestnictwa w warsztatach.

### Html
* tag
* atrybut
* dołaczanie skryptów i styli do strony

### Js
* bloki sterujące (if, switch)
* pętle
* funkcje

### Css 
Znajomość zastosowania cssa

### Git
* klonowanie repozytorium
* przełączenie się między gałęziami (branch)
* komitowanie

## Środowisko pracy
Uczestnicy będą pracować na własnych komputerach. Będziemy korzystać z:

### Edytor tekstu
Dowolny: notepad++, vim etc.

### Przeglądarka
Współczesna przeglądarka z konsolą developerską. Na przyklad firefox z firebugiem lub chrome.

### Git
Zalecane programy z interfejsem tekstowym. 

## Materiały do pobrania
Zajęcia będą sie opierać o przykładowy projekt dostępy [na githubie](https://github.com/marcin-wosinek/angular-workshop).

## Jak będą wyglądać zajęcia
Będziemy omawiać podstawowe koncepcje angulara na przykładowym kodzie, i potem przechodzić do powtarzania kroków samemu. Wiec pokaże Wam jak wygląda prosty kontroler, i poproszę o stworzenie dodatkowego. I tak dla każdej z omawianych koncepcji.

## Co dalej?

Pierwsze warsztaty będą wprowadzeniem do świata frontendowych aplikacji. Następne spotkania będą poruszać takie tematy jak:

* webstorage i inne js api
* aplikacja przeglądarkowa - tworzenie
* optymalne środowsko programistyczne
* unit testy i testowalność aplikacji
* komunikacja z backendem

## Materiały do nauki
* http://angularjs.org/
* http://egghead.io/
