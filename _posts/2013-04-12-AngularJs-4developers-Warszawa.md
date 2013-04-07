---
layout: default
category: prezentacja
title: AngularJs 4developers Warszawa
tags: [AngularJs, 4developers, Warszawa]
---
# AngularJs
TODO:

* przykłady kodu do slajdów
* przygotować prezentacje featurów
* naszkicować slajdy 

## Kim jestem?
* Marcin Wosinek
* 5 lat doświadczenia w IT
 * Pracy w C# zawdzięczam mocne przekonanie do testów jednostkowych
 * Pracy we front endzie - js
* aktualnie js kontraktor w Poznaniu

## Wy?
* kto korzysta z frameworków js?
 * backbone?
 * ember?
* kto uważa że pisanie testów jest konieczne w dobrym rzemiośle programistycznym?
* kto uważa że jak pisać kod i testy to w TDD?
* kto stosuje TDD przy pisaniu przeglądarkowego js?

## Temat
* zmiany w myśleniu o front endzie
* konieczność dostosowania praktyki do nowych realiów
* przykład frameworku odpowiadającego nowym potrzebą

## Nowa rzeczywistość
* Js się rozwija 
* jQuery to nie wszystko

## Tradycyjna architektura stron
* generowanie html po stronie serwera
* przesyłanie danych razem ze znacznikami html
(grafika do narysowania)

## Podejście aplikacyjne
* wiecej logiki po stronie front endu
* templaty jsowe
(grafika do narysowania)

## Komunikacja z backendem
* wysyłanie requestów restowych 
* odbieranie danych w Json

```js
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": 10021
  }
}
```

## Zmiany
* słownik - mniej atrybutów, tagów i klas, a wiecej modeli należących do domeny aplikacji (klienci, produktu etc.)
* nowe wymagania w stosunku do jakości - wzrost ilość i znaczenia kodu realizowanego w przeglądarce

## Testowalność
* w tradycyjnym jQuerowym kodzie bardzo niska
* jeśli logika dotyka DOM - w testach będziemy musieli mockować DOM

```js
function PasswordCtrl() {
  // get references to DOM elements
  var msg = $('.ex1 span');
  var input = $('.ex1 input');
  var strength;

  this.grade = function() {
    msg.removeClass(strength);
    var pwd = input.val();
    password.text(pwd);
    if (pwd.length > 8) {
      strength = 'strong';
    }
    else {
      strength = 'weak';
    }
    msg
     .addClass(strength)
     .text(strength);
  }
}
```

## Boilerplate
* Kod powtarzany dla każdego kontrolera - słuchanie eventów, aktualizowanie dom etc.
* Zamiast DRY - WET (We Enjoy Typing)
* Boiler plate zabija testowalność kodu:
 * jest kluczowy do działania aplikacji
 * jeśli go nie testujemy - to nie sprawdzamy elementów bez których aplikacja nie działa
 * jeśli go testujemy - to dostajemy 2 razy wiecej boilerplate

```js
initialize: function () {
  this.allCheckbox = this.$('#toggle-all')[0];
  this.$input = this.$('#new-todo');
  this.$footer = this.$('#footer');
  this.$main = this.$('#main');

  this.listenTo(app.Todos, 'add', this.addOne);
  this.listenTo(app.Todos, 'reset', this.addAll);
  this.listenTo(app.Todos, 'change:completed', this.filterOne);
  this.listenTo(app.Todos, 'filter', this.filterAll);
  this.listenTo(app.Todos, 'all', this.render);

  app.Todos.fetch();
}
```

## AngularJs
* framework aplikacji
* 29KB zminimalizowany i spakowany
 * backbone: 19KB (z underscore & backbone)
 * backbone: 32KB (z lodash & jQuery)
 * ember: 49KB
* brak zależności:
 * może używać jQuery, o ile jest dostępne przy uruchomieniu

