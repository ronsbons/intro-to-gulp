# intro-to-gulp

## Overview
gulp.js is a build tool in JavaScript that can automate certain tasks, like compressing images and bundling/minifying CSS and JavaScript files.  It can be configured to modify your original files or create new ones.  Plugins are available to use with Gulp to define its tasks, or you can write your own using JavaScript.  In addition to running tasks, Gulp is a build system, which means it can copy, compile, deploy, test, and lint.

### Uses
Gulp is often used to do frontend tasks like:
- Spinning up a web server
- Reloading the browser automatically whenever you save a file
- Compiling Sass to CSS
- Optimizing all assets (CSS, JS, fonts, and images) for production

### Installing Gulp
``` npm install gulp --save-dev ``` adds gulp as a dev dependency to your project's package.json.

### Structure
Gulp tasks are run from a CLI shell and require package.json and gulpfile.js in the project's root directory.  gulpfile.js is where all the task operations are defined, required plugins are included, and a default task is defined.

A basic example of a gulpfile is:
```
// Adding dependencies
var gulp = require('gulp');
var gutil = require('util-gulp');

gulp.task('hello-world', function() {
  console.log('hello world');
});
```

When you run the command ``` gulp hello-world ``` from the command line, we are telling gulp to run the "hello-world" task in the gulpfile.js.


In the configuration section of the file, you can also specify which folders for Gulp to read and which folders for Gulp to build:
```
var gulp = require('gulp');
var folder = {
  src: 'src/',
  build: 'build/'
};
```

## Findings
Gulp seems like it would be a useful tool for larger-scale projects and to implement it from the start of your project.

## Resources
- [An Introduction to Gulp.js] (https://www.sitepoint.com/introduction-gulp-js/)
- [Wikipedia article] (https://en.wikipedia.org/wiki/Gulp.js)
- [Gulp for Beginners] (https://css-tricks.com/gulp-for-beginners/)
