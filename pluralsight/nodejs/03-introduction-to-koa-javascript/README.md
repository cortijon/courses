# [Introduction to Koa](http://www.pluralsight.com/courses/javascript-koa-introduction)

## 1. Getting Started

### 1.1 Getting Started

- minimalistic: focus in application, and not in the framework
- callback free
- from the future

### 1.2 Installing Koa

- install nvm
- nvm ls-remote: all versions of node (and io.js)
- nvm ls: all installed node versions
- nvm use {version}
- nvm help
- nvm version

### 1.3 Writing our first applications

- node --harmony app.js

## 2. Understanding yield and generators

### 2.1 Introduction

- ES6
- `yield`
- generators = `function *someFunc() {}`

### 2.2 What can I use this for?

### 2.3 How Koa Uses Generators

### 2.4 What about errors?

- top level error handling (return 500)
- use `try {} catch (e) {} finally {}`

### 2.5 Errors you will run into

- forgetting the asterisk
- forgetting to use yield
- forgetting --harmony

### 2.6 Wrapping up

**Y**o, Node
**I**
**E**xpect a
**L**ittle
**D**elay here

## 3. Koa Concepts - the Moving Parts

### 3.1. Introduction

- application
- this = context = request + response

### 3.2 The Application Object

- for testing purposes, always expose the app for other modules

```js
var koa = require( 'koa' );
var app = koa(); // application object
module.exports = koa;
```

or

```js
var koa = require( 'koa' );
var app = module.exports = koa();
```

or


```js
var app = module.exports = require( 'koa' )();
```

- the `.listen()` function
- the `.use()` function

**The use of `.use()`**

```js
var app = require( 'koa' )();
app.use( function *() {

  console.dir( this.request );

});
```

**Using the next parameter to .use()** - see code example

### 3.3 The request object

**Requesting the request**

```js
app.use( function *() {

  var r = this.request;

});
```

**Properties of the request object**

- `request.header`
- `request.method`
- `request.ulr`
- `request.path`

**Functions of the request object**


- `this.request.is( 'json' )`
- `this.request.is( 'html' )`

```js
switch ( this.request.accepts( 'json', 'html', 'text' )) {

  case 'json' : break;
  case 'html' : break;
  case 'text' : break;
  default : this.throw( 406, 'json, html or text only' );

}
```

### 3.4 The Response Object

**Requesting the response**

```js
app.use( function *() {

  var r = this.response;

});
```

**Properties the response**

- `this.response.body = { name : "Eric" }`
- `this.response.status = 404`
- `this.response.type = "application/json"`

**Functions the response**

```js
this.response.set( 'Location', '/user/123' );

this.response.set({
  'Etag' : '1234',
  'Last-Modified' : new Date
});

this.response.redirect( 'http://ericdouglas.github.io' );
```

### 3.5 The context object

- we can remove the `request` and `response`, and use just `this.{property}` or `this.{method}`

See code example

## 4. Building an HTTP with Koa

### 4.1 Introduction

**Initial setup**

- create a folder
- npm init
- two files: `app.js` and `test.js`
- install koa --save
- simple server
- `npm start : node --harmony app.js`

### 4.2 The first method - create new users

### 4.3 The validation

### 4.4 The Getting of one user

### 4.5 The updating of one user... and deleting

## 5. Building a complete website with Koa

### 5.1 Introduction

**Routes - Questions**

Method | Route | Description
:--:|:--:|:--:
GET | / | home
GET | /question | new question form
POST | /question | store new question
GET | /question/:id | display edit form
POST | /question/:id | update question

**Routes - Votes**

Method | Route | Description
:--:|:--:|:--:
GET | /vote?qid=:id | show voting form
POST | /vote | store new form
GET | /vote/:id/comment | show add comment
POST | /vote/:id/comment | add comment

**Routes - Result**

Method | Route | Description
:--:|:--:|:--:
GET | /results | show result filter form
POST | /result | renders report in excel

**Initial setup**

- mkdir koaVote
- npm init

### 5.2 Show Home Page

### 5.3 Refactoring and layout


