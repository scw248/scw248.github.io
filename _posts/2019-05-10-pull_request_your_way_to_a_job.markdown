---
layout: post
title:      "Pull Request Your Way to a Job"
date:       2019-05-10 20:41:41 +0000
permalink:  pull_request_your_way_to_a_job
---


After speaking with several VPs and Directors of Engineering that I used to work with while I was in sales, a common tip  provided for someone entering a coding bootcamp was that I should contribute to open source projects on Github to impress employers when looking for ajob.  

After some research, I understood that these projects are of all sizes/scales from companies/groups that list them as accepting external help.  What does the helper get out of it?  A great example to employers that he or she can work with other developers on the same code, which is what you're usually doing on a software engineering team (as opposed to building something from scratch and nobody else touching your code).

With some help from my Flatiron Tech Coach, I was pointed in the right direction on places to start: https://www.firsttimersonly.com/, https://github.com/MunGell/awesome-for-beginners#ruby, and https://firstcontributions.github.io/#project-list are among the many options.  Once you find a project that isn't already being worked on and you're comfortable completing it, send a message to whoever posted the issue, and claim it!

While it can be a little scary to know how to fork, clone, sync, merge, and push correctly (and different groups on Github may have different requirements), it generally follows a similar pattern:


1. Click the 'Fork' button on GitHub to copy the repository to your account.

2. Click the 'Clone or Download' and copy the link provided.

3. In your terminal, make sure you are already inside the folder that you'd like to clone the repository into.  Then type `git clone <paste your copied link here>`

4. You should see in your terminal that you are on the 'master' branch (ex: `[09:38:04] (master) Flatiron`).  To avoid confusion when you submit your changes to the code, create a new branch and make your changes on that one.  You can do so by typing `git checkout -b <name your feature branch>`

5. Once you open up your code editor (ex: `code .` for VSCode), make the necessary edits to the code as requested in Github.

6. It is best practice to commit your changed code every 5-7 minutes, but if the issue you're solving only requires a line or two of code, you're probably fine with commiting just once.  To do so, start by typing `git add .` and press enter.

7. Then `git commit -m 'briefly describe the changes you made here'`, and press enter.

8. Finally, type `git push -u origin feature-branch-name` and press enter.*


AWESOME!  Now you've submit the changes, and you're feeling on top of the world...but the issue creator on Github leaves a comment or two that your code isn't quite right and needs to be corrected.  DON'T PANIC!  There is a process for this too!

First, you need to make sure your copy of the remote repo is up to date with what's on Github (since others may have submitted changes since your fork), so you may need to sync with an upstream.  To do so, and any time you need to sync your local repo with the remote one, follow these steps:


1. `git fetch upstream` to grab the updated version of the remote repo

2. `git checkout master` to go to your local master branch

3. `git merge upstream/master` to update your local master branch

4. `git co your-feature-branch-name` to jump back to your feature branch

5. `git merge master` to update your feature branch with your local master one*


Finally, make your edits needed to your code, and push your changes to GitHub again: `git add .`, then `git commit -m 'briefly describe the changes you made here'`, and this time you can just type `git push`.  Voila!

It can be a lot initially, but so was tying your shoes the first time you did it.  You learned, and the more and more you do it, it will become second nature!

Happy coding!




