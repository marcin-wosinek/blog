---
layout: default
category: presentation
title: The angular way - MeetJs Summit
# jvideoId: 9sDiy0QIVuA
# slideShareId: 19963430
tags: [AngularJs, angular way, MeetJs, Gdańsk]
---
# The angular way (sharp turn)

There is a lot of positive buzz about angular in front end js framework community - directives, two-way bindings, 'by google'. There is as well some critic - it's bigger then backbone, unlike ember it does dirty checking. In this presentation we will take a look on 'the angular way' the set of practice that is necessary to know if we want to fairy judge angular. So we will take a look on:
* TDD and unit tests with karma test runner
* yo generators
* grunt server
* angular separation of concerns

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

## (screen of serverfault site in Lynx)

## (screen of ie6 - with tones of bars)

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
* animations

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

## Modules - idea (draw graf of modules - angular ui; application core; application user and application admin)
* packages containing all code - controllers, services, directives
* modules can depend on others - then our code can be easily splited into multiple modules
* only one main module, used as the root of application

## Modules - spliting code
* keeping directives in seperate files
* 'one module for one page'

## Testability
* dependency injection
* declarative views

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
* [https://egghead.io](egghead io)
* [http://www.youtube.com/user/angularjs/videos](youtube/angularjs)
* [http://ngmodules.org](ng-module)	
* books (disclaimer: neither of them I've read):
 * [http://www.packtpub.com/angularjs-web-application-development/book](Mastering Web Application Development with AngularJS)
 * [http://www.amazon.com/AngularJS-Brad-Green/dp/1449344852](AngularJS from O'Reilly)

* [http://angularjs.org/](http://angularjs.org/)
* [http://egghead.io/](http://egghead.io/)
* [http://www.youtube.com/user/angularjs](http://www.youtube.com/user/angularjs)

## AngularJs community
* group on facebook: url
* There is an idea to make one day angular meeting - ng-camp

## Summary
* angular shares a lot with other js frameworks
* main advantages is testability
* while angular offers really nice architecture framework, it is us who shape the quality of code

## Contact
* http://marcin-wosinek.github.io/blog/presentation/2013/10/19/The-angular-way-MeetJs-Summit.html
* @MarcinWosinek
* marcin.wosinek@gmail.com
* [google plus]

## Credits
* Audience photo: http://www.flickr.com/photos/dougbelshaw/5604047370/
* Bees photo: http://www.flickr.com/photos/theseanster93/4056815767/
* hammer & screw: http://www.flickr.com/photos/justinbaeder/5317820857
