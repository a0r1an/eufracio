---
id: 605
title: Get Some SVG In Your Life
date: 2016-11-01T09:01:00+00:00
author: Adrian Eufracio
description: Are you tired of blurring images and the large file sizes that come with assets delivered in JPEG and PNG. Well if your asset is a vector asset you should use the latest and greatest of what the web has to offer, SVG!
layout: post
permalink: /get-some-svg-in-your-life/
categories:
  - html, svg, css
---

Scalable Vector Graphics, or SVGs, are two dimensional vector graphics that are created using the xml language. They were created specifically for the web and give web developers the ability to display vector graphics in an editable format.

Lets take a look at a circle created with an SVG.
{% highlight html %}
<svg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
  <circle cx="100" cy="100" r="100"/>
</svg>
{% endhighlight %}

Before we worry about the details of the attributes and values in the SVG element, I want to explain the theory behind the code above. We create an SVG element with a few attributes. Then we create a circle element within that SVG element. The circle element applies a couple attributes that define where to place the element and how large it should be.

But now let's take a look at a more complex SVG.
{% highlight html %}
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 300 300">
<path fill="#804D35" d="M35 254.6l9.7 28.8 211 1.7 12-34L35 255"/>
<path fill="#2F2B33" d="M40 288c1.3 1.2 221 0 221 0s5.3-6.4-50.2-10c-34.4.8-55.7 6-55.7 6s-25-6-47-6c-91 4-69 8.8-68 10z"/>
<path fill="#EE304E" d="M15.2 187.8s20.3-30 36.2-35.4c3.6 1.2 189 1.5 198.3 1.2 26.8 5.8 23.5 24 31.6 26.4 1.8-.3 11 79.6-19.8 77.6-1.3 2.5-50.6 4-55.7 4.5s-21.4 10-43 13c-4.6 1-78.7 0-78.7 0s-34-4-55-26c-1-2 0-9-13-60z"/>
<ellipse cx="151.3" cy="128.9" fill="#FFEDC3" rx="109.8" ry="76.8"/><path fill="#00B8C3" d="M43 114.6c0-49 58-81 107-82 82.7-2 106.5 68.2 105.3 67.6C133.3 44.7 43 114.6 43 114.6z"/>
<path fill="#FCEE21" d="M44.3 117.7c43.7-26 94-35.7 144.5-30.4 16 1.7 32 5 47.6 9.8 4.5 2 9 3 13.4 5l3.5 2c-1 0 .3 0 .6 1 4 2 8-4.2 3-6.2-22-10-46-14.6-69-17-51-6.5-103 4.5-148 31-4 2.3-1 9 4 6.3zm72.4-84.4s9-4.8 10.4-3.8 2-2.3 2-2.3l9-2h11l1-2.3s12-1 13 2c0 4 15.7 4 15 10-2.5 8-12 2-13 4-11.4 6-17 0-17 0l-13 4-1-7s-3 5-8 5.3c-17.3 4-9-8.5-9-8.5zm-100.5 155C6 189.3-7 221 24 227.3c10.4-2.6 40 2 36-13s-33.8-24.2-44-26zm267.4-7s5-1 8 4 4.7 22.2 4 27.6-.6 10-13.8 11-18.8-9-19.8-8-14.2 1-14.2 1-7.4-7 1.3-12c4-3 4-8 4-8s5-12 9-14 22-2 22-2z"/>
<path fill="none" stroke="#000" stroke-miterlimit="10" d="M68 167.3c11 12 91 71 170.3-5.6m-73 45.6c2 36.4-1.3 65.6-1.3 65.6"/><ellipse cx="157.1" cy="213.4" rx="1" ry="3"/>
<ellipse cx="159.7" cy="238.7" rx="1.2" ry="3.3"/>
<ellipse cx="157.2" cy="262.7" rx="2" ry="3.4"/>
<path fill="none" stroke="#000" stroke-miterlimit="10" d="M139 188.5c15.7 5.5 38 0 38 0"/>
<ellipse cx="182.5" cy="119.1" fill="#FFF" transform="matrix(.81 -.587 .587 .81 -35.153 129.678)" rx="26.7" ry="30.5"/>
<ellipse cx="126.5" cy="119.1" fill="#FFF" transform="matrix(.884 .467 -.467 .884 70.21 -45.287)" rx="26.7" ry="30.5"/>
<circle cx="138.6" cy="117.9" r="3.3"/>
<circle cx="170.6" cy="117.9" r="3.3"/>
<path d="M134.7 172.4c3.4-3.5 7.7-3.2 7.7-3.2s24.2-.2 25.5.3 2 3 2 4.2c-1 1.4-5 10.7-7 13.3-2 1.8-9 0-9 0s-4-1-5-1.8c-.7-.3-3.4 0-4-.2s-11.5-10.6-12-12.3"/>
<path fill="#FFF" d="M149 172.3c-.2-1-1-1.7-1.8-1.5l-3 .5c-.8 0-1.3 1-1.2 2 .2 1 1 1.7 1.8 1.5l3-.5c1 0 1.4-1 1.2-2zm9 1.5c.2-.8-.3-1.6-1-1.8l-4.2-.8c-.7 0-1.5.4-1.6 1.2v.3c-.3.8.2 1.6 1 1.8l4 .8c.8 0 1.6-.4 1.7-1.2zm9-.4c0-1-.8-1.7-1.6-1.6l-5 .4c-.8 0-1.4 1-1.3 1.8 1 1 1 1.7 2 1.6l5-.4c1 0 2-1 2-1.8z"/>
</svg>
{% endhighlight %}

