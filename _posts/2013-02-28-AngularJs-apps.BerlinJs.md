---
layout: default
category: presentation
title: AngularJs apps.BerlinJs
videoId: eGvZr5EFk7M#t=488s
tags: [AngularJs, BerlinJs, Berlin]
---
# AngularJs
### apps.berlin.js 28 February 2013
Handouts:

* [slides](https://docs.google.com/presentation/d/1lAWCOU_ELJEKAy4kKldXVaF5fOITsWpqqVCLSXsdubo/edit#slide=id.p)
* [utils install script](https://github.com/marcin-wosinek/angular-dev)
* [vbox with all utils installed](https://docs.google.com/folder/d/0Bzhquk4DfXAtYUhKNlJhb01jaEk/edit)

## Who am I?
* Marcin Wosinak
* 5 years experience in IT
  * WebDev: Javascript
  * C# dev: UnitTests
* Currently js contractor in Poznań, Poland

## You?

* Who was already working with angular?
* Who likes having unit tests?
* Who is using yeoman?

## What is AngularJs

* it's application framework
* it's 29KB compressed and minified
 * backbone is 19KB (with underscore & backbone)
 * backbone is 32KB (with lodash & jQuery)
 * ember is 49KB
* no dependencies:
 * can use jQuery if available on loadtime

## AngularJs Overview
* MVVM [G+] [1]
* Plain js object
* Dependency injection
* TESTABILITY!
* Directives
* Declarative programming

## MVVM architecture
* plain js models
* dirty checking - but object.observer is comming

```js
function TodoCtrl($scope, $log) {
  // use console log
  $log.log('Test');

  $scope.addTodo = function() {
    $scope.todos.push({text:$scope.todoText, done:false});
    $scope.todoText = '';
  };
 
  $scope.remaining = function() {
    var count = 0;
    angular.forEach($scope.todos, function(todo) {
      count += todo.done ? 0 : 1;
    });
    return count;
  };
 
  $scope.archive = function() {
    var oldTodos = $scope.todos;
    $scope.todos = [];
    angular.forEach(oldTodos, function(todo) {
      if (!todo.done) $scope.todos.push(todo);
    });
  };
}
```

## Dependency injection
* increase testablity
* nice sumarize interconnections between parts of aplication

```js
$scope; // view model
$log; // console: ie friendly
$window; // testable window counter part
$http; // http requests
// and all our services
```

## Directives
* tools to teach html new tricks
 * binding controller

```html
<div ng-controller="ProductCtrl">
```

 * loops

```html
<ul>
  <li ng-repeat="friend in friends">
    [{{$index + 1}}] {{friend.name}} who is {{friend.age}} yrs old.
 </li>
</ul>
```

 * binding models

```html
<input type="checkbox" ng-model="confirmed" ng-change="change()"
```

* or bing back old ones

```html
<blink>Click me</blink>
```

* No dom manipulation in controler!

## Declarative programming
* What we have in html, css now is in js as well
* html: want paragraph?

```html
<p>Text</p>
```

* css: want it red?

```css
p { color: red}
```

* js: what it bind to model - we are writing in pure html

```html
<p>{{modelData}}</p>
```

## TESABILITY!
* Dependency injection
* Directives
* simple plain old js objects as models

```js
//Code:
function PasswordCtrl($scope) {
  $scope.password = '';
  $scope.grade = function() {
    var size = $scope.password.length;
    if (size > 8) {
      $scope.strength = 'strong';
    }
    else if (size > 3) {
      $scope.strength = 'medium';
    }
    else {
      $scope.strength = 'weak';
    }
  };
}

// test:
var scope = {};

var pc = new PasswordCtrl(scope);
pc.password('abc');
pc.grade();
expect(scope.strength).toEqual('weak');
```

## Doubt
* for some even deal breakers

## html validator are going to hate it
* those tags are invalide

```html
<tabs>
   <pane title="Localization">
```

* those atributs are invalide

```html
<li ng-repeat="todo in todos">
<input type="text" ng-model="todoText" />
```

* and this little guy was purpouse fully removed from html

```html
<blink>CLICK ME!</blink>
```

## Back to 90's?
* angular uses proprietery tags, allow us to create own, and expect us to write stuff like this:

```html
<form ng-submit="addTodo()">
<button ng-click="fireAlert()">
```

## Not proper tags
* all directives: tags and attributes
* for attributes there is data-\* or x-\* version
* tag directives needs shim for ie8

## No - it's our future
* web components
* shadow dom 

Will be native apis. Now we can get some of benefits with angular.
All is safly separeted into scopes.

## Shadow DOM
* Used by browsers internally to create controls
* Will expose the same featres to web devs
* In working draft http://www.w3.org/TR/shadow-dom/
* Nice overview http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom/ 

## Yeoman
* CLI
* cool tool to creating code
* push changes form server to broswer - no refreshing

## Testacular
* Test runner
* Runs tests in reall browsers
* Works on linux, don't need graphic env
* Build by angular team, all angular tests are on testacular
* Works with jasmine, sinon

## Want to give it a try?
* I've prepared vbox for you with dev env
* Full machine https://docs.google.com/folder/d/0Bzhquk4DfXAtYUhKNlJhb01jaEk/edit?usp=sharing - based on ubuntu server
 * user: developer
 * pass: developer
* Install script https://github.com/marcin-wosinek/angular-dev

## How to start with angular?
* Is possible to use in legacy projects
* Goes well allong with jquery
* There is a project to rewrite bootstrap js to angular directives [angular-ui-bootstrap] [2]
* They say it is possible to use it along with require.js [angular-require-js] [3]

## Questions?
* If our css doesn't go well with ng-show and ng-hide give try with ui-if from angular-ui

## How to catch me
* marcin.wosinek@gmail.com
* \#marcin.wosinek
* write up and links:
* http://marcin-wosinek.github.com/angular.berlin.js

[1]: https://plus.google.com/+AngularJS/posts/aZNVhj355G2   "G+"
[2]: http://angular-ui.github.com/bootstrap/   "angular-ui-bootstrap"
[3]: https://github.com/elsom25/angular-requirejs-html5boilerplate-seed   "angular-require-js"
