---
layout: default
category: warsztaty
title: 1 Warsztaty AngularJs - GeekCarrots Poznań
tags: [AngularJs, GeekCarrots, Poznań]
---
# AngularJs: Warsztaty - stopień 1
## Start
* treść slajdów: [http://bit.ly/angular-workshop-1](http://bit.ly/angular-workshop-1)
* `git clone` [https://github.com/marcin-wosinek/workshop-1.git](https://github.com/marcin-wosinek/workshop-1.git)
* chrome:
 * linux: chromium-browser --disable-web-security
 * windows - skopiować link do chroma i edytować: "(originalny link) --disable-web-security"
* `git config --global alias.tree "log --oneline --graph --decorate --all"`

## AngularJs "Hello world"
* `git checkout slide-1`
* dwustronne bindowanie
* działający, nie trywialny kod oparty o sam widok
* pliki: index.html +8
```html
<input type="text" ng-model="yourName" placeholder="Enter a name here">
<hr>
<h1>Hello {{yourName}}!</h1>
```

## ng-include
* git checkout slide-2
* dynamiczne wczytywanie części widoku
* pliki: views/main.html & index.html +7
```html
<!-- index.html -->
<div ng-include src="'views/main.html'">
</div>
```

```html
<!-- views/main.html -->
<label>Name:</label>
<input type="text" ng-model="yourName" placeholder="Enter a name here">
<hr>
<h1>Hello {{yourName}}!</h1>
```

## Kontroler
* wiąże 'swój' widok z resztą aplikacji
* zawiera prostą logikę, związaną z samym wyświetlaniem

## $scope
* obiekt wiążący kontroler z widokiem
* `$scope.title` będzie dostępny jako {{title}} w widoku
* ng-model - wiąże elementy formularza z modelem
* ng-repeat - pozwala iterować po tablicach zdefiniowanych na $scope

## ng-controller
* `git checkout slide-3`
* podpięcie kontrolera do części widoku
* $scope działa tylko wewnątrz tagu, na którym jest kontroler
* pliki: views/hello.html & script/script.js

```html
{{helloMessage}}
<br>
<div ng-controller="InputCtrl">
  <input ng-model="sharedData.value" />
  <p>{{sharedData.value}}</p>
</div>
```

```js
workshop.controller("HelloCtrl", function($scope) {
  $scope.helloMessage = "Hello world";
});
```

## Zadanie 1
* `git checkout todo-1`
* dodanie kontrolera zawierającego menu
* dodanie i wyświetlenie menu w index.html
* implementacja: index.html & script/script.js

## Rozwiązanie 1
* `git add .`
* `git commit -m '(commit message)'`
* `git checkout done-1`

```html
<div ng-controller="MenuCtrl">
  <a ng-href="{{href}}">{{text}}</a>
</div>
```

```js
workshop.controller("MenuCtrl", function($scope) {
  $scope.href = "http://google.pl";
  $scope.text = "go to google";
});
```

## $routeProvider
* git checkout slide-4
* definiuję ścieżki w aplikacji
* pliki: scripts/script.js

```js
$routeProvider
  .when("/hello", {
    templateUrl: "views/hello.html",
    controller: "HelloCtrl"
  })
  .otherwise({
    redirectTo: '/main'
  });
```

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
* `git checkout todo-2`
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
* `git add .`
* `git commit -m '(commit message)'`
* `git checkout done-2`

```html
<li ng-repeat="link in links">
  <a ng-href="{{link.url}}">{{link.text}}</a>
</li>
```

```js
$scope.links = [
  {
    url: '#/main',
    text: 'Main'
  }]
```

## Zadanie 3
* `git checkout todo-3`
* zbudować własną podstronę, z wyświetlaniem listy danych podanych w kontrolerze
* implementacja: script/script.js & nowy plik widoku

## Rozwiązanie 3
* `git add .`
* `git commit -m '(commit message)'`
* `git checkout done-3`

```js
workshop.controller("ListCtrl", function($scope) {
  // checkout http://www.json-generator.com/
  $scope.list = [
    {
      "firstName": "Serenity",
      "lastName": "Oldridge",
      "picture": "http://placehold.it/70x70/632955",
```

```html
<table>
  <tr><th>Picture</th><th>Firstname</th><th>Lastname</th><th>Age</th><th>Gender</th><tr>
  <tr ng-repeat="person in list">
  <td><img ng-src='{{person.picture}}'></td>
```

## OrderBy
* `git checkout slide-5`
* pliki: views/list.html

```html
<tr ng-repeat="person in list | orderBy:'lastName'">
  <td><img ng-src='{{person.picture}}'></td>
```

## Zadanie 4
* `git checkout todo-4`
* wymień hardkodowany parametr na pochodzący ze zmiennej
* użyj ng-model + kilka input type="radio"
* implementacja: views/list.html +4, script.js +28

## Rozwiązanie 4
* `git add .`
* `git commit -m '(commit message)'`
* `git checkout done-4`

```html
First name: <input ng-model="orderKey" type='radio' value='firstName'/><br/>
Last name: <input ng-model="orderKey" type='radio' value='lastName'/><br/>
```

## filter
* `git checkout slide-6`
* składnia filter: {experesion}
* pliki: views/list.html +7

```html
<tr ng-repeat="person in list | orderBy:orderKey | filter:'oo'"
```

## filter - argumenty
{expresion} zwraca:

* string 'Lorem ipsum' - szukamy stringu w całych obiektach na liście
* obiekt {key: 'value'} - szukamy obiektów, które pod *key* mają wartość pasującą do _value_ 
* obiekt {$: 'value'} - szukamy obiektów, które gdziekolwiek mają wartość pasującą do _value_ 

## Zadanie 5
* `git checkout todo-5`
* zmienić filter na wyszukiwarkę z 3 polami: szukanie po firstName, lastName lub wszędzie
* implementacja: views/list.html +5

## Rozwiązanie 5
* `git add .`
* `git commit -m '(commit message)'`
* `git checkout done-5`

```html
Everywhere: <input ng-model="search.$" type='text'/><br/>
First name: <input ng-model="search.firstName" type='text'/><br/>
Last name: <input ng-model="search.lastName" type='text'/><br/>
```

## Funkcje w modelu
* `git checkout slide-7`
* pliki: views/main.html +7 & script/script.js + 37

```js
  $scope.name = function () {
    return $scope.firstName + " " + $scope.lastName;
  }

  $scope.counter = 0;
  $scope.valueUpdated = function () {
    $scope.counter++;
  };
```

```html
<h1>Hello {{name()}}!</h1>
<input type="text" ng-change="valueUpdated()" ng-model="value" placeholder="Edit me">
```

## Validowanie formularza
* `git checkout slide-8`
* pliki: views/main.html +10

```html
<form name="exampleForm">
  Required field: <input ng-model="required" required/><br>
  Email field: <input ng-model="email" type="email" required/><br>
  <button ng-disabled='!exampleForm.$valid'>Submit</button>
</form>
```

## Zadanie 6
* `git checkout todo-6`
* dodać formularz z danym osoby - obiekt newPerson
* skorzystać z _ng-click_ do obsługi klikniecia przycisku
  * dodać do listy newPerson ( nazwaListy.push(nowyElement) )
  * podstawić pusty obiekt za ten podstawiony
* implementacja: script/script.js +46 & views/list.html +10

## Rozwiązanie 6
* `git add .`
* `git commit -m '(commit message)'`
* `git checkout done-6`

```html
<form>
  Picture: <input ng-model="newPerson.picture" type='text' placeholder="http://"/><br/>
  First name: <input ng-model="newPerson.firstName" type='text'/><br/>
  Last name: <input ng-model="newPerson.lastName" type='text'/><br/>
```

```js
$scope.add = function () {
  $scope.list.push($scope.newPerson);
  $scope.newPerson = {};
}
```

## Trzymanie danych w kontrolerze
* `git checkout slide-9`
* strata danych przy przejściu na inną podstronę
* użycie tego samego controlera 2 razy - jak na #/main
* pliki: script/script.js +29 & views/main.html +1

```js
$scope.firstName = 'Jan';
$scope.lastName = 'Kowalski';
```

```html
<input type="text" ng-model="firstName" placeholder="Enter a first name here">
<input type="text" ng-model="lastName" placeholder="Enter a last name here">
```

## Services
* `git checkout slide-10`
* nowy serwis - dla kontrolera co 2 razy występuje
* stan jest globalny dla aplikacji
* pliki: script/script.js +62 & views/hello.html +4 & views/main.html +7

```js
// Create serices
workshop.factory("SharedData", function(){
  return {
    value: "Example value"
  };
});
```

## Zadanie 7
* `git checkout todo-7`
* dodanie własnego serwisu, People do użytku przez ListCtrl
* implementacja: script/script.js +42

## Rozwiązanie 7
* `git add .`
* `git commit -m '(commit message)'`
* `git checkout done-7`

```js
workshop.factory("People", function() {
  return [ {"firstName": "Serenity" /*...*/}];
```

```js
workshop.controller("ListCtrl", function($scope, People) {
  $scope.list = People;
```

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
* dane dostępne pod url
* ładne url:
 * http://example.com/products - lista produktów
 * http://example.com/products/1 - pierwszy produkt
* na ogół dane w json

## $resource
* query - pobieranie tablicy
* get - pobieranie obiektu
* parametry

```js
var userResource = $resource('/user/:userId', {});
userResource.get({userId: 1});
```

## Dane do json
* `git checkout slide-11`
* pliki:
 * nowa zależność: index.html & script/angular/angular-resource.js
 * dane: data/people
 * pobieranie: script/script.js +42

```js
workshop.factory("People", function($resource){
  var peopleResource = $resource('data/people', {});
  return peopleResource.query();
});
```

## Podsumowanie
* kontroler?
* widok?
* router?
* service?

## Materiały do nauki
* [AngularJs codecademy - widoki](http://www.codecademy.com/courses/javascript-advanced-en-2hJ3J)
* [http://docs.angularjs.org/tutorial/](http://docs.angularjs.org/tutorial/)
* [http://egghead.io/](http://egghead.io/)

## Co dalej?

Pierwsze warsztaty będą wprowadzeniem do świata frontendowych aplikacji. Następne spotkania będą poruszać takie tematy, jak:

* pisanie własnych filtrów i directives
* korzystanie z animacji
* ciasteczka
* unit testy
* angular-ui & angular bootstrap

## Stay tuned
* [GeekCarrots Poznań](http://geekgirlscarrots.pl/category/spotkania/poznan/)
* [Akai](http://akai.org.pl/)
* [GDG Poznań](https://plus.google.com/110191013153077917985/posts)
* [Hacking-Poznań](http://www.meetup.com/Hacking-Poznan/)
