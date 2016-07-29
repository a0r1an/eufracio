---
id: 350
title: Go Modular With Your CSS
date: 2015-11-25T09:00:58+00:00
author: Adrian Eufracio
description: CSS can be pretty frustrating when your codebase starts to increase. Without the proper structure and naming conventions, your CSS can be downright unmanageable. Lets delve into the steps we can take to control our CSS codebase.
layout: post
guid: http://adrianeufracio.com/?p=350
permalink: /go-modular-with-your-css/
categories:
  - css
---
CSS has always had a special place in my heart. It is an easy, yet powerful tool, that web makers use everyday. With the introduction of CSS preprocessors like Sass, CSS has become much more robust and scalable. That is exactly what developers need in 2015. We developers find ourselves working less on websites and more on webapps. This adds a level of complexity meaning more code, more team members, and more problems to solve. This is where things start to get tricky with CSS. CSS can be pretty frustrating when your codebase starts to increase. Without the proper structure and naming conventions, your CSS can be downright unmanageable. There are many debates and arguments over what is the proper way to name classes and store CSS and I welcome these discussions because it brings to light the importance of wrangling CSS. Lets delve into the steps we can take to control our CSS codebase.

## SASS

Sass gives CSS added functionality that makes CSS more robust. One of the most important features is the ability to create partials. Partials are Sass stylesheets that are included into another Sass stylesheet. With partials we can separate css snippets into their own Sass file, giving developers a better way to modularize CSS. You can have a partial like <i class="code-term">_button.css</i> just for buttons styles or a <i class="code-term">_reset.scss</i> partial for reset styles. Separating CSS snippets into separate files makes CSS more manageable and organized. Check out <a href="http://adrianeufracio.com/starting-with-sass/" target="_blank">my article on Sass</a> that goes more in-depth.

## More Structure you want?

Partials are just the start of structuring CSS. For large websites, CSS needs to have a more refined and thought out structure. One such structure is <a href="http://bradfrost.com/blog/post/atomic-web-design/" target="_blank">Atomic Design</a>. Created by <a href="https://twitter.com/brad_frost" target="_blank">Brad Frost</a>, Atomic Design is a methodology for creating design systems. Atomic Design pushes the idea of constructing your css in a methodical manner. This is done by creating 5 different layers in a projects CSS structure; Atoms, Molecules, Organisms, Templates, and Pages. Each layer consists of a folder that contains partials that are considered part of that layer. Atoms contain elements that are common and found throughout the site like headline tags and buttons.

    -atoms/
    -atoms/<span class="pink">_headline.scss</span>
    -atoms/<span class="pink">_buttons.scss</span>

**Molecules** contain elements that are comprised of multiple atoms like a search component comprised of two inputs.

    -molecules/
    -molecules/<span class="pink">_search-form.scss</span>

**Organisms** contains elements like the sites header and footer.

    -organism/
    -organism/<span class="pink">_header.scss</span>
    -organism/<span class="pink">_footer.scss</span>

**Templates** are the accumulation of organisms, molecules and atoms that make up a template. They are reused on multiple layouts.

    -templates/
    -templates/<span class="pink">_article.scss</span>
    -templates/<span class="pink">_front-page.scss</span>

**Pages** are one-off designs like a contact page and an about us page.

    -pages/
    -pages/<span class="pink">_about.scss</span>
    -pages/<span class="pink">_contact.scss</span>

There is also <a href="http://csswizardry.net/talks/2014/11/itcss-dafed.pdf" target="_blank">ITCSS</a> which is similar to Atomic Design. They both have there own particular guidelines with the prevailing theme being to keep your CSS as modular as possible. Modular code is basically reusable code and having code that is reusable makes it much easier to maintain and scale a website at a high level. Your UI is made of a bunch of tiny modules; header tags, anchor links, input fields. These small modules make up bigger modules; headers, footers, forms and those bigger modules make up your UI as a whole. Being able to define and identify these modules is key to maintaining structure and clarity of your codebase.

One of the harder aspects in software development is naming. CSS selectors, particularly class and id names, are excellent examples of this problem. The same thing that makes CSS easy to use can also hinder it from being an expressive language. Class names can be named practically anything which in turn produces CSS that is less than optimal. Your class name of <i class="code-term">.upper</i> might make sense to you but if another developer hopes into the code, they won’t have any idea what this class can do. Classes should be descriptive enough so that any developer on your team can identify what part of the UI it controls. This is critical if you are working on a large website with multiple team members. There are many ways you can go about implementing a naming convention but there are a couple popular naming conventions that can steer you in the right direction. The naming convention I prefer is <a href="https://en.bem.info/method/" target="_blank">BEM</a>. BEM is an methodology, created by <a href="https://www.yandex.com/" target="_blank">Yandex</a>, that is meant to speed up the development process and ease developer teamwork. Its name is an acronym for Block, Element and Modifier. When applied to CSS this naming system provides a clear naming convention that will provide clarity to your CSS and HTML markup.

**Blocks** are defined as a container for elements. So an unordered list can be considered a block. The ul block&#8217;s class will be <i class="code-term">.menu</i>. 

An **Element** would be anything within a block, so the list items within the <i class="code-term">ul</i> are considered elements and their class would be <i class="code-term">.menu__item</i>. The two underscores signify it is an <i class="code-term">item</i> element of the <i class="code-term">.menu</i> block. 

**Modifiers** are blocks or elements that change its appearance from its original state. If we have another <i class="code-term">ul</i> that looks similar to our <i class="code-term">ul.menu</i> but it differs in some css attributes, than we can modify it by adding a modifier class of <i class="code-term">.menu&#8211;big</i>. The two hyphens signify that the class is a modifier while the name <i class="code-term">big</i> gives an indication of the difference between the original block.

    <span class="pink">.menu</span> {
    ...
    }
    <span class="pink">.menu--big</span> {
    ...
    }
    <span class="pink">.menu__item</span> {
    ...
    }

## Conclusion

Like I said before, naming conventions and other css methodologies do not bide by any strict rules. That being said you should set strict rules within your project/team once you have a methodology chosen. A great way of setting these rules and guidelines is by documenting them. There are many ways you can go about doing this. Site like <a href="http://primercss.io/" target="_blank">Github</a>, <a href="https://www.google.com/design/spec/material-design/introduction.html" target="_blank">Google</a>, and <a href="http://www.yelp.com/styleguide" target="_blank">Yelp</a> create living style guides which are tremendous resources for its team members. Even a simple <i class="code-term">README.md</i> containing your naming methodology and how to implement it across the site will help your team in the long run. Every project and team is different so choose the convention that makes the most sense for each circumstance. Your project will increase in web awesomeness by implementing any of these solutions. Please look at the resources below to learn more about modular CSS.

## Modular CSS Resources

  * <a href="http://adrianeufracio.com/starting-with-sass/" target="_blank">My Sass Article</a>
  * <a href="http://bradfrost.com/blog/post/atomic-web-design/" target="_blank">Brad Frost&#8217;s Atomic Design</a>
  * <a href="http://csswizardry.net/talks/2014/11/itcss-dafed.pdf" target="_blank">Harry Roberts&#8217; ITCSS</a>
  * <a href="https://en.bem.info/method/" target="_blank">Yandex&#8217;s BEM Methodology</a>