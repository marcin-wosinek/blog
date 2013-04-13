---
layout: default
category: presentation
title: BackboneJs in Drupal core DcWroc Wroclaw
tags: [BackboneJs, AngularJs, Drupal, DCWroc, Wrocław]
---
# BackboneJs in Drupal core
TODO:

* figure out slides
* prepare module code example

## How am I?
* Marcin Wosinek
* Currently js contractor in Poznań
* 1 year of working with d6 & d7
* 8 month after swithing completly into frontend js
* Much more experience with AngularJs then BackboneJs

## You?
* Who likes js?
* Who have bad experience with huge browser side js codebases?

## Why js matters?
* there is increasing amount of stuff you can use js for
* all modern engines have decent approach to standards
* rich ui in javascript offers better user experience

## Web 1.0: JS for Almost Nothing

## Web 2.0: JS for AJAX
* unfortunatly most of ajax method return partial html
* seems like what I know from Drupal world

## Web Today: JS for Everything
* emergin patter of front - back end relation
* static js code - front end application
* data get via rest form server
* templates done on browser side

## Challenges
* Coursera: 29k lines of JS code
* cloud9 - js, browser base IDE
* more logic needs better code quality

## jQuery is not enouth
* jQuery is cool, but it's just DOM manipulation library
* beside it we need some sollution for architecture

## Programming best practices in front end?
* in short - front end js used to be quite hacky
* unit tests are rare
* lack of design patterns and serious aproach to architecture

## Solution: Browserside js frameworks
* backbone
* angular
* ember

## Backbone is in Drupal Core
* introduced mid October 2012
* used in edit - inplace editing for fields
* should lead to better dev experience

## What is Backbone?
* one of the most popular js MV\* framework
* dependencies: jQuery, underscore
  * backbone 6.3kb gziped & minified
  * underscore 4kb gziped & minified

## MV* in Bakcbone
* route choose view according to #link
* view is responsible for DOM manipulation

## Model
* one piece of data
* keeps application state

## Collection
* puts together bunch of models
* sync with backend, or other persistant mechanizms

## View
* coordinate user interaction between user and app
* binds DOM events to model
* update DOM on model changes

## Routing
* mechanism of fireing functions based on place in aplication
* allow us to build bookmarkable urls for our backbone views

## Unserscore
* utility belt for js
* foreach, map, reduce, templating

## Front end templating
* allows us to dynamically build html on browser side
* non-hacky approach to ajax

## What we can use Backbone for?
* current implementations
* moving more UX logic into js, while keeping code sane

## Using backbone in a module

(waits for example code)

### Presentation
* code overview
* showing working code

## One page apps
* seems as more resonable design option
* can be design to work off line
* spare server memory and computation power

### Presentation - one page app offline?
(prepare simple off line app)

## AngularJs
* one page app framework
* guide developer through whole process of app creation
 * interface
 * code
 * test

## AngularJs - two ways binding
* we have two ways bingins out of the box
* model is the single source of truth

## AngularJs - testability
* testabiliti is one of main core feature
* uses dependency injection every where
* good cooperation with karma/testacular test runner

## Drupal as webservice
* One page app based on static files, and json communication with drupal

## Questions
* what framework would you recomend?

## Materials
* [Backbone fundamentals by Andy Osmani](http://addyosmani.github.io/backbone-fundamentals/)
* [Choosing right js framework with ToDo MVc](http://todomvc.com/)
* [Backbone tutorials](http://backbonetutorials.com/)
* [AngularJs - one page app tutorial](http://docs.angularjs.org/tutorial)

## Summary
* checkout what's new in browser side js - especially frameworks like Backbone and AngularJs
* Backbone is in drupal core - consider using it in your modules
* We are going to have more one page apps - don't fall behined and turn your drupal site into webservice

## Contact
* link to blog
* marcin.wosinek@gmail.com

## Credits
