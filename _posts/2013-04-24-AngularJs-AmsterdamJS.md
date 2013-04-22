---
layout: default
category: presentation
title: AngularJs - AmsterdamJS
tags: [AngularJs, AmsterdamJS, Amsterdam]
---
# AngularJs
## Who am I?
* Marcin Wosinek
* 5 years IT experience
 * WebDev: Javascript
 * C# dev: UnitTests
* Currently js contractor in Poznan, Poland

## JQuery
* jQuery js dom manipulation librarly

## You?
* Who is using js frameworks?
 * backbone?
 * ember?
 * angular?
* who believs unit tests are necessary part of dev craft?
* who believe that TDD is the best way of writting tests?
* who is using TDD while write browser side js?

## Topic
* changes in the way we thing about browser side js
* the need of updating our practice to new standards
* example of framework which will help us alogne the way

## New reality
* JS is developing 
* jQuery is not everything

## Traditional web architecture
* html generated on server side
* transfer of data mixted with html

## Application approach
* more logic on front end side
* js templates

## Communication with backend
* sending rest request
* receiving data in JSON

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

## Changes
* our dictionary - less html stuff (tags, attributs & classes), and more application domain related
* new expectation for quality of our code - more code and more important stuff done on browser side

## Challenges - testability
* in traditional jQueyr code pretty low
* if our logic touches DOM, we need to mock it while testing

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

## Challenges - boilerplate
* Code repeated for every controller - event listening, DOM update etc.
* Instead DRY - WET (We Enjoy Typing)
* Boiler kills code testability:
 * it is necessary for applicatio to work
 * if leave it without tests - we are not checking critical part of our application
 * if we test it - we get two times more boilerplate

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
* application framewor
* 29KB minified & gziped
 * backbone: 19KB (z underscore & backbone)
 * backbone: 32KB (z lodash & jQuery)
 * ember: 49KB
* no dependecy:
 * it will use jQuery, if it was available when instantiated

## MV* architecture
* At the beggining it looked like MVC, now MVVM - or MVW(hatever)
* where we are supposed to put logic depends on what this logic is doing

## View
* based on clean html
* shows values in \{\{ model \}\}
* interpret directives extending html features

```html
<ul>
  <li ng-repeat="todo in todos">
    <span>{{todo.text}}</span>
  </li>
</ul>
<form ng-submit="addTodo()">
  <input ng-model="todoText" />
  <input type="submit" value="add" />
</form>
```

## Filters
* allow us to have controll over data showed in ng-repeat
* helpful in implementation of incremental search, sorting etc.

```html
<ul>
  <li ng-repeat="project in projects | filter:search | orderBy:'name'">
    <a href="{{project.site}}">{{project.name}}</a>: {{project.description}}
  </li>
</ul>
```

## Controller
* binds 'own' view with the rest of application
* contains simple logic, connected to display

## $scope
* binds controller and view together
* $scope.title will be available as {{title}} in view
* ng-model - directives binding input on view with data in scope
* ng-repeat - template side loop

### Presenation
1. Angular 'Hello world'
2. Templating with ng-repeat

[presentation](/blog/angular-hello.html)

## Simple js objects
* we are working with simple js objects and functions
* no 'extend' magic

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

## Two ways binding
* model is the only source of true
* chanage on model update view
* changes on view update model

## Forms support
* understands html5 attributs - required, pattern, date
* add classes describing input states

```html
<!-- Html updated by angular -->
<form name="exampleForm" class="ng-pristine ng-invalid ng-invalid-required">

    Required field:
  <input ng-model="required" required="" class="ng-pristine ng-invalid ng-invalid-required"></label> <br>

    Email field: 
  <input ng-model="email" type="email" class="ng-pristine ng-valid ng-valid-email"></label> <br>

  <button ng-disabled="!exampleForm.$valid" disabled="disabled">Submit</button>
</form>
```

### Presentation
1. Example of validating code

[presentation](/blog/angular-form.html)

## Dependecy injection
* all dependency of our compotnent is injected as arguments of wrapping function
* defines nicelly interaction between compontents
* increas testability

```js
function HelloCtrl($scope, $window, $log) {
  $scope.message = 'Display me in view';
  $window.alert('Use window via $window service - that improves testability');
  $log.log('We can even test console log calls - thats to $log wrapper');
}
```

## Services
* reusable pieces of code
* injected into controllers, directives and other services
* most of application logic should be placed into services

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

