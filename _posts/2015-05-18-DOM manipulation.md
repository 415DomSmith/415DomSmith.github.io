---
layout: post
title:  "DOM Manipulation"
date:   2015-05-18 17:36:05
author: Dominic V. Smith
categories: gSchool Blog events
image: true
---

Dom (me) is easily manipulated by cookies. DOM (Document Object Model) is not. Talking about the DOM, and showing off a [mini-project](http://415domsmith.github.io/pixelArt/)

This past week we've been working with the DOM, and learning how to manipulate it using Javascript.

For those more familiar with Dom(inic) (me), and not "the DOM"; The DOM is basically a list of objects that your web browser creates based on the HTML(or other files) it receives from a website's hosting server. When your browser gets this code, it "defines the logical structure of documents and the way a document is accessed and manipulated" (-Thanks [W3](http://www.w3.org/TR/DOM-Level-2-Core/introduction.html). 

This "logical structure" is typically described as a tree, where every object on a webpage (and many that aren't visibly displayed on the webpage) are not only linked together, but also share a larger base container (the document or the window, depending on how meta you want to get.)<br>

<img class="img-responsive img-post" src=" http://www.kirupa.com/html5/images/DOM_js_72.png "/>

<br>

So the DOM is basically a complex representation of an HTML document. It is made up of what we call elements, or DOM elements. A DOM element can be thought of as a piece of a web page. Your header, a "<p>" of text, an image, a link, and all other tags that make up a webpage are all elements. For a developer, what is important is that this list of elements is stored in the active memory of your browser. And with javascript, developers can edit this list of elements, and the individual properties of elements, to make visual changes to a web page after it has loaded in your browser.

I had a mindblown moment when I opened up the console on my browser for the first time, and looked at the level of detail and the number of objects and properties that are created for even the simpliest of webpages.

If you've never done it before, open up the console on your web browser. Don't worry, you won't break anything. For Mac users of Chrome, ```command + option + j``` on your keyboard is the default, in Firefox, the default is ```command + option + k```. Similarly, you can reach these screens through drop down menus. 

When the console opens up, you should be able to click on a tab that says either elements (for Chrome), or Inspector (for Firefox). When you fire up a webpage, those tabs get populated with a bunch of stuff, or if you want to get technical, a bunch of objects. These objects are what make up a webpage and you can click around and check them out to discover the levels of detail each one has. I encourage you, if you haven't ever done so, just check out some of your favorite websites through the console and see what makes them tick, and in many cases the volume of code that goes in to making the simpliest of pages (google.com has a lot more going on under the hood than you would think).

As I mentioned earlier, your browser makes a list out of the lines of code it interprets. And unlike the base code that your browser receives, this list can be edited in real time to change what the user sees. That's how we get nifty animations or transitions to show up on a webpage, or even something as simple as colors changing or a window popping up. The DOM list gets edited, and things get added in (or removed). This is all done through Javascript, and I'll share an example of my first DOM manipulation project I recently did as an exercise at gSchool.


We were tasked with creating a webpage that contains a grid based drawing platform to make "pixel art". There were no real stipulations on how it should look or function, other than that you should be able to use multiple colors to draw something.

To do this, I started with making the "canvas" to draw on in a javascript file separate from my HTML. My HTML included a script tag that linked to this javascript file, and when the browser reaches this tag, it knows to go get the script file and run that when it receives it. The first part of the javascript was a function with a for loop that produced over 2800 little white squares (made out of div elements). The alternative I guess would have been to hard code the div's in to the HTML 2800 times... which obviously would have taken a real long time to do...The power of javascript and DOM manipulation.

Here's the code for the canvas function:
<br>
 <a class="jsbin-embed" href="http://jsbin.com/mukuceroxa/1/embed?js,console">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

 <br>

 After I had the div's created, I used more DOM manipulation in the javascript file to loop over each div and add an event listener function, which basically waits for a div to be clicked (it listens for the "click"). This function is what creates the drawing effect, by changing the background color of the div clicked. This color is selected using a variable for the color name, which is selected by choosing one of the color buttons coded in to the HTML. These buttons also have event listeners on them, as well as some styling hard coded in to a CSS file to make them look a little more interesting (hover effect and color change when they are selected). I also created a button reset function that made the currently selected color button return to it's de-selected look.  

 This is what the code looks like:


 <a class="jsbin-embed" href="http://jsbin.com/mepopevica/1/embed?js">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

<br>
So the end result is [this little pixel drawing page.](http://415domsmith.github.io/pixelArt/). Check it out and play around.

<br>

In hindsight, there are ways I can improve the code for this. I could have used [event propagation](http://info.meteor.com/blog/browser-events-bubbling-capturing-and-delegation) to add event listeners to the divs, rather than looping over them to add the listener. Additionally, I could have made the cavas size a little more absolute, because it doesn't really scale well when the window is resized or it is opened on smaller resolution screens. But all in all, for my first real exposure to DOM manipulation, I'm pretty happy with how it turned out. I even enjoyed playing around with it a bit.

<div class="post-img">
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/pixelArtDemo.png"/>
</div>







