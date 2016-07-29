---
id: 263
title: Starting With Sass
date: 2015-11-11T09:00:59+00:00
author: Adrian Eufracio
description: "CSS is an easy way to style websites but it lacks features that developers need. Sass is a scripting language that is interpreted into CSS. Sass provides features that CSS doesn't like Variables, Mixins, Operators and other functionality that is available in other object-orientated languages."
layout: post
guid: http://adrianeufracio.com/?p=263
permalink: /starting-with-sass/
categories:
  - css
---
The world wide web first came into existence in 1989 thanks to the almighty Tim Berners-Lee. Since then, the web has grown leaps and bounds. Websites are not just blogs and simple static websites. We have seen the growth of web apps in the past decade and more recently we see these web apps compete with native apps for overall usage. But do not get it twisted, we still use HTML and CSS to create our layouts! CSS is an awesome and easy way to style websites but sometimes it is lacking in features that current developers are in desperate need for. How do we solve this predicament.

## Introducing Sass

Sass is a scripting language that is interpreted into CSS. Sass provides features that CSS doesn&#8217;t like Variables, Mixins, Operators and other functionality that is available in other object-orientated languages. These features makes CSS more dynamic and capable to create the complex web apps that are pertinent on the web today.

## Installing Sass

Sass was built on top of Ruby, a programming language. That means we need to have Ruby installed into our OS to begin your journey with Sass.
  
**Mac Users**
  
Ruby is already pre-installed on Mac. If you want a quick and dirty way to install Sass, type the following in your terminal application.

    sudo gem install sass

For security reasons, this way of installing packages is not recommended. Instead install <a href="http://brew.sh/" target="_blank">Homebrew</a>, a package manager that lets you install packages safely, by typing the following in terminal.

     ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Now we can use Homebrew to install Sass by typing this into your terminal.

    brew install sass

**Window Users**
  
Window users need to install Ruby. This can be done easily by using <a href="http://rubyinstaller.org/" target="_blank">RubyInstaller</a>. Once downloaded and installed, open your command prompt and type in the following.

    gem install sass

## Let’s Play With Sass!

Now that we have our development environment ready, we can start using Sass in our projects. Hopefully you have a CSS folder within your projects folder .In that folder, create a <i class="code-term">.scss</i> file. Look at the structure below for an example.

    /* project folder */
    - <span class="pink">index.html</span>
    - images/
    - css/
    - css/<span class="pink">style.scss</span>

We must navigate to the CSS folder&#8217;s location in your terminal/command prompt. Once there, we run this command

    sass style.scss style.css

This will grab your Sass file, style.scss, and convert it into a CSS file called style.css. Note: You can name your Sass file anything you want as long as it has the <i class="code-term">.scss</i> extension at the end. Likewise your outputted CSS file can be named anything you want as long as it has a <i class="code-term">.css</i> extension at the end. For example&#8230;

    /* This will work but obviously dont do this. */
    sass fish.scss sushi.css

Sass can also watch your file for changes and output an updated CSS file when done. This is done by typing this in your terminal/command prompt

    sass —watch style.scss:output.css

CSS files can be pretty large and it is an industry standard to minimize CSS files when pushing them to a production environment. There are many third-party minifiers but Sass cuts out the middle man and uses its own minifier. Earlier in the article, I mentioned converting your Sass file into a CSS file by typing <i class="code-term">sass style.scss style.css</i> in your terminal/command prompt. To output a minified CSS file, type this into your terminal/command prompt.

    sass style.scss style.css:compressed

## What Does A Sass File Look Like?

Sass does not overcomplicate the syntax. It uses the same syntax as CSS with some additional syntax additions that are easy to understand and similar to other programming languages. But we don’t want to go through the whole process of installing Sass to write plain ol’ css! Lets go ahead and make use of the tricks that Sass provides.

## Nesting

Nesting is exactly what it sounds like. With nesting, we can nest selectors within selectors. This gives our code a better visual hierarchy.

    /* Sass */
    <span class="pink">.a</span> {
     <span class="pink">.b</span> {
      font-size: <span class="orange">1em</span>; 
     }
    } 
    /* This will output the css below */
    /* CSS */
    <span class="pink">.a .b</span> {
     font-size: <span class="orange">1em</span>;
    }

