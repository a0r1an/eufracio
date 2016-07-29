---
id: 318
title: Automate Your Workflow With Gulp
date: 2015-11-18T09:00:21+00:00
author: Adrian Eufracio
description: 'As Front-End Developers, we are sometimes overcome with the amount of work that goes into building a simple website.  How can we automate time-consuming tasks in our development workflow.Gulp provides developers the toolbox to automate the tasks in their workflow. '
layout: post
guid: http://adrianeufracio.com/?p=318
permalink: /automate-your-workflow-with-gulp/
categories:
  - javascript
---
As Front-End Developers, we are sometimes overcome with the amount of work that goes into building a simple website. It is amazing all the tasks that go into a website to make it function properly and look good on the many devices available. Whether it be optimizing images, creating sprites or minifying files These tasks are often done more than once. This contradicts with the DRY principle of not repeating ourselves. How can we automate time-consuming tasks in our development workflow.

## Introducing Gulp

<a href="http://gulpjs.com/" target="_blank">Gulp</a> quenches our thirst for an automated task workflow. It provides developers the toolbox to automate the tasks in their workflow. Gulp can compile CSS, optimize images, transpile JavaScript, minify files, and concatenate files just to name a few. Gulp can do this and more thanks to the developer community of <a href="https://www.npmjs.com/" target="_blank">NPM</a>, Node Package Manager. With Gulp, it is easy to add and remove tasks to a project depending on the projects end goal.

## Get Started

    // file structure for this article
    <span class="pink">index.html</span>
    scss/
    scss/<span class="pink">style.scss</span>
    // Leave the css folder empty for now
    css/

