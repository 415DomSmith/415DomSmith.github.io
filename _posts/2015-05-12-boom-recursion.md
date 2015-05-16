---
layout: post
title:  "Bang -- Recursion"
date:   2015-05-12 14:36:05
author: Dominic V. Smith
categories: gSchool Blog recursion
image: true
---

ALWAYS remember... TRUST THE RECURSION!

More new concepts! Yay-ish!

So we journeyed down the rabbit hole that is recursion at the end of last week. For those who were like me before this class, and have no idea what recursion is... I think the official definiton is:

```re·cur·sion -(riˈkərs-on)```

```Adjective. See definition of recursive.```

That's a bad joke, but apparently part of the hazing process of joining the recursion brotherhood (recursion is kind of culty...).

I think recursion might be best explained with an example. Think of a Russian nesting doll. Inside each doll, there is a smaller version. And inside that, an even smaller version. And so on, and so forth, **UNTIL** we reach the smallest version of this doll. 

<div class="post-img">
<img class="img-responsive img-post" src=" {{site.baseurl}}/img/nestingdoll.jpg "/>
</div>

The smallest version of this doll is a big part of what we're looking for in recursion. In recursion, this smallest doll is what we call our base case.

Recursion is a way to solve a problem by only solving a smaller portion of the larger problem. This concept mainly applies to instances where we would need to use itterations or loops inside a function to get the function to work. Just about any function that can be solved with a loop can be solved through recursion, and vice versa. Now this doesn't always mean that recursion is the best or systemicly fastest way to solve a function, but it often does require less written code. 

So when we write a recursive function (which we'll look at in a second), we are making the function do all the work by calling the function within itself. In order to make sure that the function doesn't continue forever (or until a stack overflow, which we'll look at in a minute), we want to decrease some value passed through the function, and set a lower limit for this value (which will be our base case). When the base case is reached, we stop calling the function within itself.

So let's look at recursive function that is a pretty standard introduction to how recursion works, factorials:

<a class="jsbin-embed" href="http://jsbin.com/bixanayulo/1/embed?js,console">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

To find the factorial of a number, you take that and you multiply it by every number below it.

So the factorial of 5 would be: ```5 x 4 x 3 x 2 x 1```
which equals 120.

To simplify this, we know that the factorial of 5 (120) is 5 x the factorial of 4 or ```4 x 3 x 2 x 1``` or 24. And to simplify this even further, we know that factorial 4 (24) is 4 x the factorial of 3 or ```3 x 2 x 1```which is 6. We can keep going down until our base, which is 1. 

This creates a cascading effect, and as we simplify it, we decrease the values we are working with until it's something base and small (like 1). And this is why recursion is awesome, because rather than working with a big number (like 120) or a big problem, we can work with smaller numbers, and solve a smaller portion of that larger problem. If we look at our code above, we'll see that our initial question is the factorial of n, which in this example is 5. But rather than solve for n, we are trying to solve for ```factorialR(n-1)``` or ```n - 1``` (4). Because the function is calling itself on every pass, we're subtracting 1 from n on every pass, until we get our base.

Again, looking at the code, we see that our base is ```if n === 0```. This means that when our passed value (n) gets down to 0, we've recursed down as far as we can, and then the function will work on returning back up.

After the function cascades down it then cascades back up. When a function calls itself, the functions passing values higher than the base are stored in memory, waiting to complete their call. Once the base is reached, every function, in order, is able to complete its call and return its value as input for the function above it. The functions waiting for their input from the function below them are waiting in "the call stack", which is a form of active memory for the program environment. Because multiple copies of a function need to be stored in a suspended state as they wait for their input, recursive programs can take up a lot of memory. This is especially true when a function needs to call itself a lot of times.

It is possible for a recursive function to take up too much memory, by calling itself too many times and having too many copies of itself waiting for input (the number of copies in memory are sometimes referred to as "recursive depth"). When this happens, it is possible for the call stack to essentially crash or "overflow", causing decreased system performance and possible crashing. The most commonly used term for this is stack overflow (it's more than just a [website](http://stackoverflow.com/)).

In some cases, a recursive solution may not be the best solution. If you have a function that needs to run recursively a large number of times, you can seriously bog down your computer or cause a crash. Also, problems without a base that you can return to are virtually impossible with recursion. Additionally, problems where you need to pass information around in a variable, or return a variable, are difficult to get to work in recursion.

I'll share one more example of a recursive function, this one is a little more fun than factorial.

<a class="jsbin-embed" href="http://jsbin.com/tahipufone/1/embed?js,console">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

The above code works similar to factorial, in that we are returning (n-1) every time the function calls itself. With a base n of 99, the function calls itself quite a few times... and every time, it logs to the console the "99 bottles of beer" song. We have our base of ```n === 1```, so that it stops calling itself at 1. There is also an if statement for ```n ===2```, just to catch the plural change in the wording, from "bottles" to "bottle".

Fun stuff, and real simple examples of recursive functions. 


Until next time.








