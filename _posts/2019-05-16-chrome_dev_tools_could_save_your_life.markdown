---
layout: post
title:      "Chrome Dev Tools Could Save Your Life"
date:       2019-05-16 20:15:31 -0400
permalink:  chrome_dev_tools_could_save_your_life
---


While working on my Rails/JS project, I was running into a lot more issues than normal.  Jquery and AJAX are rarely used anymore so there wasn't much point in using those, but I haven't learned React yet, so I was trying to get by with fetch() and Javascript alone.  

However, the main premise of the lab to render an index and show page with JS instead of Rails wasn't as straightforward for me because all of my index routes were nested and so were my show routes.  Frustration was mounting because I could see examples of what should work, but they weren't working for me.

Then a fellow student posted a video by Brad Smith from a previous Flatiron School cohort: [http://www.smithwebtek.com/asdf](http://).  While it is an older video that covers the basics of the project in AJAX, that wasn't what caught my eye; instead it was his use of Chrome Dev Tools.  It's hard to say what makes something click in your mind (maybe it was his passion for coding and his careful repetition of steps), but before watching this video, I had never felt comfortable using dev tools.  Suddenly, I had a multitude of helpers at my fingertips:


* Throw a debugger into my code so I could see my image attribute was generating as null

* Copy the line where I put my event listener to see that the function I was using in it was not running `e.preventDefault()` properly

* Select a link element within a button to see what the class is (just to double check since my event listener wasn't picking it up)

* Inspect my event listeners by clicking on the tab of the same name (when in the elements tab) and see if my click event is listed properly

* And of course, run my server and see that I have an error that my dataset is null.  Then, click on the link provided so it shows this is generating from the data-id I put in one of my div elements


The list goes on and on, and there's a lot more I realize that I can learn from these tools.  While I'll admit that they haven't solved all of my problems yet, they've definitely pointed me in the right direction, and saved me loads of time.  

So if you're tired of having to wait to ask fellow developers or a teacher what's wrong with your code, try dev tools, and save yourself a headache.

Oh, and thanks Brad Smith!


