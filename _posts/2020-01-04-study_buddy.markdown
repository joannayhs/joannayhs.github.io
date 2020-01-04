---
layout: post
title:      "Study Buddy"
date:       2020-01-04 18:05:44 +0000
permalink:  study_buddy
---

For the javascript single page application (SPA) project, I wanted to do  something that  was relevant to my past life as an education major. I graduated college as an Elementary Education and STEM major. I taught a fourth grade class during my student teaching experience, so I decided to try to make an app that they could use to help them study some of the things I taught them in class. 

![](https://i.imgur.com/N4vTbEHl.png)

This SPA felt like a huge hill to climb when I started. The lessons during the javascript section were good for covering the basics, but I felt like I didn't know how to put it all together. I understood Rails and I understood how to manipulate the DOM using Javascript, but my biggest challenge was figuring out how to get the two to communicate. 

I started this project by building my backend first. I created three different tables in my database: Quizzes, Questions, and Options. Quizzes  have many Questions and Questions have many Options. Questions belong to Quizzes and Options belong to Questions. A Quiz has many options through questions. 

Once those were set up, I set up routes that would display the data from my database as JSON objects. The code to do that looked like: 
```def index 
        quizzes = Quiz.all 
        render json: quizzes, include:[:questions, :options]
    end ```
		
The reason for adding the `include` tag when rendering the json at the quizzes index route was so that the data would be available when fetching the data during an AJAX call. 

When I was finished the backend, I started working on the frontend.  This proved to be the most difficult part. I felt unsure as to how best to separate my javascript into classes. The lessons during this section had us coding in an index.js file but  didn't model how to create files for separate classes. Thanks to videos made by my cohort leader, I was able to get it working, but this is an area of my project I still feel could use some improvement. 

My project features three AJAX class. I have a `.fetch` call that uses the `GET` method to load the quiz data in my API so that I can display it on the DOM. I have another `.fetch` call that uses `GET` to fetch all the question data from my API. The final `fetch` request  uses a `PATCH` method to update a quiz's  status as complete. 

I found that this project helped solidify my understanding of how to use event listeners. I have many instances of event listeners  listening for click events to know when someone chooses certain options on the quiz and those events trigger certain `div` elements to appear and others to disappear.  It was tricky to figure out what to show and what to remove, but I think eventually I got the hang of it. 

Overall this project was a challenge, but in the end, I'm really proud of all that I was able to accomplish and I really like javascript and the different things it can do for web development. 