## Routing - $routeProvider
* we can define route (with arguments), redirections etc.
* bookmarkable adresses
* it's cooperate nicely with back and forward
* support routes with and without /#

```js
angular.module('phonecat', [])
  .config(['$routeProvider', function($routeProvider, $locationProvider) {
    // $locationProvider.html5Mode(true);
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

## REST - $resource
* service generating endpoint to communication with 
* synchronously returns empty array or object - to be used in view; when data arrives, empyt shell is filled out

```js
myApp.factory('ProductService', function($resource) {
  var ProductService = {};

  var ProductResource = $resource('/product/:productId');

  ProductService.getItem = function (index) {
    return ProductResource.get({productId: index});
  }

  ProductService.addItem = function (item) {
    ProductResource.save({}, item));
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
* nonstandard tags and attributes defined by angular, or application developer
* extensiate html with new features
* the only place in angular app to do DOM manipulation
* in place of '{expression}' we put 'variable' to get data form $scope.variable
* examples:
 * ng-show - hide element when false
 * ng-hide - hide element when true
 * ng-view - place to put view from route
 * ng-class - allow us to conditionally apply classes
 * ng-switch - diplay one of options

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
* toolset improving programming workflow
* yo - code generator:
 * for angular it generatre:
  * services
  * directives
  * controllers
  * routes - controller, view & route
 * supports other frameworks and plane js apps
* grunt - common task automatization
 * minification and code packaging
 * development server with auto reload
* bower - dependency manangement

### Presentation
1. Open a server and page in a browser
2. Change view and show it in browser

## Karma (Testacular)
* test runner firing our tests in any browser
* it started on machin we are writing code
* browsers are connecting to server which starts tests

## Habits - writing callbacks
* displaying what was received with GET needs no callback
* make sens only when we want to react to success or failer

## Habits - imperative binding
* for that we use directives and \{\{\}\}

## Habits - changing DOM in controller
* we use only directive to modify DOM
* when we write own directives is recomended to have good test coverage

## Gotchas - writing directives
* directives are the tool used for meny core feature
* rough developer experience - especially when compare to other framework features

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

## Gotchas - ng-model in ng-repeat
* ng-repeat creates new scope for each element
* child scopes has parrent as prototype
* ng-model="value" works supprisingly, while ng-model="object.value" as expected
* the same issue is always when we have sub scopes

```html
// Gotcha!
<ul>
  <li ng-repeat="item in list">
    <input ng-model="item" />
  </li>
</ul>

// Work as expected
<ul>
  <li ng-repeat="item in list">
    <input ng-model="item.name" />
  </li>
</ul>
```

## Gotchas - code minification
* bind models with parameters defined on $scope is based on name - proper minification configuration is requried
* dependency injection rely on argument's name

```js
syngularApp.controller('ProductCtrl', function($scope, ProductApi) {
  // easy but minification unfriendly
});

syngularApp.controller('ProductCtrl', ['$scope', 'ProductApi', function($scope, ProductApi) {
  // minification resistant
}]);
```

## Gotchas - $resource
* it's defined in different file
* returns empty array or object - instant console.log() will show nothing

## Gotchas - filters working only on arrays
* ng-repeat will iterate on object - but filter & orderBy will not work

## Gotchas - e2e testing
* setting it up is complicated
* it can be consider a trap-feature

## Gotchas - updating data from outside angula
* most of model update happen in handled by angular
 * getting data from $resource
 * happens in directive related code: ng-model, ng-clic
* in cases when changes are comming form outside of angular world, we need to use $digest function

## Gotchas - $ in service names
* it prevent names conflict between our app and framework
* using $ as prefix in custom services makes no sens

## Materials
* http://angularjs.org/
* http://egghead.io/
* http://www.youtube.com/user/angularjs

## Summary
* ideas form backend programming are comming to js
* AngularJs help us write mature code for browser
* it's good idea to checkout Yeoman

## Contact
* http://marcin-wosinek.github.io/blog/presentation/2013/04/24/AngularJs-AmsterdamJS.html
* @MarcinWosinek
* marcin.wosinek@gmail.com

## Credits
* Audience photo: http://www.flickr.com/photos/dougbelshaw/5604047370/in/photostream
* BackboneJs logo: https://github.com/documentcloud/backbone/blob/master/docs/images/backbone.
* Two ways binding: http://docs.angularjs.org/guide/dev_guide.templates.databinding
* http://karma-runner.github.io/0.8/index.html
* http://yeoman.io/
