# Mongoose

node.js를 이용해 우아하게 mongodb 객체를 모델링 해준다.

## Schemas

```javascript
var mongoose = require('mongoose');
var Schema = mongoose.Schema;

var blogSchema = new Schema({
  title:  String,
  author: String,
  body:   String,
  comments: [{ body: String, date: Date }],
  date: { type: Date, default: Date.now },
  hidden: Boolean,
  meta: {
    votes: Number,
    favs:  Number
  }
});
```

### find

`Model.find(conditions, [fields], [options], [callback])`

* Parameters:

    ```javascript
    conditions <Object>
    [fields] <Object> optional fields to select
    [options] <Object> optional
    [callback] <Function>
    ```

* code

    ```javascript
    // named john and at least 18
	MyModel.find({ name: 'john', age: { $gte: 18 }});
    
    // executing a query explicitly
    var query = MyModel.find({ name: /john/i }, null, { skip: 10 })
    query.exec(function (err, docs) {});

	```

* link
	>http://mongoosejs.com/docs/api.html#model_Model.find

## 참고링크

Schemas
http://mongoosejs.com/docs/guide.html

Mongoose API
http://mongoosejs.com/docs/api.html

