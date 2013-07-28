---
layout: default
category: warsztaty
title: 2 Warsztaty AngularJs - GeekCarrots Poznań
tags: [AngularJs, GeekCarrots, Poznań]
---
# AngularJs: Warsztaty - stopień 2
## Środowisko
* konsolowy git
* chrome/chromium
 * korzystamy z `<input type="range">`
 * powinen być slider tutaj: <input type="range">
* lokalny serwer http - ciasteczka nie działają z file systemu

## Start
* Treść slajdów: [http://bit.ly/angular-workshop2](http://bit.ly/angular-workshop2)
* git clone [https://github.com/marcin-wosinek/workshop-2.git](https://github.com/marcin-wosinek/workshop-2.git)
* chrome:
 * linux: chromium-browser --disable-web-security
 * windows - skopiować link do chroma i edytować: "(originalny link) --disable-web-security"
* git config --global alias.tree "log --oneline --graph --decorate --all"

## Projekt
* Książka kontaktów
 * lista kontaktów
 * strona osoby
 * formularz edycji

## index.html
* ng-view - ładujemy ścieżki
* underscore - użyteczne funkcje

```html
<!-- Add your site or application content here -->
<div class="container" ng-view></div>

<script src="components/angular/angular.js"></script>
<script src="components/underscore/underscore.js"></script>
```

## Ścieżki
* konfiguracja aplikacji
* definicja ścieżek

```js
$routeProvider
  .when('/', {
    templateUrl: 'views/main.html',
    controller: 'MainCtrl'
  })
  .when('/contact/:id', {
    redirectTo: '/contact/:id/view'
  })
```

## Kontrolery
* $routeParams
* contacts

```js
angular.module('workshop2App')
  .controller('ContactViewCtrl',
      function ($scope, $routeParams, contacts) {
    $scope.contact = contacts.get($routeParams.id);
    $scope.id = $routeParams.id;
  });
```

## Serwis z danymi
* contacts
* [json-generator](http://www.json-generator.com/)

```js
angular.module('workshop2App')
  .factory('contacts', function () {
    var exampleContacts = [ ... ];

    // Public API here
    return {
      getAll: function () {
        return exampleContacts;
      },
      get: function (id) {}
```

## Underscore
* użyteczne funkcje
* [dokumentacja](http://underscorejs.org)

```js
var evens = _.filter([1, 2, 3, 4, 5, 6], function(num){ return num % 2 == 0; });
// => [2, 4, 6]

var sum = _.reduce([1, 2, 3], function(memo, num){ return memo + num; }, 0);
// => 6

_.isString(object)
_.isNumber(object)
```

## Struktura plików
* git checkout slide-1
* app/ zawier wszystko co jest potrzebne do zdepoloyowania aplikacji
 * index.html - jedyny plik do użytku bezpośredniego
 * view/ - templaty angulara
 * styles/ - pliki css i nie skopilowany sass
 * components/ - zewnętrzne komponenty
 * scripts/ - js
  * app.js - definicja modułu + konfiguracja
* test/ katalog z testami

## Yeoman
* narzedzie do wspierania workflowu developerskiego
* generator kodu

### Prezentacja:
1. Generowanie ścieżki
2. Odpalenie serwera
3. Automatyczne odświerzenie na zmianę

* pozwalają zmieniać dane z poziomu widoku
* wbudowane filtry

## Filtry
```html
<p>{{ someText | uppercase }}</p>

<p>Output: {{ array | limitTo:3 }}</p>

<tr ng-repeat="friend in friends | filter:searchText">
</tr>
```

## Pisanie filtrów
* zwracamy przetworzony element
* przyjmujemy dowolną liczę argumentów

```js
angular.module('workshop2App')
  .filter('filterName', function () {
    return function (input, arg1, arg2) {
      return 'between filter: ' + input;
    };
  });
```

```html
<li ng-repeat="element in list | filterName:value1:value2">
```

## angular.forEach
* pętla
* nie kopiujej danych stworzonych przez angulara (object.$someAngularStuff)

```js
var array = [1, 2, 3];

angular.forEach(array, function(value){
    this.push('Value: ' + value);
});
```

## Zadanie 1: filtr przedziału
* filtr wybierający ludzi z odpowiedniego przedziału wieku
* git checkout todo-1
* użycie: app/views/showContacts.html +9
* implementacja: app/scripts/filters/between.js

```html
<tr ng-repeat="contact in contacts | between:'age':min:max">
```

## Rozwiązanie 1
* git add .
* git commit -m '(commit message)'
* git checkout done-1
* Pytania?

```js
return function (input, key, min, max) {
  if (angular.isArray(input)) {
    var toReturn = [];

    angular.forEach(input, function (element) {
      if (min <= element[key] && element[key] <= max) {
        toReturn.push(element);
      }
    });

    return toReturn;
  }

  // is not array - just return unmodified and forget
  return input;
};
```

## Angular 1.1.x
* w przeciwieństwie do 1.0.x - gałąź niestabilna
* w przeciągu kilku tygodni wyjdzie 1.2
* duży feature animacje

## Animacje
* directivy odpowiadają za zmianę dom
* do wersji 1.1.4 nie było wsparcia dla animacji

## ngAnimation
* pozwala odpalać animacje na zmiana DOM:
 * ng-repeat
 * ng-include
 * ng-hide
 * ng-show
* Demo [http://www.nganimate.org](/http://www.nganimate.org/)

## Zadanie 2: zastosowanie animacji
* animowanię zmiany wyświeltanych elementów
* git checkout todo-2
* implementacja: app/views/showContacts.html & app/styles/main.css

## Rozwiązanie 2
* git add .
* git commit -m '(commit message)'
* git checkout done-2
* Pytania?

```html
<li ng-animate="'animate'" ng-repeat="contact in contacts | between:'age':min:max">
```

```css
.animate-enter,
.animate-leave
{
  -webkit-transition: 400ms cubic-bezier(0.250, 0.250, 0.750, 0.750) all;
  -moz-transition: 400ms cubic-bezier(0.250, 0.250, 0.750, 0.750) all;
  -ms-transition: 400ms cubic-bezier(0.250, 0.250, 0.750, 0.750) all;
  -o-transition: 400ms cubic-bezier(0.250, 0.250, 0.750, 0.750) all;
  transition: 400ms cubic-bezier(0.250, 0.250, 0.750, 0.750) all;
  position: relative;
  display: block;
  overflow: hidden;
  text-overflow: clip;
  white-space:nowrap;
}
```

## Cel: śledzenie userów
* liczenie odwiedzin
* śledzenie aktywności

## Global controller
* git checkout slide-3
* pliki: app/index.html +26
* hack na zawsze uruchamiany kontroler

```html
<!-- Before -->
<div class="container" ng-view></div>
```

```html
<!-- After -->
<div ng-controller="GlobalCtrl">
  <div class="container" ng-view></div>
</div>
```

## Generator UUID (Universally unique identifier)
* git checkout slide-4
* pliki: app/scripts/services/wsUuidGenerator.js
* prawdopodobieństwo kolizji:
 * miliard co sekunde: w 100 lat mamy 50%
 * 600 milionów dla każdego człowieka na ziemi: 50%
 * ryzyko że udeży mnie meteor w ciągu roku = kolizja przy kilku dziesiątkach bilionów UUID

```js
return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'
  .replace(/[xy]/g, 
    function(c) {var r = Math.random()*16|0,v=c=='x'?r:r&0x3|0x8;return v.toString(16);});
```

## Ciasteczka - cookies
* do 4 kb danych
* przesyłane z każdym requestem do serwera

## Zastosowanie
* śledzenie użytkowników/liczenie odwidzin
* <del>przechowywanie danych</del>: lepiej użyć [webstorage](http://dev.w3.org/html5/webstorage/)
* logowanie usera - dobrze zainteresować się tym [http://witoldsz.github.io/angular-http-auth/](http://witoldsz.github.io/angular-http-auth/)

## Cookies w angularze
* ngCookies - dodatkowy plik do załadowania
* $cookies - sewis opakowywujący użycie cookies

## Zadanie 3: tracking cookies
* git checkout todo-3
* implementacja: app/scripts/controllers/global.js
* Jeśli nie ma 'trackingId' na ciasteczku - ustawamy je na nowo wygenerowany UUID

## Rozwiązanie 3
* git add .
* git commit -m '(commit message)'
* git checkout done-3
* Pytania?

```js
angular.module('workshop2App')
.controller('GlobalCtrl', function ($scope, $cookies, wsUuidGenerator) {
  // if it's empty set trackingId on cookie to new created UUID
  if (!angular.isString($cookies.trackingId)) {
    $cookies.trackingId = wsUuidGenerator.createUuid();
  }
});
```

## Directives
* rozszeżenia do html
* formy użycia

```html
<span my-dir="exp"></span>
<span class="my-dir: exp;"></span>
<my-dir></my-dir>
<!-- directive: my-dir exp -->
```

## Pisanie directives
* git checkout slide-5
* plik: app/scripts/directives/ws-accept-cookies.js
* tak definiujemy tak jak kontrolery serwisy czy filtry
* properties zwracanego obiektu:
 * template - html który zastąpi zawartość
 * restrict - ograniczenie uzycia directive:
  * E - element, tag
  * A - atrybut
  * C - klasa
  * M - komentarz
 * link - funkcja opalana po podpięciu directive

```js
angular.module('workshop2App')
  .directive('wsAcceptCookies', function () {
    return {
      template: '<div></div>',
      restrict: 'E',
      link: function postLink(scope, element, attrs) {
        element.text('this is the wsAcceptCookies directive');
      }
    };
  });
```

## ngTransclude
* pozwala na wstawienie oryginalnej zawartości tagu wewnątrz templatu
* wymaga transclude: true

```js
{
  transclude: true,
  template: '<div ng-transclude></div>'
}
```

## Zadanie 4: template dla ws-accept-cookies
* git checkout todo-4
* przykład użycia: app/index.htm +27
* implementacja: app/scripts/directives/ws-accept-cookies.js
* to co jest oryginalnie wewnatrz tagu chcemy mieć wciąż w directive + chcemy mieć guzik 'accept'

## Rozwiązanie 4
* git add .
* git commit -m '(commit message)'
* git checkout done-4
* Pytania?

```js
return {
    template: '<div ng-transclude></div>' +
              '<button>Akceptuje</button>',
    restrict: 'A',
    transclude: true,
    link: function postLink(scope, element, attrs) {
  }
```

## Linking function
* miejsce na logikę directive
* argumenty - kolejność jest istotna:
 * scope - zakres. W najprostrzym przypadku dzielony ze światem zewnętrznym
 * element - element jQuery lub jqLite do którego podpinany logikę
 * attrs - obiekt z atrybutami na elemencie do którego się wpinamy

## Zadanie 5: ws-accept-cookies - implementacja chowania
* git checkout todo-5
* dodanie obsługki kliknięcia guzika akceptuj
* ukrywanie elementu jesli ciasteczka były już zaakceptowane

## Rozwiązanie 5
* git add .
* git commit -m '(commit message)'
* git checkout done-5
* Pytania?

```js
link: function postLink(scope, element, attrs)  {
    // accept button logic
    scope.accept = function () {
      $cookies.accepted = 'true';
      element.css('display', 'none');
    };

    // hide element if cookies are already accepted
    if ($cookies.accepted) {
      element.css('display', 'none');
    }
  }
```

## Podsumowanie
* pisanie filtrów?
* animacje?
* pisanie directives?
* ngCookies? - session cookies

## Materiały do nauki
* [http://egghead.io/](http://egghead.io/) epizod 10 - 21
* [http://www.nganimate.org/](http://www.nganimate.org/)

## Co na następnych warsztatach?
* directives - dokończenie
* unit testy & TDD we frontendzie
* warte uwagii projekty:
 * angular-ui
 * angular-bootstrap

## Stay tuned
* [GeekCarrots Poznań](http://geekgirlscarrots.pl/category/spotkania/poznan/)
* [Akai](http://akai.org.pl/)
* [GDG Poznań](https://plus.google.com/110191013153077917985/posts)
* [Hacking-Poznan](http://www.meetup.com/Hacking-Poznan/)
