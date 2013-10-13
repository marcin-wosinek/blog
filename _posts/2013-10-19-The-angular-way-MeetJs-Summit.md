---
layout: default
category: presentation
title: The angular way - MeetJs Summit
# jvideoId: 9sDiy0QIVuA
# slideShareId: 19963430
published: false
tags: [AngularJs, angular way, MeetJs, Gdańsk]
---
# The angular way (sharp turn)

There is a lot of positive buzz about angular in front end js framework community - directives, two-way bindings, 'by google'. There is as well some critic - it's bigger then backbone, unlike ember it does dirty checking. In this presentation we will take a look on 'the angular way' the set of practice that is necessary to know if we want to fairy judge angular. So we will take a look on:
* TDD and unit tests with karma test runner
* yo generators
* grunt server
* angular separation of concerns

## Who am I? (rogale)
* Marcin Wosinek
* 5 years IT experience
 * WebDev: Javascript
 * C# dev: UnitTests
* Currently js contractor in Roche in Poznan, Poland

## Questions:
* Who have heard about angular?
 * praises?
 * critics?
* Who have used angular?

## The buzz (bees or logos)
* 'by google'
* plenty of talks
* testability
* short and readable code

## Reality (hummer and scrows)
* it's not a silver bullet
* just a tool - and for some problems it's good fit, while for others not

## Common pitfall (logos)
* So we have a lot of browser side js frameworks
* and non of them works without js on the browser side
* all of them needs tricks to show their content to search engines

## Angular is good at: (screens)
* one page app
* dynamic components of html pages
* complex forms - fields depending on each other
* dealing with rest serivices
* in short: boring busines panges - on which probably most of us is working everyday

## Note: (refactoring related pic)
* point 1 \& 2 makes transition form legacy html page to hip one page apps really smooth
* we can start writing new features of legacy system in angular
* gradully refactor old code onto angular
* up to removing all jQuery code or even backend rendering

## Angular domain
* admin pages - page edits, managing usert etc.
* shop carts and checkout pages

## Angular domain - NOT
* view of wikipedia like sites
* games

## Angular MV*
* model provided by services - feed with data from rest service
* view - html with angular-specific extensions: direcitives
* controler - code directly binded with view
* directives - js that deals with DOM manipulation

## Concepts separation
* you can touch DOM only in directives - doing it in controler is very bad idea
* controlers are supposed to have as little logic as posibile - getting data form REST, and data manipulation should be placed in services
* while it's possible to have computiation in view, it's more testable to have it in controlers

## Directives
* essential to use them
* but only usefull to write them
* before we decide to become senior angular developer - just reuse already existing ones in angular core, angular ui and other libraries

## Testability
* dependency injection
* declarative views

## Keeping code testable
* NEVER touch DOM in controler
* split move logic into services
* use angular replacements for core javascript: $window, $log, $timeout

## Karma
* pretty cool test runner
* we start server, and then connect the browsers
* code is run in real browsers

## Supported test framewokrs
* core tests in jasmine (veryfiy it)
* moca and others frameworks are supported

## Modules - idea (draw graf of modules - angular ui; application core; application user and application admin)
* packages containing all code - controllers, services, directives
* modules can depend on others - then our code can be easily splited into multiple modules
* only one main module, used as the root of application

## Modules - spliting code
* keeping directives in seperate files
* 'one module for one page'

## Yeoman
* development workflow

## Grunt
* build - minification, merging files, sass compliation
* server - neat server that for reload when we change our files

## Yo generators
* cool tool that allows us to generate code that fits into really nice scaffolging
* we don't need to figure out Gruntfile.js, karmaconfig, jshint configuration and test files ourself
* even if we don't plan to use ie karma, everything will be prepared if we change our mind later

## Materials
* ng-module


* [http://angularjs.org/](http://angularjs.org/)
* [http://egghead.io/](http://egghead.io/)
* [http://www.youtube.com/user/angularjs](http://www.youtube.com/user/angularjs)

## Summary
* angular shares a lot with other js frameworks
* main advantages is testability
* while angular offers really nice architecture framework, we can still develop our code to be untestable and unmaintainable

## Contact
* http://marcin-wosinek.github.io/blog/presentation/2013/10/19/The-angular-way-MeetJs-Summit.html
* @MarcinWosinek
* marcin.wosinek@gmail.com

## Credits
