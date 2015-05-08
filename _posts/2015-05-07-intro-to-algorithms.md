---
layout: post
title:  "Awwww - Algorithms"
date:   2015-05-07 17:12:05
author: Dominic V. Smith
categories: gSchool Blog algorithms
image: true
---

Algorithms. Not just for NASA scientists and people who write numbers and stuff on chalkboards. 

So this week we've finally gotten in to material that terrifies me (ie. new stuff). I think I will split up the new concepts in to new blog posts. So in this post I will talk about algorithms, and specifically, algorithms for sorting.

First, let's start with what an algorithm is... because to be honest, before this week I thought it was something that required multiple degrees in mathematics and computer science to understand. An algorithm is a specific set of instructions for carrying out a certain procedure or solving a specific problem. That's it. 

In terms of programming, this means that someone found a really efficient way to do something, or answered a specific problem, and that solution has been proliferated through the programming world.  

So why are algorithms important in software development? Granted, I'm still fairly new to this world, and by no means an authority on algorithms... but basically, by promoting tried and true solutions to common problems, it prevents other programmers from having to re-invent the wheel, so to speak. 

In the computing world, however, not all algorithms are created equally. There can be multiple algorithms for the same task, and depending on what type of data you are working with or how complex it is, the efficiency of each algorithm can vary.

To start our adventure in to algorithms, we began with sorting algorithms. The common sorting algorithms are:

* Bubble Sort
* Selection Sort
* Insertion Sort
* Merge Sort
* Quick Sort
* Radix Sort
* Heap Sort
* Shell Sort
* Bucket Sort
* And probably more I am missing... 

<br>
There's a great website that visually displays how some of the different sorting algorithms work at [www.sorting-algorithms.com](http://www.sorting-algorithms.com/), how efficient they are at different tasks.

As an introduction to algorithms, we focused on bubble sort because it is one of the easier sorting algorithms to understand and reproduce. We used it to organize data inside an array, sorting numerical values from lowest to highest. To do this, bubble sort takes two values and compares them. The largest value gets moved to the higher position (bubbles to the top). The algorithm does this for nearly every value, but as a value gets sorted to the top, it is no longer checked. So as we get to the lower values, there are less values to run through to check. 

Here's a great video explaining how bubble sort works and why it is awesome: 
<iframe width="560" height="315" src="https://www.youtube.com/embed/Jdtq5uKz-w4" frameborder="0" allowfullscreen></iframe>
<br>
Once we understood how it worked, we had to create it from scratch. My initial version got the job done, but it modified the original array that was passed through. If you hit the **Run** button, you'll see the array ```[6666,29,543,3,45,78,21,9,666,30,67,77,88,99,103,30,1284,8]``` get passed through and sorted from lowest to highest.
<br><br>

<a class="jsbin-embed" href="http://jsbin.com/menapalaje/1/embed?js,console">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

<br>

This function is considered a destructive operation because it modifies the original array passed through it. As an unintended example of how algorithms become integral to problem solving in programming, a couple days after learning my first algorithm I came across another exercise in which I could use my new found bubble sort powers. To find the median value in a range of numbers, I wrote a new version of bubble sort to organize a range of values from lowest to highest, before finding either the middle number in the range, or the average of the middle two numbers. 

This time I wrote bubble sort to not be so destructive, instead copying all of its original values in its original order to a new array, and then modifying that new array, leaving the original one intact. The code is little longer, but functions the same way, with the sorted array then being checked for its median value. 
<br><br>

<a class="jsbin-embed" href="http://jsbin.com/repojipavo/1/embed?js,console">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

<br>

I'm sure this could be refactored to be much prettier, but for the purpose of the exercise, it got the job done and allowed me to figured out how to bubble sort without destroying the original array.

Look at me using algorithms... turns out they aren't as scary or nerdy as they sound. Ok, maybe they're still nerdy... but they're also pretty powerful. As we get in to more advanced algorithms, I'm sure they will get scary again. After all, some algorithms even [rule the world](http://www.theguardian.com/science/2013/jul/01/how-algorithms-rule-world-nsa). But bubble sort was a nice introduction to algorithms, and hopefully this post will help others realize that you don't need to be a mathematician or superhero (algorithm man... nerdiest super hero ever?) to harness an algorithms powers. 

Until next time.