Before you start using Gulp you need to [install](https://nodejs.org/en/) Node.js, a JavaScript runtime. Node.js comes with NPM, a package ecosystem. We will use NPM to install Gulp. To do this open your CLI, Command Line Interface, and type in <i class="code-term">npm install &#8211;global gulp</i>. This will install Gulp globally on your computer. Navigate to your projects folder with CLI and type <i class="code-term">npm init</i>. You will be prompted to fill out the information that will be saved into a **package.json** in your directory. **package.json** will hold all your projects dependencies. Now we can install Gulp as a dependency in your project by typing this in your CLI<i class="code-term">npm install &#8211;save-dev gulp</i>. **package.json** file should look something like this.

    // Note: name and version are the only required fields to have package.json work properly
    {
      "name": "adrian",
      "version": "1.0.0",
      "description": "",
      "main": "index.html",
      "author": "",
      "license": "ISC",
      "devDependencies": {
        "gulp": "^3.9.0"
      }
    }

Notice how Gulp was added to your devDependencies and also how a **node_modules** folder was also created in your directory. **node_modules** holds all the devDependencies files. Last thing before we start coding is to create a **gulpfile.js** inside our project directory. **gruntfile.js** contains the code that creates our automated tasks. At a minimum it will contain this code.

    // gruntfile.js
    // Load our gulp module
    <span class="pink">var</span> gulp = require('<span class="orange">gulp</span>');
    // Task is a gulp function that defines our task
    gulp.task('<span class="orange">default</span>', <span class="blue">function</span>() {
      // code goes here
    });

<i class="code-term">gulp.task</i> takes three arguments <i class="code-term">name</i>, <i class="code-term">deps</i>, and <i class="code-term">function</i>. <i class="code-term">name</i> is the name of the task and can be anything but cannot include spaces. <i class="code-term">deps</i> is an optional array that contains all of the tasks that will run and complete before your task runs. <i class="code-term">function</i> executes the task&#8217;s code. Here is a simple example of a Gulp task that will log to your CLI.

    // gruntfile.js
    <span class="pink">var</span> gulp = require('<span class="orange">gulp</span>');
    <span class="pink">var</span> gutil = require(‘<span class="orange">gutil</span>’);
    gulp.task('<span class="orange">default</span>', <span class="blue">function</span>() {
       return gutil.<span class="blue">log</span>(’<span class="orange">You created a task that says you created a task!</span>');
    });

This code is well and good but we want to create a useful task. A task that will save us time and do the work for us.

## Convert Sass To CSS With Gulp

One of the most common tasks a Front-End Dev does is compile their Sass to CSS. Lets have Gulp do this for us! First we must add the Gulp plugin for Sass as a devDependency. We do this by installing the Sass package. <i class="code-term">npm install gulp-sass &#8211;save-dev</i> Now Sass is installed as a devDependency! For Sass to be accessed through Gulp, we must call it in the form of the <i class="code-term">require()</i> function.

    <span class="pink">var</span> gulp = require('<span class="orange">gulp</span>');
    <span class="pink">var</span> sass = require('<span class="orange">gulp-sass</span>');

The <i class="code-term">require()</i> function is part of the Node syntax and it gives us access to our modules, devDependencies. Now that we have access to Sass we can create the task.

    <span class="pink">var</span> gulp = require('<span class="orange">gulp</span>');
    <span class="pink">var</span> sass = require('<span class="orange">gulp-sass</span>');
    gulp.task('<span class="orange">sass</span>', <span class="blue">function</span> () {
      gulp.src('<span class="orange">./scss/*.scss</span>')
        .pipe(sass().on('<span class="orange">error</span>', sass.logError))
        .pipe(gulp.dest('<span class="orange">./css</span>'));
    });

<i class="code-term">gulp.task()</i> is named sass and returns a function that does three things. It defines what files to convert using the <i class="code-term">gulp.src()</i> function. <i class="code-term">gulp.src()</i> can be a string or array that tells the task what files to use. In the example above, I am telling Gulp to look inside of **/scss/** for any files with a file extension of <i class="code-term">.scss</i>. Then we use the <i class="code-term">pipe()</i> function to log a an error if Sass notices one. <i class="code-term">pipe()</i> function is also part of the Node syntax that reads and writes data. We then chain off <i class="code-term">gulp.src()</i> again and use the <i class="code-term">pipe()</i> function to pass another function called <i class="code-term">gulp.dest()</i>. <i class="code-term">gulp.dest()</i> function takes all the data that has been passed so far in our function and spits it out into the path you wish. In our example, it takes the the Sass files we targeted with <i class="code-term">gulp.src()</i> and inserts them in **/css/**.

Now in our CLI, we can tell Gulp to run the sass task &#8230; <i class="code-term">gulp sass</i>. Check your **css** folder and you have a shiny new stylesheet called **style.css**. You just created your first Gulp task but how can we make this task even more of a time saver. Wouldn&#8217;t it be nice to have **style.css** update whenever **style.scss** updates?

## Even More Automated

We start by creating another task. This time we will name the task default.

    gulp.task('<span class="orange">default</span>', <span class="blue">function</span>() {
    // we will add our code here
    });

The benefit of naming the task default is that Gulp recognizes this name and in the CLI you simply type <i class="code-term">gulp</i> and anything in your default Gulp task will be executed. Now we will add a <i class="code-term">gulp.watch()</i> function and provide it two values. The first value will tell the function which files to watch for changes and the second task will be the task that runs when the files that are being watched change.

    gulp.watch('<span class="orange">./scss/*.scss</span>', ['<span class="orange">sass</span>']);

<i class="code-term">gulp.watch()</i> watches all files in the **scss** folder with a **.scss** extension and runs the sass task that we created above. Now when we run <i class="code-term">gulp</i> in our CLI, Gulp will constantly watch our sass files for changes and update **style.css** leaving us free to code.

## Handy Automated Tasks

Here are some more handy tasks you can add to your gulp file.

## Compress and Optimize Images And SVGs

    // CLI
    npm install --save-dev gulp-imagemin

    // gulpfile.js
    <span class="pink">var</span> imagemin = require('<span class="orange">gulp-imagemin</span>');
    <span class="pink">var</span> pngquant = require('<span class="orange">imagemin-pngquant</span>');
    gulp.task(‘<span class="orange">imagemin</span>', () => {
        return gulp.src('<span class="orange">images/*</span>')
            .pipe(imagemin({
                progressive: <span class="green">true</span>,
                svgoPlugins: [{removeViewBox: <span class="green">false</span>}],
                use: [pngquant()]
            }))
            .pipe(gulp.dest(‘<span class="orange">img</span>'));
    });

## Minify Javascript Files

    // CLI
    npm install --save-dev gulp-uglify

    // gulpfile.js
    <span class="pink">var</span> uglify = require('<span class="orange">gulp-uglify</span>');
    gulp.task('<span class="orange">compress</span>', <span class="blue">function</span>() {
      return gulp.src('<span class="orange">lib/*.js</span>')
        .pipe(uglify())
        .pipe(gulp.dest('<span class="orange">dist</span>'));
    });

## Convert Images To A Sprite

    // CLI
    npm install --save-dev gulp.spritesmith

    // gulpfile.js
    <span class="pink">var</span> spritesmith = require('<span class="orange">gulp.spritesmith</span>');
    gulp.task('<span class="orange">sprite</span>', <span class="blue">function</span>() {
      var spriteData = gulp.src('<span class="orange">images/*.png</span>').pipe(spritesmith({
        imgName: '<span class="orange">sprite.png</span>',
        cssName: '<span class="orange">sprite.css</span>'
      }));
      return spriteData.pipe(gulp.dest('<span class="orange">path/to/output/</span>'));
    });

## Final gulpfile.js

    <span class="pink">var</span> gulp = require('<span class="orange">gulp</span>');
    <span class="pink">var</span> sass = require('<span class="orange">gulp-sass</span>');
    <span class="pink">var</span> imagemin = require('<span class="orange">gulp-imagemin</span>');
    <span class="pink">var</span> pngquant = require('<span class="orange">imagemin-pngquant</span>');
    <span class="pink">var</span> uglify = require('<span class="orange">gulp-uglify</span>');
    <span class="pink">var</span> spritesmith = require('<span class="orange">gulp.spritesmith</span>');
    
    gulp.task('<span class="orange">default</span>', <span class="blue">function</span>() {
      gulp.watch('<span class="orange">./scss/*.scss</span>', ['<span class="orange">sass</span>']);
    });
    gulp.task('<span class="orange">sass</span>', <span class="blue">function</span> () {
      gulp.src('<span class="orange">./scss/*.scss</span>')
        .pipe(sass().on('<span class="orange">error</span>', sass.logError))
        .pipe(gulp.dest('<span class="orange">./css</span>'));
    });
    gulp.task(‘<span class="orange">imagemin</span>', () => {
        return gulp.src('<span class="orange">images/*</span>')
            .pipe(imagemin({
                progressive: <span class="green">true</span>,
                svgoPlugins: [{removeViewBox: <span class="green">false</span>}],
                use: [pngquant()]
            }))
            .pipe(gulp.dest(‘<span class="orange">img</span>'));
    });
    gulp.task('<span class="orange">compress</span>', <span class="blue">function</span>() {
      return gulp.src('<span class="orange">lib/*.js</span>')
        .pipe(uglify())
        .pipe(gulp.dest('<span class="orange">dist</span>'));
    });
    gulp.task('<span class="orange">sprite</span>', <span class="blue">function</span>() {
      var spriteData = gulp.src('<span class="orange">images/*.png</span>').pipe(spritesmith({
        imgName: '<span class="orange">sprite.png</span>',
        cssName: '<span class="orange">sprite.css</span>'
      }));
      return spriteData.pipe(gulp.dest('<span class="orange">path/to/output/</span>'));
    });
    

## Conclusion&#8230; Not Really

Now you can copy and paste your **gulpfile.js** and **package.json** in your other projects and in your CLI type in <i class="code-term">npm install</i> and all the packages in your **package.json** file will be installed. You are now on the road to having an optimized Front-End workflow. Many of the plugins I have mentioned above have their own options and settings that can be configured to your likely. I highly encourage you to checkout their documentation to further your optimization skills.

## Gulp Resources

  * <a href="http://gulpjs.com/" target="_blank">Gulp</a>
  * <a href="https://github.com/gulpjs/gulp/blob/master/docs/API.md" target="_blank">Gulp API</a>
  * <a href="https://nodejs.org/en/docs/" target="_blank">Node API</a>
  * <a href="https://www.npmjs.com/package/gulp-sass" target="_blank">Sass for Gulp</a>