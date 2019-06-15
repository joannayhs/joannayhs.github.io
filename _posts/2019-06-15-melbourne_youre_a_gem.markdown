---
layout: post
title:      "Melbourne, You're a Gem. "
date:       2019-06-15 20:17:25 +0000
permalink:  melbourne_youre_a_gem
---


In August 2015, I boarded a plane, and then another plane, and then another plane, before eventually setting foot in Melbourne, Australia. I spent a year there, working as an au pair and exploring the beautiful city and the rest of the country. When thinking through different ideas for my first Ruby CLI project, I realized I wanted it to be travel related and I knew Melbourne would be a good place to choose. I decided to make a gem that would allow the user to browse current events and attractions happening around Melbourne. 

My first step in the process was writing out what I wanted my CLI gem to do when it was finished. I wanted it to welcome the user and present him/her with a list of categories. I then wanted the user to be able to choose a category and view the related events and attractions in Melbourne. Then the user could select one of those events and see the details about where the event was located and the description of it. The user could go back and forth between the main list of categories and view as many events as they liked until they were ready to exit. I began coding by creating a `CLI class` that outlined the steps. I used pseudocode to symbolize what I eventually wanted the CLI gem to say. 

Once I got my CLI working, I created a `Scraping class` that scraped the data I was looking to collect. Finding the best website for the job proved to be a diffifcult process. I tried using popular travel websites that I'd used in the past, but the coding for them was complicated and was wasting time that I didn't feel I had. Eventually, I decided to go straight to the official [tourism website](http://https://www.visitmelbourne.com/regions/melbourne/things-to-do) for Melbourne where I found exactly what I needed. Scraping is a skill that has been really challenging for me to fully comprehend, but this project helped me to really understand the process. I was able to scrape the website for a list of attractions and their urls. I then scraped those urls to find the details about each attraction that would be displayed in my CLI gem. 

I quickly realized that my project needed an `Attraction class` that would create new attractions and save them. This class was able to keep track of all the data for each attraction and event. As I worked, I realized that I needed this class to be able to sort the attractions in name order, so I created a class method for that. Once I created that class, I incorporated it into my `Scraper class` so that as I scraped the information, I instantiated a new attraction at the same time. When I started building the relationships between classes and putting the pieces together, I  realized that I was making the `Attraction class` keep track of its categories, which is something a `Category class` should probably do.  That's when I created a `Category class` that kept track of and organizaed each of the different categories. I incorporated the institiation of that class into my `Scraper class` as well.

Once I had all my scraping complete and my attractions and categories were organized and relating appropriately, I went back to my `CLI class` and began refactoring my pseudocode to work with my newly created objects. This took a lot of brain power and I had to create different class methods and instance methods to make it work, but in the end, I managed to create a gem that did exactly what I wanted it to do. 

My `visit_melbourne` gem welcomes the user and provides a list of categories: 

![](https://i.imgur.com/aVW0rU7.png)

When the user inputs a number corresponding to the category, he/she gets a list of attractions and events in that category: 

![](https://imgur.com/qK6vekn.png)
![](https://imgur.com/FwVKVBQ.png)

Then the user can choose a number that corresponds with an event or attraction and get more information: 

![](https://i.imgur.com/FDzDbxc.png)

Each level provides the user with a way to get back to the category list or to exit the program. My program takes edge cases into consideration and will respond to tell the user to enter a valid input: 

![](https://i.imgur.com/Ft16T11.png)
![](https://i.imgur.com/zz6H1b1.png)
![](https://i.imgur.com/mfeMiSP.png)

When finished, the user types "exit" and is told to enjoy his/her visit: 

![](https://i.imgur.com/0Wk0X1k.png)


This project really tested my knowledge of Ruby and how to code and problem solve. There were some frustrating moments, but overall, I am so proud of the outcome. Two months ago, I never would have been able to produce anything like this and now that it's done, I want to show everyone I know! 

You can find the CLI Ruby gem [here](https://github.com/joannayhs/Melbourne-Visit).

Enjoy your visit! 


