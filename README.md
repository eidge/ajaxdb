# Getting Started

```
User = AjaxDb.Model.create(
  url: '/api/users',
  constructor: function(carer) {}
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
