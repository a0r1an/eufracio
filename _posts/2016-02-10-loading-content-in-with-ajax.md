---
id: 568
title: Loading Content In With Ajax
date: 2016-02-10T09:00:57+00:00
author: Adrian Eufracio
description: When a page initially loads, many requests are made to the browser. Content, Images, and JavaScript Files are just some of the types of requests made to the browser. For websites that require lots of content and images, it is best to delay the requests for these assets until they need to be displayed. Ajax gives developers the tools to do just that.
layout: post
guid: http://adrianeufracio.com/?p=568
permalink: /loading-content-in-with-ajax/
categories:
  - javascript
---
When a page initially loads, many requests are made to the browser. Content, Images, and JavaScript Files are just some of the types of requests made to the browser. Of course, the more assets we request from the server, the slower our website will be. For websites that require lots of content and images, it is best to delay the requests for these assets until they need to be displayed. Asynchronous JavaScript and XML gives developers the tools to do just that. Asynchronous JavaScript and XML thankfully has a shorter name it goes by called Ajax. It enables developers with the ability to update parts of a web page asynchronously without having to reload the page. This feature has many use cases that can be implemented on a website that craves speed.

## Load on Hover

Online publications like <a href="http://mashable.com/" target="_blank">Mashable</a> have a tremendous amount of content that needs to be pulled from their servers and displayed to their users. As part of their navigation, there dropdown menu contains article images and titles for each category. The dropdown is not seen until you hover over any of the links in the navigation, making it unnecessary for them to load the content until the user hovers on a link. This makes it a perfect use case for Ajax. I will recreate a similar scenario with my own page.

<p data-height="500" data-theme-id="20621" data-slug-hash="GowOMJ" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/GowOMJ/'>AJAX HOVER PART 1</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



Here we have a webpage with an element with a class of <i class="code-term">.menu</i>. When hovering over <i class="code-term">.menu</i>, the <i class="code-term">.menu-submenu</i> element will appear. There isn&#8217;t any content inside <i class="code-term">.menu-submenu</i> but we will load the content in using Ajax. 

<p data-height="500" data-theme-id="20621" data-slug-hash="adQVLR" data-default-tab="js" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/adQVLR/'>AJAX HOVER PART 2</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



Using jQuery and the Ajax function, we retrieve the content within <i class="code-term">content.html</i> and insert it in the <i class="code-term">.menu-submenu</i>. This creates a faster initial load with virtually the same web experience.

## Load On Click

Another common predicament that large blogs have is displaying multiple blog post teasers. Displaying many blog post on a page will increase the load time of a website. Easily fixable with Ajax! Instead of loading all your content on the initial load, lets load it when clicking a button. 

<p data-height="500" data-theme-id="20621" data-slug-hash="gPQXjr" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/gPQXjr/'>AJAX CLICK PART 1</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



We start with a simple webpage with a button at the bottom of it. Now lets add our JavaScript that will load content in when the button with an <i class="code-term">ID</i> of <i class="code-term">#load-more</i> is clicked.

    
    <span class="pink">$</span>("<span class="orange">#load-more</span>").click(<span class="blue">function</span>(){
    	<span class="pink">$</span>.ajax({
    		url: "<span class="orange">content.html</span>",
    		cache: <span class="green">false</span>
    	})
      	.done(<span class="blue">function</span>( html ) {
        	$( "<span class="orange">.content</span>" ).append( html );
        	$("<span class="orange">#load-more</span>").css("<span class="orange">display</span>","<span class="orange">none</span>");
      	});
    });
    

This was just as easy as the hover example but lets make it easier for the users so they don&#8217;t have to click on anything to load the rest of the content. All they have to do is reach the bottom of the page. 

<p data-height="500" data-theme-id="20621" data-slug-hash="pgQdZp" data-default-tab="result" data-user="adrianeufracio" class='codepen'>
  See the Pen <a href='http://codepen.io/adrianeufracio/pen/pgQdZp/'>AJAX SCROLL</a> by Adrian Eufracio (<a href='http://codepen.io/adrianeufracio'>@adrianeufracio</a>) on <a href='http://codepen.io'>CodePen</a>.
</p>



Using the scroll function, we check whenever the user scrolls if they have reached a point where they have scrolled the height of the web page. Once they have reach the bottom, we load the content into the page.

## Conclusion

As you can see these are basic examples, but when dealing with large websites these simple Ajax requests can help create a faster web experience. Faster is better. It is important to note that Ajax is dependent on JavaScript so make sure to create a fallback to alternatively load content when there is no JavaScript available.

## Ajax Resources

  * <a href="http://api.jquery.com/jquery.ajax/" target="_blank">jQuery.ajax()</a>
  * <a href="https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started" target="_blank">AJAX | MDN</a>
  * <a href="http://www.sitepoint.com/use-jquerys-ajax-function/" target="_blank">How to Use jQuery’s $.ajax() Function</a>