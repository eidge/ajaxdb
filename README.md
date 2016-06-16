#AjaxDb

AjaxDb is a framework agnostic data layer for your front-end. It aims to be the single-source of
truth for data, effectively solving data synchronization across components and API
whether you're using React, AngularJs or some other front-end framework.

# Motivation

Having gone through most of the modern front-end frameworks, I keep seeing the same
challenge over and over again solved in different ways. The main problem with
front-end applications is **keeping state** and keeping it **in sync** across all the
different components.

React solves this with Redux and immutable data, AngularJS uses data-binding
and shared objects across components. Both solutions with it's merits and
problems but none of them perfect.

When digging a bit deeper it becomes clear that the problem is that we do not
have a single-source of truth for data in the front-end (Actually we do, it's
the API but is rather slow).

**AjaxDb** is a POC for a front-end data-layer that merges both an API client
layer and a database with data subscriptions.

# Getting Started

## Instalation

## AjaxDb

**AjaxDb** represents your store and is your interface to create models.

You either use the default one:

```javascript
User = AjaxDb.Model.create({
  url: '/api/users/:id'
});
```

Or create your own store with overriden configuration:

```javascript
MyStore = AjaxDb.create({
  http: {
    updateMethod: 'patch'
  },
  cacheStore: MyCacheStore,
  baseUrl: '/api/v2'
});

User = MyStore.Model.create({
  url: '/users/:id'
});
```

## AjaxDb.Model

```javascript
User = AjaxDb.Model.create(
  url: '/api/users/:id',
  constructor: function(user) {}
  methods: {
    all: { method: 'get', path: '/' }
    get: { method: 'get', path: '/:id' },
    create:  { method: 'post' },
    update:  { method: 'put', '/:id' },
    destroy: { method: 'delete', '/:id' },
  },
  fields: {
    firstName: AjaxDb.Field.String,
    lastName:  AjaxDb.Field.String,
    birthDate: AjaxDb.Field.Date
  }
)

User.prototype.fullName = function() {
  return this.firstName + ' ' + this.lastName;
}
```

## AjaxDb.Collection
## AjaxDb.Request
## AjaxDb.Field

  - #toApi
  - #fromApi

## AjaxDb.Field.String
## AjaxDb.Field.Number
## AjaxDb.Field.Datetime

## XHRBackend

