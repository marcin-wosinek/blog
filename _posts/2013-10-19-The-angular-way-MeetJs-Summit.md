---
layout: default
category: presentation
title: The angular way - MeetJs Summit
# jvideoId: 9sDiy0QIVuA
# slideShareId: 19963430
tags: [AngularJs, angular way, MeetJs, Gdańsk]
---
# The angular way
Meet js summit Gdańsk 19 October 2013

## Who am I?
* Marcin Wosinek
* 5 years IT experience
 * WebDev: Javascript
 * C# dev: UnitTests
* Currently js contractor in Roche in Poznan, Poland

## You?
* Who have heard about angular?
 * positives?
 * negatives?
* Who have used angular?

## The buzz
* 'by google'
* plenty of talks
* testability
* short and readable code
* two ways binding

## Reality
* it's not a silver bullet
* just a tool - and for some problems it's good fit, while for others not

## Common pitfall
* So we have a lot of browser side js frameworks
* and non of them works without js on the browser side
* it's tricky to make search engine index your content

## Lynx
* that still happens

## Ie6
* that too

## Angular strong points (screens - a lot of working apps)
* one page app
* dynamic components of html pages
* complex forms - fields depending on each other
* dealing with rest serivices
* in short: boring busines panges - on which probably most of us works daily

## Note:
* point 1 \& 2 makes transition form legacy html page to hip one page apps really smooth:
* we can start writing new features of legacy system in angular
* gradully refactor old code onto angular
* up to removing all jQuery code or even backend rendering

## Angular domain (screens of examples)
* admin pages - page edits, managing usert etc.
* shop carts and checkout pages

## Angular domain - NOT (screens of contre examples)
* view of wikipedia like sites
* games

## Angular MV*
* model provided by services - fed with data from rest service
* view - html with angular-specific extensions: direcitives
* controler - code directly binded with view
* directives - js that deals with DOM manipulation

## Concepts separation
* you can touch DOM only in directives - doing it in controler is very bad idea
* controlers are supposed to have as little logic as posibile - getting data form REST, and data manipulation should be placed in services
* while it's possible to have computiation in view, it's more testable to have it in controlers

## Directives
* it's essential to use them
* but only useful to write them
* before we decide to become senior angular developer - just reuse already existing ones in angular core, angular ui and other libraries

```js
<ANY ng-show="{expression}">
<input ng-model="variable">

<ng-view> <any ng-view>

<ANY ng-class="{expression}">

<ANY ng-switch="expression">
  <ANY ng-switch-when="matchValue1">...</ANY>
  <ANY ng-switch-when="matchValue2">...</ANY>
  ...
  <ANY ng-switch-default>...</ANY>
</ANY>
```

## Modules - idea
* packages containing all code - controllers, services, directives
* modules can depend on others - then our code can be easily splited into multiple modules
* only one main module, used as the root of application

## Modules - spliting code
* keeping directives in seperate files
* 'one module for one page'

## Testability
* dependency injection
* declarative views

```html
<div ng-repeat="project in projects | filter:search | orderBy:'name'"> </div>

<form ng-submit="addTodo()">
  <input ng-model="todoText" />
</form>
```

```js
function HelloCtrl($scope, $window, $log) {
  $scope.message = 'Display me in view';
  $window.alert('Use window via $window service - that improves testability');
  $log.log('We can even test console log calls - thats to $log wrapper');
}
```

## Keeping code testable
* NEVER touch DOM in controler
* split move logic into services
* use angular replacements for core javascript: $window, $log, $timeout
* write tests first - it's the easiest way to have testable code

## Karma
* pretty cool test runner
* we start server, and then connect the browsers
* code is run in real browsers
* extra fast - I have about 300 tests executed in about 4 seconds

## Test frameworks
* core tests in jasmine (veryfiy it)
* mocka and others frameworks are supported

## Yeoman
* development workflow

## Grunt
* The JavaScript Task Runner
* build - minification, merging files, sass compliation
* server - nice server that force reload when we change our files, and helps uns in prototyping

## Yo generators
* cool tool that allows us to generate code that fits into really nice scaffolging
* we don't need to figure out Gruntfile.js, bower packange file, karmaconfig, jshint configuration and test files ourself
* even if we don't plan to use ie any of the tools, everything will be prepared if we change our mind later

## Materials
* [egghead io](https://egghead.io)
* [youtube/angularjs](http://www.youtube.com/user/angularjs/videos)
* [ng-module](http://ngmodules.org)	
* books (disclaimer: neither of them I've read):
 * [Mastering Web Application Development with AngularJS](http://www.packtpub.com/angularjs-web-application-development/book)
 * [AngularJS from O'Reilly](http://www.amazon.com/AngularJS-Brad-Green/dp/1449344852)

## AngularJs community
* [fb.com/groups/angularjs.polska](https://www.facebook.com/groups/angularjs.polska)
* There is an idea to make one day angular meeting - ng-camp

## Summary
* angular shares a lot with other js frameworks
* main advantages is testability
* while angular offers really nice architecture framework, it is us who shape the quality of code

## Questions?

## Contact
* [http://bit.ly/angular-meetjs-summit](http://bit.ly/angular-meetjs-summit)
* @MarcinWosinek
* marcin.wosinek@gmail.com
* [google plus](https://plus.google.com/108223112357727405944)

## Credits
* Audience photo: http://www.flickr.com/photos/dougbelshaw/5604047370/
* Bees photo: http://www.flickr.com/photos/theseanster93/4056815767/
* hammer & screw: http://www.flickr.com/photos/justinbaeder/5317820857
