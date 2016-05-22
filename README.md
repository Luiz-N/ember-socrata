Ember-Socrata
=============
An adapter for interacting with Socrata open data services.

Currently, Ember-Socrata only handles Socrata's Consumer API, ie. retrieving data.

# Installation
```bash
ember install ember-socrata
```

# Configuration
In your project's `config/environment.js`:

```javascript 
module.exports = function(environment) {
  var ENV = {
    socrata: { dataRepo: 'some.data-repository.com' },
    // ...
  };
  // ...
};
```

# Usage
For each Socrata dataset you want to retrieve you must create a model and an
adapter:
```bash
ember generate model something
ember generate adapter something
``` 

## Models
In the model you should define attributes as normal, using camelCasedAttributes
where the dataset uses underscored_attributes.

Example:
### Socrata object
```javascript
{
    something_id: 123,
    some_attribute: 'some value',
    related_object_id: 456,
}
```

### Ember model
```javascript
// app/models/something.js

import Model from 'ember-data/model';
import attr from 'ember-data/attr';
import { belongsTo } from 'ember-data/relationships';

export default Model.extend({
    someAttribute: attr(),
    relatedObject: belongsTo('related-object'),
});
```

## Adapters
You must add a `dataset` property with the value of the Socrata dataset to the
model's adapter:
```javascript
// app/adapters/something.js

import ApplicationAdapter from './application';

export default ApplicationAdapter.extend({
  dataset: 'ab12-34xy',
});
```
