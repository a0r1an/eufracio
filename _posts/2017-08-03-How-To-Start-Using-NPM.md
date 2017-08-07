---
id: 605
title: How To Start Using NPM
date: 2017-08-03T15:01:00+00:00
author: Adrian Eufracio
description: Npm is a node package manager. Lets dissect these words first. Node.js is a javascript runtime for executing javascript code. Package manager is a resource that helps to distribute packages of code as easily as possible. NPM is the industry leader in package managing for javascript.
layout: post
permalink: /How-To-Start-Using-NPM/
categories:
  - React, JavaScript, Node, Web Development, NPM
---


Npm is a node package manager. Lets dissect these words first. Node.js is a javascript runtime for executing javascript code. Package manager is a resource that helps to distribute packages of code as easily as possible. NPM is the industry leader in package managing for javascript. To understand NPM lets use a grocery store as an example.

A grocery store sells a bunch of different types of items. Vegetables, Fruits, Meat, Cookies, Milk, Eggs, Sugar, Chocolate. They get these items from different companies around the world and make them accessible to those who visit the store.

Npm does the same thing but with javascript libraries. They have tons of libraries like React, Jquery, Angular, D3, andGulp to name a few. They get these libraries from other developers all around the world. And make them publicly accessible to those who use NPM.
They way you can start using NPM is by installing node.

{% highlight html %}
brew install node
{% endhighlight %}

Installing Node.js also installs NPM just double check by running

{% highlight html %}
npm -v
{% endhighlight %}

So back to the grocery store example. Lets say you buy some groceries. You buy Salmon, Pepper, Syrup and Pecans. You can be a savage and eat these items individually but chances are that if you combine all of these items you will get a dish that tastes much better.

The same thing goes with JavaScript libraries. You can use individual libraries to make your next web project but chances are that if you use multiple libraries in the right combination then your web app will perform better.

Groceries lists are a way to keep track of the things you need to get at the grocery store. NPM has something similar to a grocery list and its called package.json. package.json contains a list of javascript libraries you need for the project you are working on. To make a package.json run the following command in your terminal

{% highlight html %}
npm init
{% endhighlight %}

The NPM cli will ask you a series of questions which will be inserted into your package.json file. Now if you want to add a javascript library to your package.json then run the following command into your terminal.

{% highlight html %}
npm install package_name
{% endhighlight %}

It would be advantageous for you to have a package.json that you can use throughout your projects like as a blueprint. If you have a package.json with a list of packages you can run npm install and it will download all of those packages to your local project.

Before NPM, developers would have to manually keep track of JavaScript library updates. With NPM, you can update your library by running the following command.

{% highlight html %}
npm update react
{% endhighlight %}

You can also see all of your libraries that need be to be updated by running this command

{% highlight html %}
npm outdate
{% endhighlight %}

If you have a JavaScript library that you want to share with the world you can publish it to NPM’s repository of libraries. This would make your library available to any developer using NPM. That is a lot of developers. Just run the following command within your project that contains package.json.

{% highlight html %}
npm publish
{% endhighlight %}

Now that you have a basic understanding of NPM go out there and make an awesome web app that utilizes NPM. It will make your experience as a developer much more pleasant.

<iframe width="560" height="315" src="https://www.youtube.com/embed/hKrXJZvbD2E" frameborder="0" allowfullscreen></iframe>
