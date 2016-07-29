---
id: 556
title: Creating Modular Article Elements
date: 2016-02-03T09:04:59+00:00
author: Adrian Eufracio
description: 'Creating a modular code base is key to the extensibility of any web app.  Using the BEM inspired methodology it is a breeze to create modularized components. Today I will show you how to create a modular HTML and CSS component that is seen throughout the web. '
layout: post
guid: http://adrianeufracio.com/?p=556
permalink: /creating-modular-article-elements/
categories:
  - css
---
Creating a modular code base is key to the extensibility of any web app. A modular code base requires involvement from both the design team and the development team as the interface should be designed in a way that promotes modularity. Today I will show you how to create a modular HTML and CSS component that is seen throughout the web. 

## <i class="code-term">article</i> Element

<i class="code-term">article</i> is an HTML5 element that can be found all over the web. It represents an independent item section of content. It&#8217;s often used as an element to represent blog post teasers among other things. These blog teasers can come in many sizes and shapes. This is exactly where modular components shine.

## Going Modular

If the design team gives us three types of article layouts it is our job as Front End Developers to dissect the design and look for ways to create modular components. 

<img src="http://adrianeufracio.com/wp-content/uploads/2016/02/modular-mock.jpg" alt="A three article design mock" width="1000" height="600" class="alignnone size-full wp-image-557" srcset="http://adrianeufracio.com/wp-content/uploads/2016/02/modular-mock-300x180.jpg 300w, http://adrianeufracio.com/wp-content/uploads/2016/02/modular-mock-768x461.jpg 768w, http://adrianeufracio.com/wp-content/uploads/2016/02/modular-mock-460x276.jpg 460w, http://adrianeufracio.com/wp-content/uploads/2016/02/modular-mock-240x144.jpg 240w, http://adrianeufracio.com/wp-content/uploads/2016/02/modular-mock.jpg 1000w" sizes="(max-width: 1000px) 100vw, 1000px" />

As you can see these three article layouts share the same design elements. A title, a post date, an author byline and an article image. The best way to code these components is by creating a HTML and CSS architecture that can be reused. There are many CSS naming conventions which I described in my <a href="http://adrianeufracio.com/go-modular-with-your-css/" target="_blank">article regarding modular CSS</a>, but for this tutorial I will use a naming convention that resembles BEM.

## Lets start!

When you look at this design you can start seeing the individual elements as Lego pieces that are used to comprise the entire component. With this mentality, lets start coding out our component and learn as we go.

<p data-height="400" data-theme-id="20621" data-slug-hash="vLazxj" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/vLazxj/'>Modular Component</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



We have created our first component pretty easily using the article element. If another developer or designer looks at our HTML and CSS markup, they will be able to understand what they mean since it is written in a semantic manner. Our next task will be to create our second component using the same HTML structure while adding CSS classes when needed to help modify the look of the element.

<p data-height="400" data-theme-id="20621" data-slug-hash="obMaBm" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/obMaBm/'>Modular Component 2</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



As you can see, just by adding a one class to our existing element, <i class="code-term">.article-medium</i>, we can alter the appearance of our component to create the modified component. Lets do the same for our last component.

<p data-height="350" data-theme-id="20621" data-slug-hash="GoBYYo" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/GoBYYo/'>Modular Component 3</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



This component was just as easy to make. Using the BEM inspired methodology it is a breeze to create modularized components. To wrap this tutorial up, I will place all the elements together and use the section element to help with the layout.

<p data-height="500" data-theme-id="20621" data-slug-hash="mVjQwW" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/mVjQwW/'>Modular Component Complete</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



## Modular Resources

  * <a href="https://en.bem.info/" target="_blank">BEM</a>
  * <a href="http://www.lego.com/en-us/" target="_blank">LEGO</a>
  * <a href="https://smacss.com/" target="_blank">SMACSS</a>