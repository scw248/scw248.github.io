---
layout: post
title:      "What is the Difference Between Static and Dynamic Arrays?"
date:       2019-08-02 01:17:29 +0000
permalink:  what_is_the_difference_between_static_and_dynamic_arrays
---


First off, did you know there was more than one type of array?  If you're a junior developer that has only studied Javascript, CSS, HTML, and Ruby like me, you may have thought that dynamic arrays (or just 'arrays' as they're referred in JS) are all there is.  

However, Java, C++, and several others programming languages have something called static arrays as well as dynamic ones.  It turns out that the distinction has a lot to do with how these are stored in RAM.  If we imagine our computer's Random Access Memory as billions of shelves, our dynamic array's length is chosen by the programming language (usually about 10).  Whether we take up four shelves or 10 of them (whether we put four elements in the array or 10), it is taking up 10 shelves.  

If we add an 11th element to that array, then the array size will double, but the next shelf may be taken by a Word Document (if you're saving them locally), or Spotify.  If that's the case, then the whole array needs to be copied with the new element and pasted to a location that can fit an array of 20 elements.  This is not the most common scenario, but because of it, this could take O(n) runtime, which is not ideal.

So what's the deal with these static arrays?  Well, this is how we implement a dynamic array:

```
let array = []

array[0] = 400
array[1] = 200
```

and so on...but a static array is written like this:

```
int array[] = new int[10]

array[0] = 400
array[1] = 200
```

where here we defined the length of the array (10), and now when we add elements to it, our worst case scenario is O(1) since we'll never have to worry about relocating the entire array.

Both of these arrays have fast lookups, but dynamic arrays have variable size and static arrays have fast appends.  Both can be useful in different situations, and if nothing else, now you know you're always working with dynamic arrays in Javascript!


