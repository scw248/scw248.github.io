---
layout: post
title:      "It's All About the Patterns"
date:       2019-07-26 15:20:53 -0400
permalink:  its_all_about_the_patterns
---


When you start out prepping for technical interviews, you could use any number of resources (Coderbyte, HackerRank, CodeWars, etc), and the temptation is to figure out an answer, and then memorize it - or look up the solution and memorize it is generally a strong one.  

However, how much would a slight variation to that problem throw you off completely, and make you fail to answer the questions correctly?  This is why actually learning and algorithms, design patterns, and general solution patterns are much more important - and they could help you immensely on the job as well.

While reading 'Cracking the Coding Interview', I got more familiar with these algorithms and patterns, but in my opinion, that book assumes your knowledge on quite a few things, and may not be enough alone for a bootcamp grad.  That is how I came upon two other resources that make a more in-depth effort to explain the patterns you should know: LeetCode and InterviewCake.  LeetCode isn't terribly different than CodeWars or the others, but I do like that after you come up with a solution, it will walk you through a solution with a faster runtime and less memory usage.  For example:

sortScores is a function that will take an array of scores for a video game, and a high score that will be the maximum number that can be reached.  It should return the scores sorted in descending order.  My brute force, but seemingly efficient solution was:

```
function sortScores(unorderedScores, highestPossibleScore) {

   if (unorderedScores.every(num => num < highestPossibleScore)){
       return unorderedScores.sort().reverse()
     }
     else {
       return unorderedScores.filter(num => num < highestPossibleScore).sort().reverse()
     }
 }
```

However, in this solution, you're iterating through the array, and then sorting, which take quite a but of runtime.  A more efficient solution is not quite as simple:

```
function sortScores(unorderedScores, highestPossibleScore) {

  const scoreCounts = new Array(highestPossibleScore + 1).fill(0);


   unorderedScores.forEach(score => {
       scoreCounts[score]++;
   });

   const sortedScores = [];

   for (let score = highestPossibleScore; score >= 0; score--) {
     const count = scoreCounts[score];

     for (let time = 0; time < count; time++) {
       sortedScores.push(score);
      }
   }

   return sortedScores;
 }
```

InterviewCake is similar except it goes a level deeper to ask you if you have an answer to the question, it will explain, the 'gotcha' aspects of the problem, and if you're not getting it, you can keep clicking 'Tell Me More' so it can give hints or explain what algorithm or pattern the problem is looking for.  

InterviewCake is a paid service after a few problems, but whether you want to pay or not, the biggest takeaway I've had from it so far is that every day when you learn a new pattern or algorithm, write it down in a doc or on a piece of paper, and read over that list EVERY SINGLE DAY.  It is not that others are smarter than you, they just have more experience, so keep familiarating yourself with these patterns, and you're on your way to solving any technical problem.
