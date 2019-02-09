---
layout: post
title:      "Blank Space (CLI GEM Project)"
date:       2019-02-09 00:19:38 +0000
permalink:  blank_space_cli_gem_project
---


*by Steve Wright*


It's true what other programmers say: a blank space can be one of the most terrifying things in the world.  Luckily, the Ruby community, and programmers in general, are very open to helping via chat boards, gems, and more.  

I wanted to build a gem that would pull the current days' headlines from the Reuters' website, show the user those headlines in a numbered order, and then allow the user to type a number to get the full story from the chosen headline.
When starting to build my gem, I felt I had a solid base due to prior lessons and videos supplied to me, but as time went on, I also really started to enjoy exploring, tinkering, and testing different code.  

However, there's always that moment when it feels like you're climbing a mountain, and then you find a plateau where you can't climb any longer because you used .each when you should have been using .map.  Or maybe you even have to go back down the mountain a little bit before you work your way up because you have to break your own code to figure out why you can't move forward.  I'm getting more and more comfortable with this being okay, and that if you have a mental mindset that these are inevitable, they won't get you down as much later on.  

Finally, there is the breakthrough where the core of what you want your gem to do works, and you are so proud and excited about it like a newborn baby!  Then, I find out it's bad practice to not make your scraping code its own class and I have to break my own baby.  Back down the mountain...

I should mention that I couldn't let go of my previous working code completely because I still need my base as a fragile beginner.  So I just comment it out while I build a new class, create some new code, and transfer previously created code to new locations.  Eventually though, the code starts working again, and now I've built a gem that is easier to build upon (and I can delete the old code).

Now I have my baby alive again, but it's ugly and making messes everywhere.  The text is being cut off mid-word, my inputs and outputs are spaced too close together, and text about photos is mixing in with the actual text.  What follows is a lot of exploring in gsub, regex, and other gems to help with word wrapping and styling.

Finally, a good-looking baby that is well trained!  I am proud of my child, and ready to show it to the world Lion King style!  My gem is Headlines_Today!





