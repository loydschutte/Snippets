# Setting Up Express with Handlebars

1. Make sure Express Generator is installed. If not run the following command:

```
npm install -g express-generator
```

2. Run the following command replacing appname with name of your application.

```
express --view=hbs appname
```

3. Change to the directory of your app and install the node modules.

```
cd appname && npm install
```

4. Type the following to start the app.

```
DEBUG=appnam:* npm start
```

5. Open app.js in your editor and find the following 2 lines.

```
app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'hbs');
```

Replace them with these 2 lines.

```
 app.engine('hbs', exphbs({extname: '.hbs', defaultLayout: 'layout'}));
 app.set('view engine', 'hbs');
```

6. Find the following line at the top of app.js

```
var express = require('express');
```

Add this line below it.

```
var exphbs = require('express-handlebars');
```
 
7. Type the following commands in terminal to set up your file structure.

``` 
mkdir views/layouts
mkdir views/partials
mv views/layout.hbs views/layouts/layout.hbs
touch views/partials/header.hbs
```

8. Replace the code in layout.hbs with the following.

```
 <!DOCTYPE html>
  <html>
  <head>
    <meta charset="utf-8">
    <title>Todos</title>
    <link rel="stylesheet" href="../stylesheets/style.css">
  </head>
  <body>
    {{> header}}
    {{{body}}}
    <script src='/javascripts/script.js'></script>
  </body>
  </html>
 ```

 9. Type the following command in terminal to install SASS functionality.
 
 ```
  npm install node-sass-middleware --save
```

10. Find the line below in app.js

```
 var exphbs  = require('express-handlebars');
```

 Add this line below it to use SASS in your templates.

``` 
 var sassMiddleware = require('node-sass-middleware');
```

11. Below this section:

```
 app.engine('hbs', exphbs({extname: '.hbs', defaultLayout: 'layout'}));
 app.set('view engine', 'hbs');
```

 Add this snippet:

``` 
 app.use (
   sassMiddleware({
     src: __dirname + '/sass',
     dest: __dirname + '/public',
     debug: true,
   })
 );
```

12. Remove your old stylesheet and add your SASS stylesheet and directory.

```
mkdir sass
mkdir sass/stylesheets
touch sass/stylesheets/style.scss
```

13. Install browserify by typing the following code in terminal.

```
npm install browserify-middleware --save
```

14. Find the line below:

```
var sassMiddleware = require('node-sass-middleware');
```

Then add this line below it:

```
var browserify = require('browserify-middleware');
```

15. Below the code from line 11 above add:

```
 app.get('/javascripts/bundle.js', browserify('./client/script.js'));
```

16. Type the following 2 lines into terminal

```
mkdir client
mv public/javascripts/script.js client/script.js
```

17. Add the following line to the bottom of your layout.hbs file.

```
<script src='/javascripts/bundle.js'></script>
```

18. Add jQuery to the project by typing the following line in terminal.

```
npm install jquery --save
```

Then add this line to the top of script.js in your client file.

```
var $ = require('jquery');
```

19. Install nodemon with the following line in terminal.

```
npm install nodemon --save-dev
```

Then replace this line in package.json:

```
"start": "node ./bin/www"
```

with the following 2 lines:

```
 "start": "node ./bin/www",
 "dev": "nodemon ./bin/www"
```

20. Type the following 2 commands in terminal to install browser sync:

```
npm install browser-sync --save-dev
npm install connect-browser-sync --save-dev
```

21. Add this section of code after the browserify setup in app.js.

```
if (app.get('env') == 'development') {
  var browserSync = require('browser-sync');
  var config = {
    files: ["public/**/*.{js,css}", "client/*.js", "sass/**/*.scss", "views/**/*.hbs"],
    logLevel: 'debug',
    logSnippet: false,
    reloadDelay: 3000,
    reloadOnRestart: true
  };
  var bs = browserSync(config);
  app.use(require('connect-browser-sync')(bs));
}
```

22. Install SASS support in terminal.

```
npm install bootstrap-sass --save
```

Then add this line at the top of your stylesheets.

```
@import "../../node_modules/bootstrap-sass/assets/stylesheets/bootstrap";
```

Then find this line in app.js:

```
app.use(express.static(path.join(__dirname, 'public')));
```

and add this line below it:

```
app.use('/fonts', express.static(path.join(__dirname, 'node_modules/bootstrap-sass/assets/fonts'))); 
```

Be sure to add a language type to the HTML tag in the layout.hbs file and a meta viewport tag.

```
<html lang="en">
<meta name="viewport" content="width=device-width, initial-scale=1">
```





