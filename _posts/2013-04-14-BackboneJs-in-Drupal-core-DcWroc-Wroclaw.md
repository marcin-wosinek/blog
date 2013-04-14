---
layout: default
category: presentation
title: BackboneJs in Drupal core DcWroc Wroclaw
slideShareId: 18783227
tags: [BackboneJs, AngularJs, Drupal, DCWroc, Wrocław]
---
# BackboneJs in Drupal core
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

## Advantages of new approach
* we embrace http wiht REST
* we make server to care just only about data - not markup
* we save server resource, using client resource

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
* entity
* one piece of data
* keeps application state

```js
app.Todo = Backbone.Model.extend({
  defaults: {
    title: '',
    completed: false
  },

  toggle: function () {
    this.save({
      completed: !this.get('completed')
    });
  }
});
```

# Template
* html tags mixed with {{ name }} or
* backbone cooperate with many different sollutions - underscore, handlebar etc.

```js
var html = _.template('<li><%= name %></li>', { name: 'John Smith' });
```

## Collection
* puts together bunch of models
* sync with backend, or other persistant mechanizms

```js
var TodoList = Backbone.Collection.extend({
  model: app.Todo,

  localStorage: new Backbone.LocalStorage('todos-backbone'),
```

## View
* simillar to controllers in frameworks
* coordinate user interaction between user and app
* binds DOM events to model
* update DOM on model changes

```js
app.AppView = Backbone.View.extend({

  el: '#todoapp',

  statsTemplate: _.template($('#stats-template').html()),

  events: {
    'click #clear-completed': 'clearCompleted',
  },

  initialize: function () {
    this.$input = this.$('#new-todo');

    this.listenTo(app.Todos, 'add', this.addOne);
  }

  clearCompleted: function () { /* */},

  addOne: function () { /* */}
}
```

## Router
* mechanism of fireing functions based on place in aplication
* allow us to build bookmarkable urls for our backbone views

```js
var AppRouter = Backbone.Router.extend({
  routes: {
    "posts/:id": "getPost",
  }
});

var app_router = new AppRouter;
app_router.on('route:getPost', function (id) {
  alert( "Get post number " + id );
});

Backbone.history.start();
```

## Unserscore
* utility belt for js
* adds features to js
* foreach, map, reduce, templating

## Front end templating
* allows us to dynamically build html on browser side
* non-hacky approach to ajax

## What we can use Backbone for?
* it isn't crowlable by google
* features for content authors, and loged user
* moving more UX logic into js, while keeping code sane

## Using backbone in a module

```php
function backbone_todo_library_info() {
  $path = drupal_get_path('module', 'backbone_todo');

  $options = array(
    'scope' => 'footer',
    'attributes' => array('defer' => TRUE),
  );

  $libraries['backbone_todo'] = array(
    'title' => 'Backbone todo list',
    'version' => '0.1.0',
    'js' => array(
      $path . '/js/todo.js' => $options,
    ),

    'dependencies' => array(
      array('system', 'jquery'),
      array('system', 'underscore'),
      array('system', 'backbone'),
    )
  );

  return $libraries;
}
```

### Presentation
* code overview
* showing working code

## Yeoman
* dev workflow tool box
* yo - code generator
 * for backbone we have
  * router
  * view
  * model
  * collection
 * supports other frameworks - angularjs
* grunt - automatization of common tasks
 * minimize file
 * development server with automatic page refresh
* bower - front end dependancies

### Presantation
1. Enable server and open page in browser
2. Add route
3. Add model
4. Auto refresh

(TODO - prepare presentation)

## Drupal as webservice
* One page app based on static files, and json communication with drupal

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

## Questions
* what framework would you recomend?

## Materials
* [Backbone fundamentals by Andy Osmani](http://addyosmani.github.io/backbone-fundamentals/)
* [Choosing right js framework with ToDo MVc](http://todomvc.com/)
* [Backbone tutorials](http://backbonetutorials.com/)

## Summary
* checkout what's new in browser side js - especially frameworks like Backbone and AngularJs
* Backbone is in drupal core - consider using it in your modules
* We are going to have more one page apps - don't fall behined and turn your drupal site into webservice

## Contact
* link to blog
* marcin.wosinek@gmail.com

## Credits
* logo of BackboneJs: https://github.com/documentcloud/backbone/blob/master/docs/images/backbone.png
* logo of AngularJs:https://github.com/angular/angular.js/blob/master/images/logo/AngularJS.exports/AngularJS-large.png
* http://www.teaching-materials.org/jsmvc/#/2
* http://www.teaching-materials.org/jsmvc/#/3
* http://www.teaching-materials.org/jsmvc/#/4
* http://www.teaching-materials.org/jsmvc/#/18
* photo with audience http://www.flickr.com/photos/dougbelshaw/5604047370/in/photostream/ 
* kid in sandbox: http://www.flickr.com/photos/thenickster/266142840/
* underscore logo: https://github.com/documentcloud/underscore/blob/master/docs/images/underscore.png
