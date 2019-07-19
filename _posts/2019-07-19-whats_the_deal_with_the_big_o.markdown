---
layout: post
title:      "What's the Deal With The Big O"
date:       2019-07-19 17:17:35 +0000
permalink:  whats_the_deal_with_the_big_o
---


I didn't major in Computer Science or a related field in college so while mathematics and problem solving have always been something I pride myself on, practicing algorithms was not a common occurrence for me.  

However, once you graduate a development bootcamp, you realize that a lot of available junior developer positions require knowledge of these.  You might first ask yourself "Wait, why didn't my bootcamp teach me these things?"  Well, if they did, do you think you could have properly absorbed that information on top of all of the coding work and language/framework learning that you were doing?  Probably not.  Bootcamps are great, but far from perfect, and they can only require you to learn so much in a short period of time.  The rest is appropriately on you.  And what is the top Computer Science topic everyone says you should know?  The Big O (or asymptotic runtime complexity).

The Big O is a metric to evaluate the efficiency of an algorithm.  This is a BIG DEAL because of our fast-paced world today.  In a data-heavy world where we, users and consumers, want our phones, tablets, laptops, and more to give us websites and applications that are lightening fast, so much of programming goes into making applications run faster.  For example, ([Google says 53% of mobile users abandon sites that take over 3 seconds to load](http://www.marketingdive.com/news/google-53-of-mobile-users-abandon-sites-that-take-over-3-seconds-to-load/426070/))  This is where the Big O is critical.

Not long ago, an engineer recommended to me that I take a look a course titled '[Intro to Algorithmic Thinking and Peak Fiding](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/lecture-videos/lecture-1-algorithmic-thinking-peak-finding/)' provided by MIT's Open CourseWare (a wonderfully free place to take MIT courses online).  I will use an example from this to explain the benefits of the Big O.

Imagine your application has to evaluate the array below:

```
[1, 2, 3, 4,9, 6, 7, 8, 5]
```

In your application, it must find the largest number in the array (aka peak).  If you run a basic `for loop` and go from the beginning of the loop to the end of it to find out that the middle number is, in fact, the peak, then you are dealing with a worst case scenario, or ⍬(n).  This may not seem like a big deal, but imagine if your array is part of a massive data set of user objects so it has millions of pieces of data.  Evaluation with this basic `for loop` could take 10+ seconds, and the user decides to leave the site because of it.

A simple solution to this problem is to do a binary search and start at the middle to evaluate the left and right side of the array.  So we're going to start with `array[Math.floor(array.length / 2)]` - let's say it has a variable name of middle.  

-Then evaluate if `middle > middle +1` and if `middle > middle -1` to look at the values to the left and the right of the middle element.  

-If `middle > middle +1 === true`, then we'll iterate over the left side of the array, and if `middle > middle -1 === true`, then we'll iterate over the right side of the array.  

-If they're both correct, then we've found our peak!

The point here is that now your Big O is O(log2n) and you've cut down your run time significantly so your application runs faster.  Now, you might say 'Wait!  That may not be the largest number,' and you'd be right in saying that.  You could run a more complicated algorithm for this, but IF the middle number in an array with the length of the one above is the case, then this is the your most efficient algorithm.  This example is for simplicity's sake.

Anyway, if you want a developer job and you want to be a good developer, you're going to have to learn these concepts.  I would recommend the MIT course above and the highly regarded 'Cracking the Coding Interview by Gayle Laakmann McDowell.  

I learned a lot in Flatiron School's bootcamp, but there is always more to learn, so be passionate, and enjoy it!  


