---
id: 531
title: SVG Circle Line Animation
date: 2016-01-29T17:00:38+00:00
author: Adrian Eufracio
description: SVG is an incredibly useful web element that can take many forms and sizes. Whether you want to create a complex chart or a simple shape. SVG can also be animated! Today I will show you how to do exactly that by drawing a circle using a little CSS and some JavaScript to help us out.
layout: post
guid: http://adrianeufracio.com/?p=531
permalink: /svg-circle-line-animation/
categories:
  - css
---
SVG is an incredibly useful web element that can take many forms and sizes. Whether you want to create a complex chart or a simple shape. SVG can also be animated! Today I will show you how to do exactly that by drawing a circle using a little CSS and some JavaScript to help us out.

## Lets make a circle!

We will start off by creating an SVG element within our HTML document. The code below will create an SVG that is compatible with most modern browsers.

    <svg xml:space="<span class="orange">preserve</span>" xmlns="<span class="orange">http://www.w3.org/2000/svg</span>"></svg>

Next we will add the width and height attributes to our SVG that will help us define our circle.

    <svg viewBox="<span class="orange">0 0 220 220</span>" xml:space="<span class="orange">preserve</span>" xmlns="<span class="orange">http://www.w3.org/2000/svg</span>"
    width="<span class="orange">220</span>" height="<span class="orange">220</span>">
    </svg>

With the svg out of our way we can go ahead and create our circle element within the SVG.

    <circle></circle>

Lets start spicing up the circle with some additional attributes. We will add an <i class="code-term">id</i> name for styling purposes and for some JavaScript we will use later on. We will also add <i class="code-term">cx</i> and <i class="code-term">cy</i> values. These will set the coordinates of the circle within the SVG. To center the circle within the SVG I divided the width and height by 2 and placed the value within the <i class="code-term">cx</i> and <i class="code-term">cy</i> attributes, which in this case is <i class="code-term">110</i>. Finally, we will add a radius of <i class="code-term">100</i> using the <i class="code-term">r</i> attribute.

    <circle id="<span class="orange">path</span>" cx="<span class="orange">110</span>" cy="<span class="orange">110</span>" r="<span class="orange">100</span>"></circle>

Now we can start styling the circle. For our example, we need a <i class="code-term">stroke</i> and we will set a <i class="code-term">stroke-width</i> of 10 for the circle.

    <circle id="<span class="orange">path</span>" class="" cx="<span class="orange">110</span>" cy="<span class="orange">110</span>" r="<span class="orange">100</span>" stroke="<span class="orange">#000000</span>" fill="<span class="orange">none</span>" stroke-width="<span class="orange">10</span>"></circle>

## Draw it

We finally have our complete circle but now comes the tricky part. <a href="https://twitter.com/chriscoyier" target="_blank">Chris Coyier</a> has a great <a href="https://css-tricks.com/svg-line-animation-works/" target="_blank">article</a> on how line animation works so I suggest you go read that but for now I will give you a brief explanation. What we need is to animate the stroke on circle element. To do this we need to create a dash that is long enough to hide and reveal our stroke. To figure out the dash length we need to figure out the stroke length of our circle. This is where JavaScript will help us.

    // collect our radius value
    <span class="pink">var</span> radius = document.<span class="blue">getElementById</span>('<span class="orange">path</span>').<span class="blue">getAttribute</span>("<span class="orange">r</span>");
    // collect circle length value using basic math
    <span class="pink">var</span> circleLength = 2 * Math.PI * radius;
    // output length some where we can see it
    document.<span class="blue">getElementById</span>("<span class="orange">length-container</span>").innerHTML = circleLength;

Now we should have something like this

<p data-height="450" data-theme-id="20621" data-slug-hash="yeEJEB" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/yeEJEB/'>SVG DRAW CIRCLE step 1</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



Now we use css3 to create our animation. As I mentioned before we needed to create a dash that is long enough to hide and reveal our stroke. We can set the dash length equal to the circle length.

    <span class="pink">#path</span> {
      stroke-dasharray: <span class="orange">628.3185307179587</span>;
    }

This will hide our circle completely. To reveal it we need to animiate the position of our dash. We do this by creating a keyframe that changes the dash position from its original position of <i class="code-term">628.3185307179587</i> to <i class="code-term"></i>.

    <span class="pink">@keyframes dash</span> {
      <span class="pink">from</span> {
        stroke-dashoffset: <span class="orange">628.3185307179587</span>;
      }
      <span class="pink">to</span> {
        stroke-dashoffset: <span class="orange">0</span>;
      }
    }

Now to finish up we add this keyframe animation to our #path.

    <span class="pink">#path</span> {
      stroke-dasharray: <span class="orange">628.3185307179587</span>;
      animation: <span class="orange">dash 5s linear forwards</span>;
    }

## Our final product

<p data-height="450" data-theme-id="20621" data-slug-hash="LGrZBL" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/LGrZBL/'>SVG DRAW CIRCLE step 2</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



This is a cool little element you can use on a website and extend to your requirements. Here is the same element with some added functionality. 

<p data-height="600" data-theme-id="20621" data-slug-hash="zrjzqr" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/zrjzqr/'>SVG DRAW CIRCLE</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



## SVG Animation Resources

  * <a href="https://css-tricks.com/svg-line-animation-works/" target="_blank">How SVG Line Animation Works</a>
  * <a href="https://jakearchibald.com/2013/animated-line-drawing-svg/" target="_blank">Animated line drawing in SVG</a>
  * <a href="https://sarasoueidan.com/tags/svg/index.html" target="_blank">Sara Soueidan&#8217;s SVG Articles</a>