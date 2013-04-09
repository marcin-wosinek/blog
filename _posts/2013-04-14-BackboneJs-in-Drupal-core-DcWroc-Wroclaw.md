---
layout: default
category: presentation
title: BackboneJs in Drupal core DcWroc Wroclaw
tags: [BackboneJs, AngularJs, Drupal, DCWroc, Wrocław]
---
# BackboneJs in Drupal core
TODO:

* PREPARE MODULE CODE EXAMPLE
* finish notes
* figure out slides

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

## Emerging pattern of back-front end relationship
* static js code - front end application
* data get via rest form server
* templates done on browser side

## Chalanges
* more logic needs better code quality

## jQuery is not enouth
* jQuery is cool, but it's just DOM manipulation library 
* beside it we need some sollution for architecture
(screen with jquery description about it self: What is jQuery? section from http://jquery.com/)

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

## What is Backbone?
* one of the most popular js MV\* framework
* dependencies: jQuery, underscore
  * backbone 6.3kb gziped & minified
  * underscore 4kb gziped & minified

## MV* in Bakcbone
* some graph with explanation

## Model
* one pice of data 
* TODO check model responsibilities

## View
* binds DOM events to model
* update DOM on model changej 
* TODO check view responsibilities

## Collection
* puts together bunch of models
* TODO check collection responsibilities

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

## Using backbone in a module

(waits for example code)

### Presentation
* code overview
* showing working code

## One page apps

### Presentation - one page app offline?

## Drupal as webservice
* One page app based on static files, and json communication with drupal

## Questions

## Materials

## Summary
* checkout what's new in browser side js - especially frameworks Backbone and AngularJs
* Backbone is in drupal core - consider using it in your modules
* We are going to have more one page apps - don't fall behined and turn your drupal site into webservice

## Contact
* link to blog
* marcin.wosinek@gmail.com

## Credits
