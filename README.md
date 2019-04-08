# intro-to-gulp
<img src="https://raw.githubusercontent.com/gulpjs/artwork/master/gulp-2x.png" alt="Gulp logo">

## Overview
gulp.js is a build tool in JavaScript that is a task manager. Gulp can automate certain tasks, optimize your images to a smaller size, bundling/minifying CSS and JavaScript files and do other various things through plugins .  It can be configured to modify your original files or create new ones.  Plugins are available to use with Gulp to define its tasks, or you can write your own using JavaScript.  In addition to running tasks, Gulp is a build system, which means it can copy, compile, deploy, test, and lint.

### Uses
Gulp is often used to do frontend tasks like:
- Spinning up a web server / running a local server
- Reloading the browser automatically whenever you save a file
- Compiling Sass to CSS
- Minifying code
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


#### Task Methods
There are three primary task methods:
- ```gulp.task```: defines a new task with a name, optional array of dependencies, and a function
- ```gulp.src```: sets the folder where source files are located
- ```gulp.dest```: sets the destination folder where build files will be placed.

In the configuration section of the file, you can also specify which folders for Gulp to read and which folders for Gulp to build:
```
var gulp = require('gulp');
var folder = {
  src: 'src/',
  build: 'build/'
};
```

### Example
#### Image Task
This example compresses images and copies them to the appropriate ```build``` folder using plugins: [gulp-newer](https://www.npmjs.com/package/gulp-newer) and [gulp-imagemin](https://www.npmjs.com/package/gulp-imagemin).

1. Install the plugins
``` npm install gulp-newer gulp-imagemin --save-dev ```

2. Include the plugins in the gulpfile.js
```
var
  gulp = require('gulp'),
  newer = require('gulp-newer'),
  imagemin = require('gulp-imagemin');
```

3. Define the image processing task as a function
```
gulp.task('images', function() {
  let out = folder.build + 'images/';
  return gulp.src(folder.src + 'images/**/*')
    .pipe(newer(out))
    .pipe(imagemin({ optimizationLevel: 5 }))
    .pipe(gulp.dest(out));
});
```
- Define a new task called 'images'
- Define an ```out``` folder where build files will be located
- Sets the Gulp ```src``` folder and the ```/**/*``` ensures that images in sub-folders are also processed
- Pipe all files to the ```gulp-newer``` plugin.  Source files that are newer than destination files are passed through.  ```.pipe()``` is a JavaScript function that takes an "n" sequence of operations.  Each operation takes an argument, processes it, and gives the output as the input for the next operation in the sequence.
- The remaining new or changed files are piped through the ```gulp-imagemin``` plugin
- The compressed images are output to the Gulp ```dest``` folder

To run the task, run ```gulp images``` from the command line.


## Findings
Gulp seems like it would be a useful tool for larger-scale projects and to implement it from the start of your project.  There are many plugins that you can use with Gulp, but at least for smaller projects, the time it takes to understand the plugin and how to implement it may be more hassle than defining a task yourself.

### Advantages
- Gulp helps you end up with a cleaner and easier to read task file with greater consistency between tasks.
- Uses Node.js streams that doesn't need temporary files and folders.  You put one file in, you get one out.

## Resources
- [gulp.js](https://gulpjs.com/)
- [An Introduction to Gulp.js](https://www.sitepoint.com/introduction-gulp-js/)
- [Wikipedia article](https://en.wikipedia.org/wiki/Gulp.js)
- [Gulp for Beginners](https://css-tricks.com/gulp-for-beginners/)
- [How to Use Gulp.js to Automate Your CSS Tasks](https://www.sitepoint.com/automate-css-tasks-gulp/)
- [How to minify your CSS with gulp](https://medium.freecodecamp.org/how-to-minify-your-css-with-gulp-6ff3f4a896b5)
- [A Beginners Guide to the Task Runner Gulp](https://andy-carter.com/blog/a-beginners-guide-to-the-task-runner-gulp)