This code will create an SVG that is familiar to a lot of you, Cartman. Wowzers. This code might look complex and intimidating and that’s because it is! But let's dig into the code a bit. So just like the SVG before, we set an SVG element with a couple attributes. Within that SVG element we have a bunch of other elements. Each one of those elements creates a shape that make up Cartman. The intimidating part are the numbers that are attached to each element. The numbers are creating paths on an invisible plain. **????** Follow me for a second please. Like I said before SVGs are created using the xml language. The SVG uses a coordinate system to define where paths are created within the given SVG. Elements within SVGs like path and circle use the coordinate system to define their shape. 

Knowing this, we will take a look at one of the more complicated looking paths in the cartman SVG.
{% highlight html %}
<path fill="#EE304E" d="M15.2 187.8s20.3-30 36.2-35.4c3.6 1.2 189 1.5 198.3 1.2 26.8 5.8 23.5 24 31.6 26.4 1.8-.3 11 79.6-19.8 77.6-1.3 2.5-50.6 4-55.7 4.5s-21.4 10-43 13c-4.6 1-78.7 0-78.7 0s-34-4-55-26c-1-2 0-9-13-60z"/>
{% endhighlight %}

The d attribute within the path defines the shape that is about to be created. We also see a more familiar attribute called fill with a hex code value. This value will fill the shape with the color that the hex code produces.

## OK, but ...
That explains the way SVGs work but it doesn't necessarily make creating a cartman that much easier. If would be extremely difficult to create paths using the d attribute. Fortunately for us there is a much easier way. There are programs that let you create vector elements and export those vectors into a SVG. The exported SVG can then be popped into your html document and bam you got your very first cute SVG!

## Exporting an SVG
When creating an SVG in illustrator, we should make sure to pick the correct settings when exporting the svg. These our the settings that you want to go with.

<img src="../img/posts/getSvg/svgSettings.png"  width="250" />

When exporting SVGs from illustrator and most other svg makers you get code bloat that is safe to remove. I like to use Jake Archibald’s SVG optimizer. It strips out the code bloat and gives you an optimized version of the SVG.
https://jakearchibald.github.io/svgomg/

## Cool Feature Bro - Scalable
One of the best features of SVG is it’s scalability. To appreciate this feature we must know why its so important. The issue with assets like jpegs, gifs, and pngs are that they don't scale. If the asset is 300px by 300px then the asset cannot scale to a larger size without losing resolution aka looking shitty. Even if you downscale the image to 100px by 100px using CSS you will still lose quality. SVGs solve this problem. An SVG can be 100px by 100px or 100000px by 100000px and retain its quality. Plus the file size doesnt change so you can use the same 250 byte svg whether it be 100px or 100000px.

