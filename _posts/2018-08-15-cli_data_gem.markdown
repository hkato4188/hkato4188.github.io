---
layout: post
title:      "CLI Data Gem "
date:       2018-08-15 20:30:55 +0000
permalink:  cli_data_gem
---


Guess what!?  I just published a CLI Gem!  

For my first big project, I decided to create a webscraper that pulled stock information from Yahoo Finance, and now that I have completed this, I couldn't have been happier with my subject matter choice.  

I mean, it is easy to take stock tickers for granted.  Stock information is virtually everywhere, whether it be in a display running on the bottom of tv stations like Bloomberg News and CNN Money or sounded off audibly in the opening remarks in the morning and evening newscasts.  

In fact, up until recently, I have always found it somewhat pesky that they come built in as a standard feature on many Mac products--that was until I found my new appreciation for the complexities of building a stock API.  So for this blog post, I wanted to share my new found appreciation of object oriented programming in general by walking through the build of my gem and the intricacies of how my stock information is obtained.

I created my gem, using the "outside in method".  "Outside in" is such a valuable tool when approaching code challenges because without structure and direction, it is incredibly easy to get lost.  Do you think a construction worker would ever start laying down the foundation of a house without a blueprint?  Yes, it is super cheesy question that seems rhetorical, but it is easy to get caught up in a similar conundrum when programming.  

The larger and perhaps more hidden lesson in this analogy that I also learned is that our world is procedural and object-oriented.  Software is built for a reason and understanding how that reason relates to reality and can be communicated precisely in code is key.  In fact (side-note), object oriented code shares such close proximity to the real world, that Alan Kay actually conceptualized the architecture of objects as being analogous to biological cells--the building blocks of life.  

For those of you who are new to programming and computer sciences (like me!), take in the eloquent and keen words of Sandi Metz.  In her book POODR (Practical Object Oriented Design in Ruby) she challenges the reader to think of the world we interact with as being filled with objects--whether it be your spouse, your pet, or your car, each of these objects comes equipped with its own behavior and interactions.  

Although each one of these instances of objects has a procedure (for my cat's daily itenerary it involves methods that pertain solely to sleeping and eating) the world we live in isn't merely procedural; it is made up of spontaneious interactions.  It is these interactions and the beautiful complexities within them that makes object oriented programming so amazing.  In our world, behavior between our objects emerges naturally, but as programmers we have to immerse ourself in the objects to have a fighting chance of trying to capture this dynamic organizational relationship.  Going back again to Sandi Metz, programing failures might seem like failure in coding  technique but the reality is that they are more accurately just failures of perspective.

In my project, I tried capturing some of this beauty on a small scale by modeling the messages that pass between stock objects. So without further wait.... outlined below is my approach to building my Gem (for a deep dive, I invite you to look at the actual source code):  

Although I was super eager to feel like a "real programmer" and had a strong proclivity to start with live data, given the whole rant above, I fully understood the advantages of beginning with the end in mind, and crafting a blueprint of the user interface of my Gem with dummy data.  

Upon execution, I wanted my program to greet the user by listing the names of the most popular trending stocks.  From there, I wanted the user to have the option of gaining more insight into these stocks by having the ability to specifically choose a stock from the generated list of popular stocks to collect more details.  My code notes were as follows:

1. User types in stock_scraper
2. Gem shows a list of stocks and values:  
          
					Here are your stocks:
					
					a) TSLA Tesla, Inc. 
					b) Home Depot

Which stock would you like to learn more about?

3. User types in "a" and gets the associated stock Information

#Return value:  TSLA Tesla - Last Price: 361.60 - Market Time: 1:21PM EDT

With this framework, I was able to plug in fake data to get the overall interaction build.  Using my resources, I tapped into the awesome power of the bundler gem, which provided me with a packaged gem structure and left me with the challenge of instantiating stock objects (the remaining class constructions were rather straightforward).  

Since a Class is to me a type of factory for instances of that class (for this example a stock class) coding this framework for a stock begged the following questions:  

How do I think of the class construction of stocks and their attributes...or more simply put, what is a stock?
  1. A stock has an abbreviated symbol
  2. A stock has a name
  3. A stock has a last price

The latter most point then put me on the path of thinking about what is a stock price?
  1. A stock price has a market time
  2. A stock price has a change increment value 

Once these questions were stubbed out, all I had to do was scrape this information by iterating over a tabled data source of stocks, instantiating a stock object during this iteration process and assigning the respective scraped data to my stock object through reader and writer methods to assign and access each peice of data.  

With my user interaction model already outlined, I created a CLI object that would speak to a scraper object, that would in turn speak to a stock object.  Oh yeah, and there was a bit of alchemy involved...by mixing up a toxic brew of late nights and coffee... voila!  I had my stock scraper gem!!!!  Just kidding.... but not really though.

If you want to check my gem out and the source code you can run `gem install stock_scraper` and to utilize the gem's functionality simply type into your IRB session `require 'stock_scraper'` and then type in `show_stocks`.  

Happy coding!



