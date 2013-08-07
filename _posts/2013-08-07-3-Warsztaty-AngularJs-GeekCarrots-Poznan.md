---
layout: default
category: warsztaty
title: 3 Warsztaty AngularJs - GeekCarrots Poznań
tags: [AngularJs, Akai, Poznań]
---
# AngularJs: Warsztaty - stopień 3

## Środowisko
* konsolowy git
* chrome/chromium

## Start
* Treść slajdów: [http://bit.ly/angular-workshop3](http://bit.ly/angular-workshop3)
* git clone [https://github.com/marcin-wosinek/workshop-3.git](https://github.com/marcin-wosinek/workshop-3.git)
* chrome:
 * linux: chromium-browser --disable-web-security
 * windows - skopiować link do chroma i edytować: "(originalny link) --disable-web-security"
* git config --global alias.tree "log --oneline --graph --decorate --all"

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
* demo: #/shortcuts

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
* Demo: #/showContacts
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

## Testy
* Rodzaje testów: 
 * Unit testy
 * Testy integracyjne
 * Testy funkcjonalne

## Piramida testów
* Unit testy - blisko logiki
 * sprawdzamy przekładnie jednego trybika
* Testy funkcjonalne - logika wszystkich warstw razem
 * sprawdzamy działanie wielu połaczonych trybików
 * wykładniczy wzorst liczby przypadków granicznych

## Unit testy - idea
* trywialne sprawdzanie działania kody
* weryfikujemy wyizolowaną logikę
* razem z code review bardzo skuteczny mechanizm łapanie błędów

## Mocks & stubs
* sposób na izolowanie elementu
* zastępcze zależności przekazywane do testowanego obiektu
* mocks:
 * obiekt z wymaganiami
* stubs:
 * prosty obiekt, który pamieta wywołania fukncji

## Dependecy injection
* 'Odwrócenie kontroli'
* funkcja nie woła swoich zależności - dostaje je z zewnątrz

```js
// Dependecy injection
function ContactEditCtrl ($scope, $routeParams, contacts) {
  $scope.contact = contacts.get($routeParams.id);
  $scope.id = $routeParams.id;
}
```

```js
// Dependecy 'calling'
function ContactEditCtrl () {
  var $scope = ScopeFactory.getNewScope(),
    $routeParams = RouteParams.getSingleton(),
    contacts = new Contacts();

  $scope.contact = contacts.get($routeParams.id);
  $scope.id = $routeParams.id;
}
```

## Jasmine
* BDD test framework
* [http://pivotal.github.io/jasmine/](http://pivotal.github.io/jasmine/)

## Jasmine - składnia
* describe - blok grupujący 
* beforeEach - set up testu
* afterEach - clean up
* it - test

```js
describe("Jasmine", function() {
  it("is aware that true === true", function() {
    expect(true).toBe(true);
  });

  it("is aware that false !== true", function() {
    expect(false).not.toBe(true);
  });
});
```

## Jasmine - matchery (asercje)
* weryfikuje zastany stan
* (konieczna) paczka dodatkowych matcherów - [https://github.com/JamieMason/Jasmine-Matchers](https://github.com/JamieMason/Jasmine-Matchers)
* Zapamiętaj: expect().toEqual()

```js
// Defaults
expect(a.foo).toBeDefined();
expect(message).toMatch(/bar/);
expect(a).toBe(true);
expect(a).toEqual(12);
expect(pi).toBeGreaterThan(e);

// Jasmine matchers
expect(function).toBeFunction();
expect(string).toBeString();
expect(array).toBeArray();
```

## Jasmine - mokowanie
* jasmine spy
* Zapamiętaj: jasmine.createSpy().andReturn() - zadanie 2

```js
spyOn(foo, 'setBar').andCallThrough();
foo.setBar(42);
expect(foo.setBar).toHaveBeenCalled();
expect(foo.setBar).toHaveBeenCalledWith(42);

var standAloneSpy = jasmine.createSpy('standAloneSpy').andReturn(11);
```

## Unit testy - Angular
* git checkout slide-6
* karma test runner
* page runner

## Angular - testowanie controlera
* funkcja $controller
* zasoby do wstrzykiwania

```js
$controller('GlobalCtrl', {
  $scope: scope});
```

## Zadanie 2 - unit testy controlera
* git checkout todo-2a
* prosty test sprawdzający czy numer z wsUuidGenerator.createUuid trafia do ciastka
* pliki: test/spec/controllers/global.js +8

## Rozwiązanie 2a
* git add .
* git commit -m '(commit message)'
* git checkout done-2a

```js
beforeEach(inject(function ($controller, $rootScope) {
  scope = $rootScope.$new();
  cookies = {};
  wsUuidGenerator = {
    createUuid: jasmine.createSpy('createUuid').andReturn('341')
  };

  GlobalCtrl = $controller('GlobalCtrl', {
    $scope: scope,
    $cookies: cookies,
    wsUuidGenerator: wsUuidGenerator
  });
}));

it('should setup cookies', function () {
  expect(cookies.trackingId).toEqual('341');
});
```

## Zadanie 2b - naiwna implementacja
* git checkout todo-2b
* najprostrzy kod przechodzący test
* pliki: app/scripts/controllers/global.js +9

## Rozwiązanie 2b
* git add .
* git commit -m '(commit message)'
* git checkout done-2b

```js
$cookies.trackingId = '341';
```

## Refaktoring testu
* funkcja init, pozwalająca na reinicjalizacje
* git checkout slide-7

```js
init = function () {
  GlobalCtrl = $controller('GlobalCtrl', {
    $scope: scope,
    $cookies: cookies,
    wsUuidGenerator: wsUuidGenerator
  });
};
```

## Zadanie 2c
* git checkout todo-2c
* weryfikacja uzycia generatora
* pliki: test/spec/controllers/global.js +35

## Rozwiązanie 2c
* git add .
* git commit -m '(commit message)'
* git checkout done-2c

```js
expect(wsUuidGenerator.createUuid).toHaveBeenCalled();
```

## Naiwna implementacja
* git checkout slide-8

```js
wsUuidGenerator.createUuid();
$cookies.trackingId = '341';
```

## Zadanie 2d
* git checkout todo-2d
* test sprawdzający dla różnej wartości
* pliki: test/spec/controllers/global.js +38

## Rozwiązanie 2d
* git add .
* git commit -m '(commit message)'
* git checkout done-2d

```js
// check for some other value   
wsUuidGenerator.createUuid.andReturn('111');
init();
expect(cookies.trackingId).toEqual('111');
```

## Pokryty testami kod
* git checkout slide-8

```js
$cookies.trackingId = wsUuidGenerator.createUuid();
```

## Zadanie 2e
* git checkout todo-2e
* test sprawdzający zachowanie wartości ciasteczka
* refaktoring testów - wydzielenie osobnego testu dla innej wartości liczbowej
* pliki: test/spec/controllers/global.js +42

## Rozwiązanie 2e
* git add .
* git commit -m '(commit message)'
* git checkout done-2e

```js
// should not override existing cookie value
wsUuidGenerator.createUuid.andReturn('111');
init();
expect(cookies.trackingId).toEqual('341');
```

## Pokryty testami kod
* git checkout slide-10
* całkowite pokrycie testami 

```js
if (!angular.isString($cookies.trackingId)) {
  $cookies.trackingId = wsUuidGenerator.createUuid();
}
```

## Angular - testowanie serwisu
* serwis $provide do nadpisywania domyślnych komponentów

```js
module(function($provide) {
  $provide.value('ServiceA', ServiceAMock);
  $provide.value('ServiceB', ServiceBMock);
});

inject(function(_ServiceInTest_) {
  ServiceInTest = _ServiceInTest_;
});
```

## Przykład testów service
* git checkout slide-11

```js
beforeEach(function () {
  module(function($provide) {
    $provide.value('$resource', _resource);
  });

  inject(function(_contacts_) {
    contacts = _contacts_;
  });
});

it('should implement getAll', function () {
  expect(ContactsResource.query).not.toHaveBeenCalled();
  var returned = contacts.getAll();
  expect(ContactsResource.query).toHaveBeenCalled();
  expect(returned).toEqual('queryTest');
});
```

## Podsumowanie
* directives
* karma
* jasmine
* tdd

## Stay tuned
* [GeekCarrots Poznań](http://geekgirlscarrots.pl/category/spotkania/poznan/)
* [Akai](http://akai.org.pl/)
* [GDG Poznań](https://plus.google.com/110191013153077917985/posts)
* [Hacking-Poznan](http://www.meetup.com/Hacking-Poznan/)