What nesting also affords us is the ability to reference the parent selector using the <i class="code-term">&</i> symbol.

    /* Sass */
    <span class="pink">.selector</span> {
     background: <span class="orange">green</span>;
     <span class="pink">&:hover</span> {
      background: <span class="orange">red</span>;
     }
    }
    /* This will output the css below */
    /* CSS */
    <span class="pink">.selector</span> {
     background: <span class="orange">green</span>;
    }
    <span class="pink">.selector:hover</span> {
     background: <span class="orange">red</span>;
    }

Keep in mind that you don’t want to nest every bit of code that you have since this can cause css specificity problems. I would advise to be cautious of where and how you nest.

## Variables

One of the most requested features for CSS is Variables. Variables can be found in every programming language. They make it easy to store values to a specific string. With Sass we can now use variables.

    $green : <span class="orange">#dafadf</span>;
    <span class="pink">.a</span> {
     color: <span class="orange">$green</span>;
    }

This is a really simple example but lets analyze what this allows us to do. Now that we have a hex value assigned to this <i class="code-term">$green</i> variable we can now call the variable, <i class="code-term">$green</i>, anywhere in our Sass file and it will give us the exact green we are looking for without worrying if we have the correct color. Lets see a more common example.

    $primary color : <span class="orange">#acacac</span>;
    $secondary color : <span class="orange">#333333</span>;
    $primaryfont : <span class="orange">arial, sans-serif</span>;
    $secondary font : <span class="orange">georgia, serif</span>;

With variables we can assure consistency by storing reusable code in handy and easy to read variables. This makes standardizing CSS much more manageable which is imperative in large, complex projects.

## Mixins

With CSS, it is common to reuse styles from one element to another. Wouldn&#8217;t it be nice to group some of these often used styles and insert them into other elements. Mixins provide a way for us to reuse styles in a more semantic manner.

<p data-height="268" data-theme-id="20621" data-slug-hash="VvVZJM" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/VvVZJM/'>Basic CSS</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>


  
Lets refactor this code using mixins!

<p data-height="268" data-theme-id="20621" data-slug-hash="QjJLXP" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/QjJLXP/'>Mixin Example</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>


  
This code immediately becomes more semantic and manageable. Now we can reuse the <i class="code-term">big-text</i> mixin and incorporate the styles attributed to it easily. Mixins also take arguments making them even more handy and powerful.

<p data-height="268" data-theme-id="20621" data-slug-hash="EVOxYg" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/EVOxYg/'>More Mixins</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>


  
**Bonus Mixin!**
  