## Cool Feature 2 Bro - CSS Editable
Another awesome feature of SVGs are that they are editable with CSS. You can use CSS to change colors and the size of SVGs. This is an incredible useful feature as it removes the need to have multiple versions of assets in different sizes and colors. Or the need to use an vector program to make minor tweaks.

With the ability to edit SVGs using CSS it gives us the ability to create awesome animations. Want to morph a circle into a square? You can do that! Want to make a spinning loader? You can do that! Want to morph Trump’s face to Hillary Clinton’s Face. You can do that! Actually not sure if you can do that but that doesn't seem out of the question. We can animate SVGs using CSS3 animation properties like keyframes and animate.

### Animate Time
We will start with a SVG I created. Just a real cute looking circle with multiple faces SVG. 

<p data-height="300" data-theme-id="20621" data-slug-hash="KgbWWG" data-default-tab="css,result" data-user="adrianeufracio" data-embed-version="2" data-pen-title="KgbWWG" class="codepen">See the Pen <a href="http://codepen.io/adrianeufracio/pen/KgbWWG/">KgbWWG</a> by Adrian Eufracio (<a href="http://codepen.io/adrianeufracio">@adrianeufracio</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>


Lets make this cutier and make the smiling half-circle fill in with its intended fill color.
<p data-height="300" data-theme-id="20621" data-slug-hash="bBbbBE" data-default-tab="html,result" data-user="adrianeufracio" data-embed-version="2" data-pen-title="Still Super Duper Simple SVG Animation" class="codepen">See the Pen <a href="http://codepen.io/adrianeufracio/pen/bBbbBE/">Still Super Duper Simple SVG Animation</a> by Adrian Eufracio (<a href="http://codepen.io/adrianeufracio">@adrianeufracio</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
#### Boom
Super simple example of animating an SVG, the same way you would animate any other html element. 

## Keep it responsive
Certain attributes need to be set on SVG elements for them to be responsive and scale appropriately. The <i class="code-term">viewbox</i> and <i class="code-term">preserveAspectRatio</i> are your Batman and Robin when it comes to creating responsive SVGs. 

<img src="http://i.giphy.com/KClrIEFayJMiI.gif" />

Remember how I said, SVGs use their own coordinate system to define where shapes are created and positioned. Well the viewbox is what defines that coordinate system. The viewbox takes four values: min-x, min-y, width, and height. The min-x and min-y values define where to start drawing on the coordinate system. The width and height define the amount of space available to us in the coordinate system. A simple and ideal responsive SVG would have the viewport values of <i class="code-term">0 0 100 100</i>. 


The preserveAspectRatio defines how to enforce the aspect ratio. By leaving this attribute empty the value defaults to <i class="code-term">xMidyMid</i> which centers the SVG within the viewport of the SVG, no matter the size the SVG has.

If you want to scale the SVG to the size of its container than we will need to use the image tag and set the src to the SVG file. The SVG should have the viewport set and the img element will resize the SVG to the containing element.

{% highlight html %}
<img src=”circle.svg” />
{% endhighlight %}


## Make it Accessible
Just how the img element has an alt attribute, SVGs can have elements within it that make them accessible for disabled web users.
Title and Description elements can more accurately describe your SVG while the aria attributes of <i class="code-term">aria-labelledby="title" aria-describedby="desc"</i>, maximize screen reader support.
{% highlight html %}
<svg version="1.1" width="300" height="200" aria-labelledby="title desc" role="img">
  <title id="title">Circle</title>
  <desc id="desc">A simple circle to show an SVG examlple.</desc>
  <circle cx="100" cy="100" r="100"/>
</svg>
{% endhighlight %}

There is really a lot that you can do with SVGs and a lot to learn when implementing SVGs depending on your particular implementation. I plan on doing more tutorials on SVGs but I also highly recommend the following blog posts that go more into detail regarding SVGs.

### Recommended Articles
* <a href="https://www.smashingmagazine.com/2014/11/styling-and-animating-svgs-with-css/" target="_blank">Styling and Animating SVGs</a>
* <a href="https://abookapart.com/products/practical-svg" target="_blank">Practical SVG</a>
* <a href="https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox" target="_blank">Viewbox explained</a>
* <a href="https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/preserveAspectRatio" target="_blank">PreserveAspectRatio explained</a>