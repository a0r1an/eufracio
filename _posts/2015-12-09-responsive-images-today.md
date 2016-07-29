---
id: 394
title: Responsive Images Today
date: 2015-12-09T20:59:01+00:00
author: Adrian Eufracio
description: 'Responsive images on web apps is a complicated subject that if done right can positively effect your sites aesthetics and performance.  srcset, sizes, and picture element gets us one step closer to a solution for responsive images.'
layout: post
guid: http://adrianeufracio.com/?p=394
permalink: /responsive-images-today/
categories:
  - html
---
Is your idea of responsive images <i class="code-term">max-width: 100%</i>? That&#8217;s all it takes for your images to look somewhat decent on all devices but there is much much more to responsive images. Responsive images on web apps is a complicated subject that if done right can positively effect your sites aesthetics and performance.

## The Problem

While max-width:100% is an effective way to make images resize according to the images container, it does not fix some of the problems developers have encountered since the advent of smartphones and high resolution devices. When we insert an image that is a resolution of 1000px X 500px like so 

    <img src="<span class="orange">raptor.jpg</span>" width="<span class="orange">1000</span>" height="<span class="orange">500</span>" />

We have to take into account that we are also serving this image to devices that have a viewport smaller than 1000px. iPhones, Android phones, tablets all come in sizes less than 1000px. Why serve a 1000px image when certain devices only need a 320px image? What if you want to accommodate users with high resolution displays? Ever since the introduction of Retina Display by Apple, high resolution displays have become an industry standard. The need for high resolution images has given web developers another riddle to solve.

## Solution&#8230; Put a srcset on it

HTML5.1 introduces <i class="code-term">srcset</i> into the our web standards. <i class="code-term">srcset</i> is an attribute applied on the img tag that takes a comma separated list of images with a description of the image. The description can be either a pixel ratio descriptor or a width descriptor. Using the pixel ratio descriptor, we can tell the browser what image to display depending on the pixel ratio of the current device. 

    <img src="<span class="orange">dino.jpg</span>" alt="<span class="orange">dino</span>" srcset=“<span class="orange">dino.jpg, dino-hr.jpg 2x</span>">

<i class="code-term">srcset</i> contains strings seperated by commas. Strings are comprised of two values; one being the url of the image and the other being the pixel ratio this image should be displayed at. In this img tag, <i class="code-term">dino.jpg</i> and <i class="code-term">dino-hr.jpg</i> are image locations and 2x signifies the image is meant for devices with a twice the amount of pixels.
  
The browser sees the img tag, determines the pixel ratio of the viewport and then determines which image to use. If the user is on a high resolution device, the browser will serve the 2x image, <i class="code-term">dino-hr.jpg</i>.
  
This is a straight-forward syntax that offers instant functionality however it does not take into account changing widths of the viewport. Therefore this syntax should only be used for fixed width images.

## Images Come In Different Width And Sizes

A better solution for truly responsive images is a combination of the **width descriptor** and the **sizes** attribute. The width descriptor like the pixel descriptor is applied to the end of a string in the srcset attribute. Its value is the actual width of the image. For example, I have an image large.jpg which is 1024 x 500 pixels so we apply the width descriptor of 1024w. The w always follows the width of the image.

    large.jpg 1024w

So now we can pass srcset something like this that includes smaller versions of our original large.jpg

    srcset=“<span class="orange">large.jpg 1024w, medium.jpg 640w, small.jpg 320w</span>"

Now that we offer the browser a set of images it can choose from, we can now provide even more information that will help the browser select the best possible option. This is possible using the **sizes** attribute. **sizes** takes a set of strings separated by commas. Each string contains a <i class="code-term">media condition</i> and a <i class="code-term">length</i> value. The <i class="code-term">media condition</i> is the same syntax that is used in a media query.

    (min-width: 800px)

The <i class="code-term">length</i> value is the size the image in regards to the viewport. Since the size is in relation to the viewport, it&#8217;s best to apply a length value using the <i class="code-term">vw</i> viewport unit. <i class="code-term">vw</i> is the viewport width where <i class="code-term">1vw</i> is equal to one percent of the viewport and <i class="code-term">33vw</i> is equal to 33 percent of the viewport. Thus a string can look like this&#8230;

    (max-width:800px) 33vw

