---
id: 505
title: Deliver Your Site Faster With Critical CSS
date: 2016-01-20T09:00:43+00:00
author: Adrian Eufracio
description: 'CSS files are getting larger and for good reason. Our web projects are larger and more robust than ever but but do we need an entire CSS file to create the user interface. Critical is a npm package that scans a page of your website and returns an output of the necessary CSS for the page. '
layout: post
guid: http://adrianeufracio.com/?p=505
permalink: /deliver-your-site-faster-with-critical-css/
categories:
  - css
---
The modern day web experience is much more complicated and robust then it was ten years ago which means are CSS stylesheets have grown in size. A large CSS file will slow down a site but we need this CSS to create the user interface.
  
<img src="http://adrianeufracio.com/wp-content/uploads/2016/01/Untitled-1.png" alt="A user interface" width="400"  class="alignnone size-full wp-image-508" srcset="http://adrianeufracio.com/wp-content/uploads/2016/01/Untitled-1-300x200.png 300w, http://adrianeufracio.com/wp-content/uploads/2016/01/Untitled-1-419x279.png 419w, http://adrianeufracio.com/wp-content/uploads/2016/01/Untitled-1-460x307.png 460w, http://adrianeufracio.com/wp-content/uploads/2016/01/Untitled-1-240x160.png 240w, http://adrianeufracio.com/wp-content/uploads/2016/01/Untitled-1.png 600w" sizes="(max-width: 600px) 100vw, 600px" />
  
But do we need an entire CSS file to create the user interface. What about the rest of the UI that isn&#8217;t visible to the user? Like the UI as you scroll down the page or the UI on a completely different page. We are loading CSS to create UI components that are not needed when a page loads. CSS is a render blocking resource which means that the entire CSS file needs to be parsed before the browser can load anything else. Loading a large resource where only part of it is needed creates a web experience that is begging for a solution. Wouldn&#8217;t it be better to load the necessary, critical CSS that is visible to the user and load the rest when it&#8217;s needed. While this solution is not achievable, there is a something we can do to create a similar experience. Instead we can load the CSS that is needed to compose the initial user interface and then load the rest of the CSS asynchronously. This way we render the visible user interface quickly while avoiding a render blocking resource. We can do this with two tools that are available today, **Critical** and **loadCSS**.

## Critical

<a href="https://github.com/addyosmani/critical" target="_blank">Critical</a>, created by [Addy Osmani](https://addyosmani.com/), is a node.js package that uses <a href="http://casperjs.org/" target="_blank">CasperJS</a> to scan a page of your website and returns an output of the necessary CSS for the page. 

    //lets take a look at the code
    critical.<span class="blue">generate</span>({
        base: '<span class="orange">test/</span>',
        src: '<span class="orange">index.html</span>',
        dest: '<span class="orange">styles/critical.css</span>',
        width: 1300,
        height: 900
    });

The above code looks for <i class="code-term">index.html</i>, scans it using [Phantomjs](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=phantomjs), and returns <i class="code-term">critical.css</i> in the styles folder which is the CSS that is necessary for the user interface to render properly. The UI is defined with width and height parameters of 1300 x 900. All we need to do now is remove our <i class="code-term">main.css</i> from the head of our web document and place <i class="code-term">critical.css</i> in the head.

    <head>
    <link href="styles/critical.css" rel="stylesheet">
    ...
    ...
    </head>

## loadCSS

We still need to find a way to load our <i class="code-term">main.css</i> asynchronously. This is where [loadCSS](https://github.com/filamentgroup/loadCSS) comes into play. loadCSS is a JavaScript function, created by <a href="https://www.filamentgroup.com/" target="_blank">Filament Group</a>, that loads CSS asynchronously. All we need to do is place the function in the head of the document and then pass our <i class="code-term">main.css</i> as an argument in that function.

    <head>
    <script>
      // include loadCSS here...
      <span class="blue">function loadCSS</span>( href, before, media ){ ... }
      // load a file
      <span class="blue">loadCSS</span>( "<span class="orange">styles/style.css</span>" );
    </script>
    <head>

## Going A Little further

It is recommended to inline the critical CSS that is generated using Critical in the head of the web document as it eliminates a round-trip for the server. So instead of this&#8230;

    <head>
    <link href="styles/critical.css" rel="stylesheet">
    ...
    ...
    </head>

We do this&#8230;

    <head>
    <style>
    body{line-height:1}ol,ul{list-style:none}....
    </style>
    ...
    ...
    </head>

Also it is safe to assume that the layout for the home page looks different then the layout for the about page. For this reason it would be best to have a different critical stylesheet for each of these pages. I use grunt and a grunt plugin called grunt-critical to produce these results.

    // in our gruntfile.js, install grunt critical via cli
    npm install grunt-critical --save-dev

    //Add the critical task for multiple pages
    criticalcss: {
          home: {
            options: {
              url: '<span class="orange">index.html</span>',
              width: 1200,
              height: 736,
              filename: '<span class="orange">css/style.css</span>',
              outputfile: '<span class="orange">css/critical-home.min.css</span>',
              //add some minification magic :)
              minify: <span class="green">true</span>
            }
          },
          about: {
            options: {
              url: '<span class="orange">about.html</span>',
              width: 1200,
              height: 736,
              filename: '<span class="orange">css/style.css</span>',
              outputfile: '<span class="orange">css/critical-about.min.css</span>',
              //add some minification magic :)
              minify: <span class="green">true</span>
            }
          }
        }
    //Load our grunt-critical dependency
    grunt.loadNpmTasks('<span class="orange">grunt-critical</span>');

## Conclusion

It is best to implement and test your results with Critical. As noted by <a href="https://chrisruppel.com/" target="_blank">Chris Ruppel</a> over at <a href="http://fourkitchens.com/" target="_blank">Four Kitchens</a>, the inlined css should not exceed 10kb due to HTTP packet size restrictions. An interface that loads quickly is the end result of implementing Critical which yields major benefits. Adding Critical to your ever expanding workflow is a tool vital tool in a webdev toolkit. 

## Critical Resources

  * <a href="http://fourkitchens.com/blog/article/use-gulp-automate-your-critical-path-css" target="_blank">Use Gulp Automate Your Critical Path CSS By Four Kitchens</a>
  * <a href="https://github.com/addyosmani/critical" target="_blank">Critical By Addy Osmani</a>
  * <a href="https://github.com/bezoerb/grunt-critical" target="_blank">Grunt Plugin CriticalCSS</a>
  * <a href="https://www.smashingmagazine.com/2015/08/understanding-critical-css/" target="_blank">Understanding Critical CSS By Dean Hume</a>