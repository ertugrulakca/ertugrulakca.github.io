---
layout: post
title:  "Mongoose Paginate"
date:   2024-10-28 22:30:00 +0300
categories: nodejs
---

### Custom

```js
const page = req.query.page > 0 ? (req.query.page ?? 1) : 1;
    const limit = req.query.limit ?? 50;
    const offset = (page - 1) * limit;

    const movies = await Movie.aggregate([
        {
            $project: {
                title: true,
                year: true,
                imdb: true,
                poster: true
            }
        },
        {
            $skip: offset
        },
        {
            $limit: limit
        }
    ]);

    res.render('movies/index', {movies});
```

### With Module(mongoose-paginate)

```shell
npm install mongoose-paginate
```

* Schema

```js
const mongoose = require('mongoose');
const mongoosePaginate = require('mongoose-paginate-v2'); // add this line

const Schema = mongoose.Schema;

const MovieSchema = new Schema({
    title: {
        type: String,
        required: true,
    },
    plot: {
        type: String,
    },
    poster: String,
    year: Number,
    imdb: Object,
    directors: Array,
    released: Date
}).plugin(mongoosePaginate); // add this line


module.exports = mongoose.model('movies', MovieSchema);
```

* Controller

```js
const page = req.query.page ?? 1;
const limit = req.query.limit ?? 15;
const search = req.query.search ?? '';
const filter = {};

if (search) {
    filter.title = {$regex: `${search}`};
}

const movies = await Movie.paginate(filter, {
    page,
    limit,
    projection: {title: 1, year: 1, poster: 1, imdb: 1}
}).then({});
```
