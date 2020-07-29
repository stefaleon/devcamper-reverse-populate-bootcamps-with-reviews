# DevCamper API, reverse populate bootcamps with reviews

Original code from Brad Traversy's Udemy course

[https://github.com/bradtraversy/devcamper-api](https://github.com/bradtraversy/devcamper-api)

### Modifications

#### Suggedted by [Xiaoming Wang](https://www.udemy.com/user/xiaoming-wang-9/)

_models/Bootcamp.js_

```
BootcampSchema.virtual('reviewspart', {
  ref: 'Review',
  localField: '_id',
  foreignField: 'bootcamp',
  justOne: false,
});
```

_routes/bootcamps.js_

```
router
  .route('/')
  .get(advancedResults(Bootcamp, 'courses', 'reviewspart'), getBootcamps)
```

_middleware/advancedResults.js_

```
const advancedResults = (model, populate1, populate2) => async (

//...

  if (populate1) {
    query = query.populate(populate1);
  }
  if (populate2) {
    query = query.populate(populate2);
  }

```
