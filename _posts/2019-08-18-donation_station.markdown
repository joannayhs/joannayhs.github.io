---
layout: post
title:      "Donation Station"
date:       2019-08-18 23:18:24 +0000
permalink:  donation_station
---


Coming into this project, I was not particularly confident. The past few months of my life has been a whirlwind. I started a new job, moved to a new house, started a new treatment for my chronic illness, and needless to say devoting the time and attention to understanding everything I needed to know for building a Sinatra app, was not at the forefront of my mind. 

One of the hardest parts about this project was coming up with an idea. Because I didn't truly understand the material,  I wasn't sure what Sinatra and ActiveRecord were capable of doing so I didn't know what kind of app I could make. The first week of working on this project, was spent mostly rereading old lessons, researching topics I didn't fully understand, and watching video walkthroughs. 

Eventually I came to the decision to build an app that kept track of donations and charities. I've always made it a priority of mine to give a portion of my income to organizations that are doing good work around the world, and so I thought it would be nice to have a place to keep track of those. 

I started the project by building my database with three tables: users, donations, and charities. On this site, users have many donations and many charities and the donations and charities belong to the user. I built the models for users, charities, and donations to reflect those relationships, and then got to work buliding the controllers and views for each object. 

I wanted the user to be able to view all of their donations and charities in one place, so I created a profile with tables that kept track of donations they've made as well as charities they created. Those tables includ a link to edit or delete their donations and charities. 

![](https://i.imgur.com/7GfAvoKl.png)

I also wanted users to be able to browse through other charities that have been added by other users in order to get inspiration. There is a page to view all charities with links to see just the information about that charity and a button to donate. There is a link to add charities on this page as well, which brings users to the form to add a new charity. 

![](https://i.imgur.com/hMfY42Gl.png)

I remember spending most of a Saturday working on the controllers of this project and trying to get my views to function the way that I wanted them to function. I spent hours coding and reviewing old lessons to try to understand material that didn't make sense to me the first time. After working all day, I had a functioning Sinatra app and I was so proud of myself! I had a lot of work left to do to make the app more interesting and complex, but I felt like I understood the material that I was not confident about going into the project. 

I spent the rest of that week fine-tuning my project. I noticed that things would break if a user deleted a charity they created, so I found a way to work around that error using conditional statements. 

I think the thing that was hardest for me to understand going into the project was how ActiveRecord worked to create relationships between models. I thought it automatically created the ID column in a table, but quickly learned that I'd have to create that column myself, but that creating the belongs to relationship added a `charities` method and `donations` method for the User class, which returns an array of all the charity objects and donation objects that have that user id as an attribute. I think there's still a lot for me to learn about ActiveRecord, but I feel much more confident after this project. 

Overall, I'm really proud of the work that I accomplished and look forward to learning more of the complexities that Sinatra and ActiveRecord have to offer for web development. 


