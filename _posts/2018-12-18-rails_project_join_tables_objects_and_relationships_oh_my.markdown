---
layout: post
title:      "Rails Project: Join Tables, Objects, and Relationships, oh my!"
date:       2018-12-18 18:31:00 -0500
permalink:  rails_project_join_tables_objects_and_relationships_oh_my
---


Understanding the concept of object relationships in Rails (using the has_many :through association in a join table) has been the most challenging part of the project for me. I hope the following explanation below will help anyone who is just starting work on their project to get a better understanding.

First, let’s look at the Has-Many-Through definition from the Ruby on Rails Guide:

“A has_many :through association is often used to set up a many-to-many connection with another model. This association indicates that the declaring model can be matched with zero or more instances of another model by proceeding through a third model.”  https://guides.rubyonrails.org/association_basics.html#the-has-and-belongs-to-many-association

That third model is the join table.  Any table that contains two foreign keys can be thought of as a join table. 

My app: Haunted (a website where users can add and review cool haunted locations) features a Users table, a Haunted table, and a Comments table as the join table.

You can check it out here: https://github.com/SilverBright/haunted

My join table is very simple, and looks like this (user_id, and haunt_id are my two foreign keys): 

![Imgur](https://i.imgur.com/Aq87k3W.png)

For the User Model, the user can create many comments, and can have many haunts through comments.

User Model:
```
has_many :comments
has_many :haunts, through: :comments -->  this creates the many to many relationship
```

For the Haunt Model, a Haunt can belong to a User, have many comments from users, and have many users from comments.

Haunt Model:
```
belongs_to :user
has_many :comments
has_many :users, through: :comments
```

For the Comment Model (join model), comments belong to both the user and the haunt.

Comment Model:
```
belongs_to :user
belongs_to :haunt
```

So, what would this look like in the database?

In the example below, in the first row, we can see a Comment with an ID of 1 was created by a User with an ID of 1 for a Haunt with an ID of  2.  A Comment, with a column for ‘content’, has many users, and many haunts. 

![Imgur](https://i.imgur.com/Khq4MCU.png)

With our db tables and associations set up in the models, we can chain our objects together to get a collection of all of those haunts, users, and comments.

In this example, I’ve chained a specific Haunt object with comments and users so we can see all the Comments for that Haunt by each User: 

![Imgur](https://i.imgur.com/pOKbmxN.png)

Which looks like this when published:

![Imgur](https://i.imgur.com/lfr105G.png)

I’ve also chained the current users to their haunt reviews:

![Imgur](https://i.imgur.com/i90Fs14.png)

Published:

![Imgur](https://i.imgur.com/HSPbXoB.png)

As you can see, I am a very visual person, and generally need charts and diagrams to get concepts into my head!!

I hope this has been useful and informative, and you have gained a better understanding on many-to-many relationships in Rails (specifically, when using has_many :through)!  

Best of luck on your Rails project. 



