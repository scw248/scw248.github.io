---
layout: post
title:      "DRY: Partials With Locals"
date:       2019-04-01 11:56:50 -0400
permalink:  dry_partials_with_locals
---


The concept of DRY (Don't Repeat Yourself) is one you hear annoyingly often in software development, but for good reason.  When you're learning basic applications on your own, it seems fine to copy and paste code into separate areas, but with more complexity comes more bugs, and having to fix the same problem several times is annoying.  And if it's not annoying to you, it definitely will be to your coworkers when you're on a team.  A good example of DRY is partials.

Let's say we work for Twitter, and we're building the form for a new tweet that looks like this:

```
<h2>Create a New Tweet!</h2>
 
<%= form_tag tweet_path(@tweet), method: "post" do %>
  <label>Tweet Content:</label><br>
  <%= text_area_tag :content %><br>
 
  <%= submit_tag "Submit Post" %>
<% end %>
```

However, our edit form would be the exact same as this, so why recreate it?  Instead, we can create a new file in our views folder called '_ form.html.erb' and paste everything between 'do' and 'end' in our code into that file.  The underscore at the start of the file name indicates that the file is a partial and part of a larger view.  Now that we have our partial set up, we can render the form in our 'new' and 'edit' views:

```
<h2>Create a New Tweet!</h2>
 
<%= form_tag tweet_path(@tweet), method: "post" do %>
 <%= render 'form' %>
 
  <%= submit_tag "Submit Post" %>
<% end %>
```

```
<h2>Edit Tweet</h2>
 
<%= form_tag tweet_path(@tweet), method: "put" do %>
 <%= render 'form' %>
 
  <%= submit_tag "Submit Post" %>
<% end %>
```

If we were working in a view that is outside of the 'views/tweets/' folder, then we would have to edit our rendering to `<%= render '/tweets/form' %>`, so we can correctly access the form folder, but in this case, we only need 'form'.

This may not seem like a huge time saving opportunity, but imagine if this was a form to fill out a your information online for a doctor, or for a job application on linkedin!  You may need to debug, or change several lines in the form and you'd have to do it multiple times - increasing your chances of a spelling, syntax, or logic error.

Stick to DRY, and you'll save yourself a lot of headache in the future.  Happy coding!


