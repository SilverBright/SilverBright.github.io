---
layout: post
title:      "Rails with JavaScript: Some tips on getting started"
date:       2019-03-24 01:08:17 +0000
permalink:  rails_with_javascript_some_tips_on_getting_started
---


One of the hardest things about this project was figuring out how to get started.  How do I take a fully functional Rails app, throw some JavaScript at it, and make it work as a single page application?  Where does all the new code go!? How does the new code even talk to my app?  HALP!!

![Panic](https://i.imgur.com/73rPgGq.png)

Ok, DON’T PANIC (like I did).  Here’s some suggestions on getting started, and what’s worked for me:

Open your app and do the following:
* Update your **Gemfile**:
     * add `gem 'jquery-rails'`
     * add `gem 'active_model_serializers'`
     * optional: remove `gem 'turbolinks'` since you will now be taking over DOM manipulation
     * run `bundle install`

     (note:  There are additional steps to removing Turbolinks:, this might be helpful: https://stackoverflow.com/questions/38649550/how-to-disable-turbolinks-in-rails-5

Next…
* Add **serializers** into your Rails app:
     * In terminal run: `rails g serializer name-of-your-table`
     * Do this for each of your tables, for example:
```
       rails g serializer post
       rails g serializer author
```
							 
     * Add attributes and relationships to your serializer files, just like your models.  Do not include any validation methods. It should like something like this:

![](https://i.imgur.com/38rezzi.png)
![](https://i.imgur.com/CM1phqM.png)

Next…
* Add a **‘.js’** file to the **app/assets/javascript folder**:
     * Example:  `posts.js`
     * This is where all your magical JavaScript/JQuery/AJAX/JSON code will go for your project

Then…
* Update your **manifest folder**:   (my wut?)
     * open up your manifest file: **app/assets/javascript /application.js** --this is the file where you need to include the files you want to load into your rails app using `//= require`.
Here’s what mine looks like:

![](https://i.imgur.com/52KQsnR.png)

And that’s IT!!  

You can start adding your code in your ‘.js’ file, and choose whichever view file(s) you’d like the DOM to display.  Example: `views/post/index.html.erb`. 

I hope you found this helpful and best of luck to you.   

You got this!!

Here are some additional helpful links:  

http://railsapps.github.io/rails-javascript-include-external.html

https://www.sitepoint.com/active-model-serializers-rails-and-json-oh-my/

https://medium.com/@netranandamaharana/things-you-must-know-on-ruby-on-rails-single-page-application-d169b1a02065