## Architektura MV*
* początkowo przypominała MVC, teraz bardziej MVVM - nazywan MVW(hatever) przez twórców
* w skrócie - to czym zamuje sie logika, determinuje gdzie powinna się znajdować
(grafika do narysowania)

## Widok
* oparty o zwykły html
* wyświetla wartości w \{\{ model \}\}
* jest rozszeżony przez framework

```html
<ul class="unstyled">
  <li ng-repeat="todo in todos">
    <span>{{todo.text}}</span>
  </li>
</ul>
<form ng-submit="addTodo()">
  <input ng-model="todoText" />
  <input type="submit" value="add" />
</form>
```

## Kontrolery
* wiąże 'swój' widok z resztą aplikacji
* zawiera prostą logikę, związaną z samym wyświetlaniem
(grafika do narysowania - balsamique)

## $scope
* obiekt wiążący kontroler z widokiem
* $scope.title będzie dostępny jako {{title}} w widoku
* ng-model - wiąże elementy formularza z modelem
* ng-repeat - pozwala interować po tablicach zdefiniowanych na $scope
(Obrazek z wyjaśniemie co to jest scope: taki jak ten: https://docs.google.com/presentation/d/1moRrmS6ogVlOBzVidsPgLc1_w-vYC3Bt87Wk3oak5rU/edit#slide=id.gb58ffdb9_015)

### Prezentacja
1. Angularowe 'Hello world'
2. Templatkowanie z ng-repeat

## Proste obiekty js
* pracujemy na prostych funkcjach i obiektach js

```js
// Backbone
app.Todo = Backbone.Model.extend({
  defaults: {
    title: '',
    completed: false
  }
});

// Ember
Todos.Todo = DS.Model.extend({
  title: DS.attr('string'),
  isCompleted: DS.attr('boolean')
});

// Angular
todos.push({
  title: $scope.newTodo,
  completed: false
});
```

## Filtry
* pozwalają na wygodne zarządzanie tym co jest wyświetlane w ng-repeat
* usprawniają tworzeni zawęrzającego się wyszukiwania, sortowania
(przykład z zastosowaniem filter i orderby)

```html
<ul>
  <li ng-repeat="project in projects | filter:search | orderBy:'name'">
    <a href="{{project.site}}">{{project.name}}</a>: {{project.description}}
  </li>
</ul>
```

## Two ways binding
* model jest jedynym źródłem prawdy
* zmiany na modelu aktualizują widok
* zmiany w widoku aktualizują model
(two ways binding z angulara: http://docs.angularjs.org/guide/dev_guide.templates.databinding - zadowolony obrazek, potrzeba tylko dodać do podziekowań)

## Wsparcie dla formularza
* rozumie atrybuty należącę html5 - required, pattern, date
* automatycznie dodaje klasy opisujące stan elementu do wprowadzania danych
(html przetworzony przez angulara)

```html
<form name="exampleForm" class="ng-pristine ng-invalid ng-invalid-required">

    Required field:
  <input ng-model="required" required="" class="ng-pristine ng-invalid ng-invalid-required"></label> <br>

    Email field: 
  <input ng-model="email" type="email" class="ng-pristine ng-valid ng-valid-email"></label> <br>

  <button ng-disabled="!exampleForm.$valid" disabled="disabled">Submit</button>
</form>
```

### Prezentacja
1. przykład walidującego się formularza - zmiana kolorów kontrolek
2. Rzut oka na kod

## Wstrzykiwanie zależności
* nasz komponent ma przekazywane jego zależności jak parametry do funkcji go opakowywującej
* ładna definiacji powiązań między komponentami
* zwiększa testowalność
(kontroler z kilkoma wstrzykniętymi seriwiami - $scope, $log, $window)

```js
function HelloCtrl($scope, $window, $log) {
  $scope.message = 'Display me in view';
  $window.alert('Use window via $window service - that improves testability');
  $log.log('We can even test console log calls - thats to $log wrapper');
}
```

## Serwisy
* reużywalne kawałki kodu
* wstrzykiwane do kontrolerów, directives i innych serwisów
* większość logiki aplikacji powinna być w nich realizowana
(prosty serwis - opakowanie dla webstorage)

```js
/**
 * Services that persists and retrieves ToDos from localStorage
 */
todomvc.factory('todoStorage', function () {
  var STORAGE_ID = 'todos-angularjs';

  return {
    get: function () {
      return JSON.parse(localStorage.getItem(STORAGE_ID) || '[]');
    },

    put: function (todos) {
      localStorage.setItem(STORAGE_ID, JSON.stringify(todos));
    }
  };
});
```

## Ścieżki - $routeProvider
* dla aplikacji możemy zdefiniować ścieżki (z argumentami), przekierowania etc.
* ładnie współpracuje z przyciskami dalej i wstecz
* wspiera adresy z /# i bez
(przykład rejestracji kilku ścieżek)

```js
angular.module('phonecat', [])
  .config(['$routeProvider', function($routeProvider) {
    $routeProvider
      .when('/phones', {
        templateUrl: 'partials/phone-list.html',
        controller: PhoneListCtrl
      })
      .when('/phones/:phoneId', {
        templateUrl: 'partials/phone-detail.html',
        controller: PhoneDetailCtrl
      })
      .otherwise({
        redirectTo: '/phones'
      });
  }]);
```

## Komunikacja z backendem - $resource
* serwis do generowani api komuniujacego się po restcie
* zalecany sposób użycia: $resource -> serwis opakowujący model -> kontroler
(slajd ze sposobem użycia - examples)

```js
myApp.factory('ProductService', function($resource) {
  var ProductService = {};

  var ProductResource = $resource('/product/:productId');

  ProductService.getItem = function (index) {
    return ProductResource.get({productId: index});
  }

  ProductService.addItem = function (item) {
    resource.save({}, item));
  }

  ProductService.removeItem = function (item) {
    // Calls method delete on ProductResource - that way, just to make ie8 happy
    return ProductResource['delete']({productId: item.id});
  }

  ProductService.getList = function () {
    return ProductResource.query();
  }

  return ProductService;
});

function ProductCtrl($scope, ProductService) {
  // Take products form ProductService and put it on $scope
}
```

## Directives
* niestandardowe tagi i atrybuty zdefiniowane przez angulara, lub developera aplikacji
* rozszeżają działanie html o nowe feature
* do nich należy manipulacja DOMem
* w miejsce '{expression}' np 'variable' żeby dostać się do $scope.variable
* przykłady:
 * ng-show - ukrywa jeśli false
 * ng-hide - ukrywa jeśli true
 * ng-view - podstawia widok zdefiniowany dla ścieżki
 * ng-clas - pozwala ustawiać inteligentie klasy
 * ng-switch - wyświelta jedną z opcji

```html
<ANY class="ng-show: {expression};"> <ANY ng-show="{expression}">
<ANY class="ng-hide: {expression};"> <ANY ng-hide="{expression}">

<ng-view> <any ng-view>

<ANY ng-class="{expression}"> <ANY class="ng-class: {expression};">

<ANY ng-switch="expression">
  <ANY ng-switch-when="matchValue1">...</ANY>
  <ANY ng-switch-when="matchValue2">...</ANY>
  ...
  <ANY ng-switch-default>...</ANY>
</ANY>
```

## Yeoman
* Zestaw narzędzi usprawniających workflow developerski
* yo - generatory kodu:
 * dla angulara automatyzuje tworzenie:
  * serwisów
  * directives
  * kontrolerów
  * ścieżek - kotrolera wraz z widokiem i ścieżką dostępu
 * wspiera również inne frameworki i czystego js
* grunt - automatyzacja częstych zadań
 * minimalizacja i paczkowanie kodu
 * serwer developerski z automatycznym odświeżaniem otwartej strony
* bower - zarządzanie zależnościami
(trzy loga: http://yeoman.io/ yo, grunt, bower)

### Prezentacja
1. Utworzenie aplikacji angularowej w nowym folderze
2. Odpalenie serwer i otworzenie strony w przeglądarce
3. Dodanie ścieżki do aplikacji i otworzenie w przeglądarce
4. Zmiana widoku i automatyczne odświerzenie strony

## Karma (Testacular)
* test runner pozwalający uruchamiać testy w przeglądarkach
* uruchamiamy serwer na maszynie na której tworzymy kod
* łaczymy z nim przeglądarki i serwer odpala w nich testy
(karma logo: http://karma-runner.github.io/0.8/index.html - cały napis: Karma, specacular test runner...)

### Prezentacja
1. Dodanie przycisku do widoku
2. Dodanie testu sprawdzającego czy alert został włączony
3. Napisanie kodu przechodzącego test

## Gotchas - pisanie directives
* Narzędzie na który jest opartę bardzo wiele corowych featurów frameworka - 2 ways binding
* rough developer experience - w szególności na tle bardzo gładkiej współpracy z resztą frameworka

```js
angular.module('blink', [])
  .directive('blink', function() {
    return {
      restrict: 'E',
      link: function(scope, elm, attr) {
        setInterval(function() {
          elm.toggle();
        }, parseInt(attr.interval, 10) || 1000);
      }
    };
  });
```

## Gotchas - ng-model w ng-repeat
* ng-repeat tworzy nowe scopy dla elementów
* scopy dzieci, dziedziczą prototypowo z parenta
* ng-model="value" działa bardzo inaczej niż ng-model="object.value"
* występuje wszędzie tam gdzie mamy podscopy

## Gotchas - minimalizowanie kodu
* wiązanie $scopu w kontrolerze i w widoku odbywa sie po nazwach atrybutów - wymagana jest odpowiednia konfiguracja minimalizacji
* wstrzykiwanie zależności jest zależne od nazwy argumentu funkcji - potrzebne dodatkowe zdefiniowanie zależności
(Przykład kodów - przed i po minimalizacji)

## Gotchas - $resource
* istnieje w osobnym pliku, który trzeba załadować
* zwraca puste obiektu lub tablice które będa dopiero uzupełnione po odebraniu odpowiedzi
* w zwiazku z tym musimy odraz zadeklarować czy mowa jest o tablicy czy obiekcie
(screen z firebuga z odpytaniem resourca i dostaniem pustego obiektu)

## Gotchas - filtry działają tylko na tablicach
* ng-repeat przeinteruje po obiekcie - ale filtry nie bedą działać
(Przykład filtru)

## Gotchas - e2e testing
* skonfigurowanie testów jest skomplikowane
* może w porywach być uznane za feature pułapkę

## Gotchas - akualizowanie scope z poza frameworka
* wiekszość zmian modelu odbywa się we frameworku:
 * pobranie danych z $resource
 * jest odpalane za pomocą directives: ng-model, ng-clic
* w sytuacji użycia zmian przychodzących z poza angularowego świata może być konieczne wywołanie fukncji $digest
(przykład kodu z użyciem directive)

## Gotchas - $ w nazwach serwisów
* odróżnia serwisy frameworkowe od aplikacyjnych
* używanie $ w nazwach własnych serwisów pozbawia $ sensu

## Pytania
1. Czemu angular a nie backbone?
2. Czy to podejścia da się zintegrować z legacy code?
3. Co walidatory na html dostosowany do angulara?
4. Z jakim backendem używać angulara?

## Materiały
* http://angularjs.org/
* http://egghead.io/
* http://www.youtube.com/user/angularjs

## Podsumowanie
* koncepcje znane z backendowych techologi będą zadomowiać sie w js
* AngularJs jest narzedziem pozwalającym na bardzo dojrzałe programowanie we front endzie
* Warto zapoznać się z yeomanem

## Kontakt
* namiary na bloga
* marcin.wosinek@gmail.com

## Podziękowania
