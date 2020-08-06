### NODE Learning Lessons Log
- This is a log for me to store the information I learn day to day in my experiences with NODE, and will serve as reference point when I may have questions or concerns regarding the methodology behind how to use NODE.

# Starting a Node App:

```sql
npm init -y
```

# Node modules:
(how to make them, export them, and import them)

```sql
npm i express
npm i ejs
npm i express-ejs-layouts
```

# Node packages 
(NPM packages you have used/researched)

- empty-trash
- one-liner-joke
- express
- ejs
- express-ejs-layouts

# Adding express to a node app

```sql
const express = require('express');
const app = express();
```

# Express routes

```sql
const express = require('express');
const router = express.Router();

router.get('/animals', function(req, res) {
    res.render('hates/animals', {title: 'Hated Animals', animals: ['snakes', 'eels']})
});

router.get('/foods', function(req, res) {
    res.render('hates/foods', {title: 'Hated Foods', foods: ['quinoa', 'chicken liver', 'duck']})
});

module.exports = router;
```

# Views
- make a new folder in the explorer to reference, call it 'views'
```sql
app.set('view engine', 'ejs')
```
- all of the nested files will now run on .ejs as opposed to .js

# Templates

```sql
app.set('view engine', 'ejs')
app.use(ejsLayouts);

app.use('/faves', require('./controllers/faves'))
app.use('/hates', require('./controllers/hates'))
```

# Layouts
Setup: (on index.js)
```sql
const express = require('express')
const app = express()
const ejsLayouts = require('express-ejs-layouts');

app.set('view engine', 'ejs')
app.use(ejsLayouts);

app.listen(8000);
```

Template: (on layout.ejs)
```sql
<!DOCTYPE html>
<html>
    <head>
        <title>Faves&Hates</title>
    </head>
    <body>
        <%- body %> 
    </body>
</html>
```

Routed using: (get & render)
```sql
app.get('/animals', function(req, res) {
  res.render('animals', {title: 'Favorite Animals', animals: ['sand crab', 'corny joke dog']})
});
```
JavaScript that can be written in each each .ejs file:
```sql
<h1><%= title %></h1>
<ul>
  <% foods.forEach(function(food) { %>
    <li><%= food %></li>
  <% }) %>
</ul>
```

# Controllers
On our .js page we would update the directory path added and add a router/export:
```sql
const express = require('express');
const router = express.Router();

router.get('/animals', function(req, res) {
    res.render('hates/animals', {title: 'Hated Animals', animals: ['snakes', 'eels']})
});

router.get('/foods', function(req, res) {
    res.render('hates/foods', {title: 'Hated Foods', foods: ['quinoa', 'chicken liver', 'duck']})
});

module.exports = router;
```
Reference to new directory:
```sql
app.use('/faves', require('./controllers/faves'))
app.use('/hates', require('./controllers/hates'))
```
