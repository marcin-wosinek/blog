---
layout: default
title: AngularJs handouts
---
# Handout
## Learning materials
* 50+ free videos covering basic and advanced stuff from angular: [http://egghead.io](http://egghead.io)
* 25+ presenations form angularJs headquater: [http://www.youtube.com/user/angularjs](http://www.youtube.com/user/angularjs)
* 25+ presentation form the first angular conference: [http://www.youtube.com/user/ngconfvideos](http://www.youtube.com/user/ngconfvideos)
* official tutorial: [http://docs.angularjs.org/tutorial](http://docs.angularjs.org/tutorial)
* book:
 * **"AngularJS"** by Brad Green & Shyam Seshadri - basic (I've read and recommend)
 * **"Mastering Web Application Development with AngularJS"** by Pawel Kozlowski \&
   Peter Bacon Darwin - advanced. Looks good because of author renome and good
   reviews. I haven't read.
* course on codecademy - [http://www.codecademy.com/courses/javascript-advanced-en-2hJ3J/0/1](http://www.codecademy.com/courses/javascript-advanced-en-2hJ3J/0/1) . Only views covered for now.

## Libraries
That I'm using:

* **angular-ui** [http://angular-ui.github.io](http://angular-ui.github.io) - pack of high quality components; eg.:
 * **bootstrap** - twitter bootstrap js rewritten in pure angular js
 * **ui-select2** - directive to integrate with select2 widget 
* **angular-nestedSortable** [http://github.com/JimLiu/Angular-NestedSortable](http://github.com/JimLiu/Angular-NestedSortable) - sortable directive

That looks very promissing:

* **restangular** [http://github.com/mgonto/restangular](http://github.com/mgonto/restangular) - rest library
* **routeSegment** [http://angular-route-segment.com](http://angular-route-segment.com) - when core routing is becoming not enough

Module directory: [http://ngmodules.org](http://ngmodules.org)

## Tools
What I use

* **yeoman** [http://yeoman.io](http://yeoman.io) - not just a tool, but a workflow
 * **yo** - code generators
 * **grunt** [http://gruntjs.com](http://gruntjs.com) - 'task runner' for js. Think rake or maven.
 * **bower** [http://bower.io](http://bower.io) - package manage (npm) for frontend
* tests:
 * **jasmine** [http://pivotal.github.io/jasmine](http://pivotal.github.io/jasmine) - test framework with beautify syntax
 * **karma** [http://karma-runner.github.io](http://karma-runner.github.io) - test runner

That one looks promissing

 * **protractor** [http://github.com/angular/protractor](http://github.com/angular/protractor) - angular with selenium
   integration form angular & karma team

## Where goes what?
* **controllers** - simple, view related logic
* **services** - complex logic; controllers integration; integration with rest 
  services; domain knowledge
* **directives** - DOM manipulation, reusabe widgets
* **filters** - manipulating data with display in mind, ie: data formating,
  in memory searches etc.

## To avoid bad practices
* never touch DOM in controller, service nor filter. Directives are the single
  place where you can play with DOM directely.

## Recommended uses
* admin pages
* pages available only for logged user
* intranet pages

All pages where we have a lot of forms.

## NOT recommended uses
* wikipedia clones: pages where is more content then interaction
 * although there are hacks to prerender sites in **phantomjs** and serve them
   as static html to crowlers
* games
