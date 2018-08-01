---
layout: post
title:      "Sinatra Project Completed"
date:       2018-08-01 21:48:28 +0000
permalink:  sinatra_project_completed
---


I had a lot of fun building this project.  

I made a Video Games Library app where users can create an account, log in, make a game, and add it to a library. 

It's not perfect and doesn't have all the functionality and beautification that I want, but it works.  

Feel free to try it out here: https://github.com/SilverBright/video-games-library-sinatra-project

Some thoughts...

This was harder than the CLI project in some ways, and easier in other ways that I did not expect.  Unlike my experience with the CLI project, which felt like perpetual chaotic fog from which I could not escape,  this time I saw patterns starting to merge and was able to visualize the general layout of my app.  Once I can visualize something, it makes it less overwhelming, and I can begin to tackle it piece by piece.  

Here's what clicked for me the most:

MVC: Model, View, Controller:

*  MODELS (Bartenders):  They take the orders from the waiters and makes the drinks. 

*  VIEWS (Patron):  It's five o'clock somewhere and the patron (user) wants to order drinks from the beautiful, glorious, user-friendly menu that's been provided by the waiter.

*  CONTROLLERS (Waiter): The Waiter takes your order, gives it to the bartender, picks it up from the bartender, and gives it to patron. 

In some cases the Patron may say it's the wrong drink, 'send it back and make me a new one'.  In that case the Waiter would take the order back to the Bartender and UPDATE it, unless the Patron says 'forget it, I don't want it'.  In that case, the drink would be DELETEd.

Now we have some exciting CRUD action going on (Create, Read, Update, Delete).

Though I debugged my project a little with pry when needed, most of the heavy lifting was done by shotgun - my new best friend.

[w3schools.com](https://www.w3schools.com/bootstrap/default.asp) is my second new best friend. If you ever need help with  your webpage layout or fuctionality (HTML, Bootstrap, etc.) This is the one-stop-shop place to go.  I must have bookmarked 300 pages at least.  (I kid.)

Like I said, I had a lot of fun with this project, and my goal in the future is to revisit this  at a later date and improve upon it as I build up more skills.  It's not a masterpiece, but perhaps one day it will be.

