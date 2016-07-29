---
id: 451
title: The Right Way To Load Web Fonts
date: 2015-12-23T09:00:39+00:00
author: Adrian Eufracio
description: 'Depending on how large the file size of your web font, you will find that your website will take a performance hit. Web fonts are a great asset for designers and developers alike that come with their own quirks and caveats. Our goal as developers is to minimize these quirks and we can do just that with Web Font Loader. '
layout: post
guid: http://adrianeufracio.com/?p=451
permalink: /the-right-way-to-load-web-fonts/
categories:
  - javascript
---
Fonts are a crucial design element for any website. In the beginning of the web, if we wanted a certain font family or font style that was not available, we were forced to use an image of a font. More images meant more server requests causing a slower web experience. The web has grown and with that has come the ability to use fonts that were previously unattainable via resources such as Google Fonts and Typekit as well as the <i class="code-term">@font-face</i> css rule. This has allowed designers and developers to incorporate fonts that were previously unattainable on websites, creating an experience that relied less on images which in turn helps with the load time.

## Web Fonts Are A Resource Too

Loading a web font is a gazillion times better than loading images of fonts but in the never ending world of web page optimization we are constantly looking for ways to make the web experience even faster. Ultimately, web fonts are loaded from a CSS file which is another resource. Depending on how large the file size of your web font, you will find that your website will take a performance hit. Let me take a step back, back in college, in HTML 101 class, we learned to load our CSS in the head of our web page. This is all peaches and cream until your CSS file size is getting increasingly large. This caused Google to recommend &#8216;eliminating render blocking CSS’ to speed up load time. CSS, by design, has to be completely parsed before the browser can render the html and load additional resources. This prevents the user from seeing any un-styled elements. So the question now is how can we load our web font without block the rendering of the rest of the web page.

## Going Async!

Async is usually a term we hear with JavaScript but fret not as the geniuses at Google and Typekit have given us the ability to load our web fonts async as well. Web Font Loader is a 12kb JavaScript file that gives developers more control over the fonts they load with the ability to load asynchronously. Lets start by creating our async solution.

    WebFontConfig = {
              typekit: { <span class="green">id</span>: '<span class="orange">xxxxxx</span>’ },
              google: {
                   <span class="green">families</span>: [‘<span class="orange">Droid Sans</span>’]
              },
              custom: {
                   <span class="green">families</span>: [‘<span class="orange">My Font</span>'],
                   <span class="green">url</span>: [‘<span class="orange">/fonts.css</span>’];
              } 
         };
    
       (function(d) {
          <span class="pink">var</span> wf = d.createElement('<span class="orange">script</span>'), s = d.scripts[0];
          wf.src = '<span class="orange">https://ajax.googleapis.com/ajax/libs/webfont/1.5.18/webfont.js</span>';
          s.parentNode.insertBefore(wf, s);
       })(document);

Adding this code to the head of our web page will load the web font without blocking the rendering of the web page whether the font is a Typekit font, Google font or our own web font. Seems simple enough until we see our page load.

## FOUT

When are page loads we witness something strange, a Flash Of Un-styled Text or what developers call FOUT. FOUT is caused by the asynchronous load of our web fonts. Since the fonts are rendered async with the rest of the page we are creating a situation where the browser searches and uses a fallback font since the web font is not loaded. Once loaded, the web font replaces the default font, or un-styled text, to achieve the intended font style.

## Fight Against FOUT

Web Font Loader combats FOUT by applying classes while your webpage is loading the web fonts. These classes are applied to the html element of your webpage.

    <span class="pink">.wf-loading</span> // when fonts are requested, this class will be applied
    <span class="pink">.wf-active</span> // when fonts have been rendered, this class will be applied
    <span class="pink">.wf-inactive</span> // when fonts fail to render, this class will be applied

If our <i class="code-term">html</i> element has a class of <i class="code-term">.wf-loading</i>, we can apply styles that will minimize the FOUT. For example, if we are using the Google font Playfair Display, we would use use the <i class="code-term">.wf-loading</i> class to apply a fallback font that looks similar to Playfair Display. Then once the <i class="code-term">.wf-loading</i> class is replaced with <i class="code-term">.wf-active</i> class, we would see our intended styles roll through.

    <span class="pink">.wf-loading</span> {
         font-family: <span class="orange">georgia</span>;
    }
    <span class="pink">.wf-active</span> {
         font-family: <span class="orange">'playfair display'</span>;
    }
    <span class="pink">.wf-loading h1</span> {
         font-size: <span class="orange">20px</span>;
    }
    <span class="pink">.wf-active h1</span> {
         font-size: <span class="orange">24px</span>;
    }

We can utilize <i class="code-term">.wf-inactive</i> class to apply a more reliable fallback experience

    <span class="pink">.wf-inactive</span> {
         font-family: <span class="orange">georgia</span>;
    }

For web pages that are requesting multiple font families, there are classes that specifically state the current status of a font family.

    <span class="pink">.wf-<familyname>-<fvd>-loading</span> // when this font is requested, this class will be applied
    <span class="pink">.wf-<familyname>-<fvd>-active</span> // when this font has been rendered, this class will be applied
    <span class="pink">.wf-<familyname>-<fvd>-inactive</span> // when this font fails to render, this class will be applied

<i class="code-term"><familyname></i> would be the font family and <i class="code-term"><fvd></i> would be the font style and font weight of the given font. 

When using Web Font Loader, it is imperative to collaborate with your designer to find a well supported fallback font that looks as close to the web font as possible. It is important to do this as it prevents the user from seeing the jarring web experience that FOUT causes. Web fonts are a great asset for designers and developers alike that come with their own quirks and caveats. Our goal as developers is to minimize these quirks and we can do just that with Web Font Loader. 

## Web Font Resources

  * <a href="https://github.com/typekit/webfontloader" target="_blank">Web Font Loader</a>
  * <a href="https://www.google.com/fonts" target="_blank">Google Fonts</a>
  * <a href="https://typekit.com/" target="_blank">TypeKit</a>