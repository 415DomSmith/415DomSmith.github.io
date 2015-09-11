---
layout: post
title:  "Learning Three JS and Web Audio API"
date:   2015-05-27 17:36:05
author: Dominic V. Smith
categories: gSchool Blog ThreeJS
image: true
---

We were given two days and a massive list of javascript libraries to explore and create something with. I chose three.js and web audio API, and created [this.](http://415domsmith.github.io/firstThreeJsAttempt/)  

Ever since going to [3D Webfest](http://415domsmith.github.io/gschool/blog/events/2015/05/14/3D-webfest.html) a couple of weeks ago, I had a fascination with 3D graphics in the browser. After that event, I knew that one day I would want to explore creating 3D spaces in the browser. But I didn't think I would have the time or chance to try it so soon. When we were given two days of class time to work independently on anything we want, I knew right away that I wanted to do something with 3D.

[Three js](http://threejs.org/) is a javascript library that makes [webGL](https://developer.mozilla.org/en-US/docs/Web/WebGL) a lot easier to use. It was originally developed by Ricardo Cabello, aka. [Mr. Doob](https://twitter.com/mrdoob), but has developed a decent sized open-source community and following. It is moving past obscure online art installations, and moving in to practical web and advertising. Here are a few recent examples that are taking three js mainstream, like [this site advertising Fox's TV show Gotham](http://witnessgotham.com/), or [this site advertising the sequal to the movie Divergent](http://www.thedivergentseries.com/). Ultimately, as browsers and computers become more powerful, I see the web progressing to include more 3D, and functional websites looking something like [this Japanese site advertising the Anime Ghost in the Shell](http://kobekokaku.jp/). 3D is taking over the movie theatres, why not the web next?

So now you understand why I chose to work with three js, let's look at what I did with it and how I did it. 

Three js creates a scene (much like a movie scene). Think of this scene like a blank canvas, or like an endless empty room. As the scene creator, it's your job to fill it with stuff, and we can fill it with just about anything. But once the scene has stuff in it, it's still just a frozen scene. Nothing is moving without a render function (which is a built in method of thee js). When 

It all began with a cube. The introduction tutorial at [three JS](http://threejs.org/) directs you in creating a 3D cube that rotates. Once I got that on the screen, I just started playing with it's parameters, and settled on an elongated rectangle version of the basic cube. To me it looked like a piano key, and looking at other examples of three JS I knew that I could use a loop to create a bunch of the same shape. The one little challenge with looping to create a shape is that all of the object you looped over show up in the same space. You need to change the starting position of each object you create, each time you create one. To fix this, I used the loop variable to just change the X position whenever a new object is created (positioning in three JS is controlled with normal X and Y planes, but since the space is 3D there is also a Z plane).