This string says at 800px and below, the image take up 33% of the viewport width. Our sizes attribute will look like&#8230;

    sizes=“<span class="orange">(max-width:320px) 100vw, (max-width:800px) 33vw, 279px</span>"

The final string omits the media condition and gives a default length of an image. Now pulling all our code together to create the final img element.

    <img srcset="<span class="orange">large.jpg 1024w, medium.jpg 640w, small.jpg 320w</span>"
         sizes="<span class="orange">(min-width: 320em) 100vw,(max-width:800px) 33vw, 279px</span>"
         src="<span class="orange">small.jpg</span>"
    >

Now the browser has three image choices with a defined width to each. It also has the size of the image at different viewport widths. Using this information the browser will pick an image that best suits the user depending on the pixel density, zoom level and also the network connection of the user.

## srcset Browser Support

<i class="code-term">srcset</i> is part of the HTML 5.1 working draft which means it will soon be a standardized part of HTML 5. There is wide support for <i class="code-term">srcset</i> among newer browsers but it lacks support in all versions of IE. Therefore all img elements are recommended to have the <i class="code-term">src</i> attribute as a fallback. For more information regarding browser support visit <a href="http://caniuse.com/#search=srcset" target="_blank">caniuse.com</a>.

## picture element

Using the <i class="code-term">srcset</i> and <i class="code-term">sizes</i> attributes give the browser the option on the best image for the user. But what if you want to provide a specific image for the user at a certain breakpoint? This is called the art direction conundrum. Thankfully there is an element that lets developers do exactly this, the <i class="code-term">picture</i> element. The <i class="code-term">picture</i> element is a container for the <i class="code-term">source</i> element and an <i class="code-term">img</i> element.

    <picture>
    <source>
    <img>
    </picture>

The <i class="code-term">source</i> element has two attributes; <i class="code-term">media</i> and <i class="code-term">srcset</i>. The <i class="code-term">media</i> attribute takes a media condition

    <source media="<span class="orange">(min-width: 45em)</span>" >

The srcset attribute is just like the srcset attribute for the img element.

    //these are all valid values for srcset in the picture element.
    <source media="<span class="orange">(min-width: 45em)</span>" srcset="<span class="orange">large.jpg</span>" >
    <source  media="<span class="orange">(min-width: 32em)</span>" srcset="<span class="orange">med.jpg</span>" >

Finally, we can provide a fallback img element.

    <img src="small.jpg" alt="A small image.">

All in all, are picture element will look like this

    <picture>
      <source media="<span class="orange">(min-width: 45em)</span>" srcset="<span class="orange">large.jpg</span>">
      <source media="<span class="orange">(min-width: 32em)</span>" srcset="<span class="orange">med.jpg</span>">
      <img src="<span class="orange">small.jpg</span>" alt="<span class="orange">A small image</span>">
    </picture>

## picture Browser Support

The picture element is also part of the HTML 5.1 working draft and the browsers that don’t except the picture will fallback nicely to the img element.

## Implement And Test

<i class="code-term">srcset</i>, <i class="code-term">sizes</i>, and <i class="code-term">pictur</i>e element gets us one step closer to a solution for responsive images. Try implementing this in your next project and test what works. You have to consider what images should use the <i class="code-term">img</i> element rather than the <i class="code-term">picture</i> element. Also make note of your web apps breakpoints and the variety of images you need to create to accommodate those breakpoints. As I said before, responsive images are not an easy task but implementing and testing will get you on the right track. 

## Responsive Image Resources

  * <a href="http://responsiveimages.org/" target="_blank">Responsiveimages.org</a>
  * <a href="http://alistapart.com/article/using-responsive-images-now" target="_blank">A List Apart&#8217;s Using Responsive Images Now</a>
  * <a href="http://blog.cloudfour.com/responsive-images-101-part-4-srcset-width-descriptors/" target="_blank">Cloudfour&#8217;s Responsive Image 101</a>
  * <a href="http://www.w3.org/html/wg/drafts/html/master/semantics.html#the-picture-element" target="_blank">W3C HTML 5.1 Working Draft</a>