My last [article on flexbox](http://adrianeufracio.com/flexbox-101/) describes the need for prefixing your css properties. This is where something like a mixin comes in handy. In the below example we will create a Mixin that turns an element to a flex container and adds all the necessary prefixes to make the flex container work properly on as many devices as possible.

<p data-height="268" data-theme-id="20621" data-slug-hash="GpwJax" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/GpwJax/'>Flexbox Mixin</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>


  
Web Design Weekly provides a <a href="https://web-design-weekly.com/2013/05/12/handy-sass-mixins/" target="_blank">list</a> of Mixins that you can use in your own development.

## Extends

Extend allows developers to reuse styles from one css selector to another. 

<p data-height="268" data-theme-id="20621" data-slug-hash="WQYNbW" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/WQYNbW/'>Extend Example</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>


  
Extends does provide us with extra functionality but it does cause some drawbacks. Extends could cause code bloat when extending a already extended selector.

<p data-height="268" data-theme-id="20621" data-slug-hash="OyaJVa" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/OyaJVa/'>Over Extend</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>


  
The above code will output this lengthy CSS selector.

    <span class="pink">.header, .header2, .header2 .inlineheader, .header4</span> {
      font-family: <span class="orange">arial</span>;
      font-size: <span class="orange">18px</span>;
      color: <span class="orange">#000</span>;
      font-weight: <span class="orange">bold</span>;
    }
    <span class="pink">.header2, .header2 .inlineheader</span> {
      padding: <span class="orange">20px</span>;
      float: <span class="orange">left</span>;
    }

Using Extends could also inadvertently link together selectors that have no relationship with one another. 

    /* Sass */
    <span class="pink">.bold</span> {
    font-weight: <span class="orange">bold</span>;
    }
    ...
    <span class="pink">h1</span> {
    @extend <span class="orange">.bold</span>;
    }
    ...
    <span class="pink">.button</span> {
     @extend <span class="orange">.bold</span>;
    }
    ...
    <span class="pink">.header-text</span> {
     @extend <span class="orange">.bold</span>;
    }
    /* This will output the css below */
    /* CSS */
    <span class="pink">.bold,h1,.button,.header-text</span> {
     font-weight: <span class="orange">bold</span>;
    }

Each selector can be hundreds of lines apart and creating a relationship between elements leads to non-semantic, unorganized code. Also Extend cannot be used inside of media queries.

    @media (max-width:1000px) {
     <span class="pink">.b</span> {
      @extend <span class="orange">.a</span>;
     }
    }

This will cause Sass to throw an error. For these reasons it is recommended to use Mixins in place of Extends as they have the same functionality but no drawbacks.

## Operators

Sass provides developers with the ability to use operators. With basic arithmetic operators we are able to add, subtract, multiply, and divide inside of our Sass file.

    <span class="pink">h2</span> {
         width: <span class="orange">5px * 5 + 5px</span>; // 30px
         width: <span class="orange">6 * (5px + 5px)</span>; // 60px
         width: <span class="orange">7px + (6px / 2) * 3</span>; // 16px
     }

## Control Directives

Developers are also able to use Control Directives to create conditional statements making our Sass files even more dynamic. With Control Directives we can add, assign or remove CSS properties to elements dynamically.

<p data-height="268" data-theme-id="20621" data-slug-hash="LpXYXr" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/LpXYXr/'>Control Directives</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



## Functions

Functions are fairly similar to Mixins as they take arguments that output code but the are unique by allowing developers to removing reusable logic.

<p data-height="268" data-theme-id="20621" data-slug-hash="ojQNra" data-default-tab="css" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/ojQNra/'>Sassy Functions</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



## Import

Probably my favorite feature of Sass is the ability to import Sass files into each other. This is possible with CSS but it creates multiple HTTP Requests causing a slower overall load time of your web application. Sass solves this issue by enabling developers to combine as many sass files with only a single HTTP Request. This means we can create a maintainable code base. To do this Sass introduces Partials. Partials are Sass files with a leading underscore ex. _reset.scss. This tells Sass not to generate a stylesheet for the Partial. Instead we can now import the Partial into our main Sass file and that will generate a single stylesheet. This is what a file structure that incorporates Partials looks like.

    <span class="pink">index.html</span>
    css/
    css/<span class="pink">style.scss</span>
    css/<span class="pink">_reset.scss</span>
    css/<span class="pink">_variables.scss</span>
    css/<span class="pink">_main.scss</span>
    images/

And inside <i class="code-term">style.scss</i> we import all of our Partials.

    @import ‘reset’, ’variables’, ’main’;

With the introduction of Partials, we have seen an emphasis on Sass file structure. There are many different methodologies you can use to create an organized architecture with Sass but most methodologies incorporate folders within the main CSS folder. The name of the folders identifies what kind of Sass files are inside the folder.

    css/
    css/<span class="pink">style.scss</span>
    css/base/
    css/components/
    css/templates/

The base folder could have basic elements styles, mixins and variables. The components folder could have the styles for elements that comprise larger sections of the user interface like the header, footer, sidebar. The templates folder would have styles that combine the components styles to create complete user interfaces. Remember, there are many ways you can structure your Sass files. Your decision should be based on what works with your team of developers and your web app. Check my resource list on the bottom of this article to learn more about Sass file structure.

## Lastly&#8230;

Not all websites are meant to be full-blown web apps and CSS by itself can be used to create the same things you can with Sass. If your site is a relatively small project, it might not be useful to incorporate Sass. For myself I like to use Sass for all my projects whether big or small. This lets me create projects with an architecture that can scale with ease. 

## Sass Resources

  * <a href="http://sass-lang.com/" target="_blank">Sass Official Website</a>
  * <a href="http://thesassway.com/" target="_blank">The Sass Way</a>
  * <a href="https://web-design-weekly.com/2013/05/12/handy-sass-mixins/" target="_blank">Web Design Weekly | Handy Sass Mixins</a>
  * <a href="http://bradfrost.com/blog/post/atomic-web-design/" target="_blank">Brad Frost | Atomic Web Design</a>
  * <a href="https://smacss.com/" target="_blank">SMACSS | Scalable and Modular Architecture for CSS</a>