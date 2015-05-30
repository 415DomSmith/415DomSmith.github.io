---
layout: post
title:  "DOM Manipulation"
date:   2015-05-18 17:36:05
author: Dominic V. Smith
categories: gSchool Blog events
image: true
---

Dom (me) is easily manipulated by cookies. DOM (Document Object Model) is not.

This past week we've been working with the DOM, and learning how to manipulate it using Javascript.

For those more familiar with Dom(inic) (me), and not "the DOM"; The DOM is basically a list of objects that your web browser creates based on the HTML(or other files) it receives from a website's hosting server. When your browser gets this code, it "defines the logical structure of documents and the way a document is accessed and manipulated" (-Thanks [W3](http://www.w3.org/TR/DOM-Level-2-Core/introduction.html). 

This "logical structure" is typically described as a tree, where every object on a webpage (and many that aren't visibly displayed on the webpage) are not only linked together, but also share a larger base container (the document or the window, depending on how meta you want to get.)
<div class="post-img">
<img class="img-responsive img-post" src=" http://www.kirupa.com/html5/images/DOM_js_72.png "/>
</div>


So the DOM is basically a complex representation of an HTML document. It is made up of what we call elements, or DOM elements. A DOM element can be thought of as a piece of a web page. Your header, a "<p>" of text, an image, a link, and all other tags that make up a webpage are all elements. For a developer, what is important is that this list of elements is stored in the active memory of your browser. And with javascript, developers can edit this list of elements, and the individual properties of elements, to make visual changes to a web page after it has loaded in your browser.

I had a mindblown moment when I opened up the console on my browser for the first time, and looked at the level of detail and the number of objects and properties that are created for even the simpliest of webpages.

If you've never done it before, open up the console on your web browser. Don't worry, you won't break anything. For Mac users of Chrome, ```command + option + j``` on your keyboard is the default, in Firefox, the default is ```command + option + k```. Similarly, you can reach these screens through drop down menus. 

When the console opens up, you should be able to click on a tab that says either elements (for Chrome), or Inspector (for Firefox). When you fire up a webpage, those tabs get populated with a bunch of stuff, or if you want to get technical, a bunch of objects. These objects are what make up a webpage, and you can click around and check them out, and discover the levels of detail each one has. I encourage you, if you haven't ever done so, just check out some of your favorite websites through the console, and see what makes them tick, and in many cases the volumes of code that go in to making the simpliest of pages (google.com has a lot more going on under the hood than you would think.)

So why is this stuff important? Well, the list of things you see in the browser are your browsers interpretation of the lines of code it gets from a server. And unlike the base code that your browser receives, this list can be edited in real time to change what the user sees. That's how we get nifty animations or transitions to show up on a webpage, or even something as simple as a button pressing down or a window popping up. The DOM list gets edited, and things get added in (or removed). This is all done through Javascript, and we'll look at some examples that I have recently had to do as exercises at gSchool.






