---
layout: default
category: warsztaty
title: Warsztaty AngularJs Akai Poznań
tags: [AngularJs, Akai, Poznań]
---
# AngularJs: Warsztaty - stopień 2 (8 VI sobota)

## Środowisko
* konsolowy git
* chrome/chromium
 * korzystamy z `<input type="range">`
 * powinen być slider tutaj: <input type="range">
* lokalny serwer http - ciasteczka nie działają z file systemu

## Start (text)
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
* od następnych warsztatów będziemy z niego korzystać

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

## Zadanie 1: filtr przedziału
* filtr wybierający ludzi z odpowiedniego przedziału wieku
* git checkout todo-1
* użycie: app/views/showContacts.html +9
* implementacja: app/scripts/filters/between.js

## Rozwiązanie 1
* git add .
* git commit -m '(commit message)'
* git checkout done-1
* Pytania?

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

## Cel: śledzenie userów
* liczenie odwiedzin
* śledzenie aktywności

## Global controller
* git checkout slide-3
* pliki: app/index.html +26
* hack na zawsze uruchamiany kontroler

## Generator UUID (Universally unique identifier)
* git checkout slide-4
* pliki: app/scripts/services/wsUuidGenerator.js
* prawdopodobieństwo kolizji:
 * miliard co sekunde: w 100 lat mamy 50%
 * 600 milionów dla każdego człowieka na ziemi: 50%
 * ryzyko że udeży mnie meteor w ciągu roku = kolizja przy kilku dziesiątkach bilionów UUID

## Ciasteczka - cookies
* do 4 kb danych
* przesyłane z każdym requestem do serwera

## Zastosowanie
* śledzenie użytkowników/liczenie odwidzin
* <del>przechowywanie danych</del>: lepiej użyć [webstorage](http://dev.w3.org/html5/webstorage/)
* logowanie usera - dobrze zainteresować się tym http://witoldsz.github.io/angular-http-auth/

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

## ngTransclude
* pozwala na wstawienie oryginalnej zawartości tagu wewnątrz templatu
* wymaga transclude: true

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

## Instalowanie yeomana
* Do przyszłych warsztatów będziemy korzytać z yeomana
* Dla chetnych: sprubujcie teraz zainstalować [yeoman](http://yeoman.io/)

## Co na następnych warsztatach?
* directives
* unit testy & TDD we frontendzie
* warte uwagii projekty:
 * angular-ui
 * angular-bootstrap

## Stay tuned
* [Akai](http://akai.org.pl/)
* [GDG Poznań](https://plus.google.com/110191013153077917985)
* [Hacking-Poznan](http://www.meetup.com/Hacking-Poznan/)
