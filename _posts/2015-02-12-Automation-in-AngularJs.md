---
layout: default
category: presentation
title: Automation in AngularJs - Las Palmas Dev Ops
# videoId: 9sDiy0QIVuA
# slideShareId: 19963430
tags: [AngularJs, Las Palmas Dev Ops, Las Palmas]
---
# AngularJs
## Who am I?
* Marcin Wosinek
* 7 years IT experience, along the way I've learned
 * C# dev: UnitTests
 * WebDev: pain of spagetti code
* from Poland, currently based in Las Palmas
* remote contractor for Softwear from Amsterdam, Netherlands

## Who are you?
* devs
* operations
* QA

## AngularJs?
* client side application framework
* the most popular one
* talks with rest api and renders at frontend
* More in [last year talk](http://marcin-wosinek.github.io/blog/presentation/2014/01/31/AngularJs-Las-Palmas-de-GC.html).

## Learning resource
* [egghead](http://egghead.io)
* [youtube/angularjs](http://www.youtube.com/user/angularjs)
* [ngconf videos](http://www.youtube.com/user/ngconfvideos)
* [ng-europe](https://www.youtube.com/channel/UCEGUP3TJJfMsEM_1y8iviSQ)
* [ng-air](https://ng-air.github.io/)

## Steep learning curve
* more natural for java devs then webdevs
* angular typical concepts make entry more difficult
* pretty comfortable plateau of productivity
* internal complexity leaks when we start writing own directives or have 1000+ bindings at page

## Softwear loop
* code is written, build & tested
* only after passing all tests (automatic or manual) gives us reason to trust the code

## Recycling 
* we need to make effort to keep order
* we live in the middle of garbage we create

## Impact of feedback delay on controll
* quick feedback => stable process
* late feedback => pretty rough

## Realistic expectation
* feedback from unit tests in around 60s
* feedback from integration below 15 min

## Previous project
* 400-500 unit tests => 10s/2min
* integration (manual, understaffed) => 3days-3weeks (max 6 months)

## 3rd party code update fail
* angular-ui, angular-select2 etc.
* application used every january:( sometime during the year we break it, and learned that next time when user came

## Profits/costs
* we save time, and prevent crises
* it takes time to build it
* our manangement needs to understands importance of automation
* [stack overflow careers](http://careers.stackoverflow.com/)

## What tools do you know to automate common tasks in front end development?

## yeoman
* code generator
* let a develop start quickly
* reusable code patterns

## example code structure for angular
* sub generator take care of fitting new files into that structure

## core team supports generators for  
* backbone
* ember
* jQuery plugin
* chrome app

## bower - frontend package manager
* maven/gem/pip for the browser
* manage loading all the external libs in the correct versions

## bower - flat dependency tree
* browser reads all file from one level - so all dependencies are installed next to each other

## bower - bower screens
* module description in bower.json
* dependecy conflict resolution

## task menagement
* automate code build
* grunt - first that got a lot of traction
* grunt file will grow...
* gulp - currently the hip one. created to address grunt issue

## purpose of grunt
* expose CLI command for common task

## Quality assurance

## Can you see the code?

## I can't :(
* I'm pretty sensitive to code style issues
* it's quite common among programmers - some don't care, but many care (too much)
* many open source project enforce consistent coding style

## JSCS
* code style enforcer
* is meant to be part of development process
* can be run by grunt

## JSCS conf
* in json
* fine grained configuration

## JSHint
* code linter
* static code analysis 
* catch issues in code:
 * non matching brakets
 * missing semicolons
* best to be integrated with code editor
* double checked by grunt at CI server

## JShint example output

## Jasmine
* bdd test framework
* play nicely in tdd
* nice flexible syntax
* almost plain english test reports
* good to install 'jasmine-expect':
 * array & object related matchers

## Karma
* test runner
* one server to rule all browsers

## Protractor
* selenium wrapper
* understands angular & waits for internals to finish execution

## Phantomjs & dependants
* webkit browser with (only) js interface
* headless and scriptable browser
* casperjs - wrapper on phantomjs, makes api easier to work wiht
* pageres - cli tool to taking page screens at different resolution

## Frisby
* npm module for testing http api
* after all frontend is doing QA for backend. So let's do it in the smart way

## Requirements
* (almost) all tools are written in js
* server side js
* npm as a dependency manager
* nvm - cli utility that takes care of managin multiple node version at the same machine

## Dependency tree @ npm
* nested dependency tree
* same module can exist in different version

## CI
* all QA task should be run as part of CI process
* projects at github plays nicely with travis-ci

## Release flow
* code is kept in source repo
* after build, code is pushed to separate git repo
* code is available for bower/npm etc
* "poor man's artifact repository"

## Semver
* strictly defined version meaning
* well established in js comunity
* *major* - bracking changes
* *minor* - non breaking changes, extending existing api
* *patch* - error fixes

## Summary
* angular is go-to framework for Single Page App
* automation leads to quality
* automation for front-end is pretty impresive

## Questions?

## ngConf extended
* conference in Salt Lake City, US
* provides streaming for remote comunities to watch live
* March 5-6, 2015
* drop me a line if you want to watch it in LPGC
* sessions:
 * Angular inside google
 * Building Platforms with angular.js
 * Ionic + Angular - mobile development
 * How organize Angular 1.3 app for Angular 2.0
 * NG-WAT?
 * es6 in angular

## Contact
* [marcin.wosinek+lpa@gmail.com](mailto:marcin.wosinek+lpa@gmail.com)
* [@MarcinWosine](https://twitter.com/MarcinWosine)
