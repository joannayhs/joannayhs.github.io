---
layout: post
title:      "Ecclesia Connect: Rails Project"
date:       2019-10-25 17:38:32 -0400
permalink:  ecclesia_connect_rails_project
---


This project almost broke me. I went into it optimistic. I actually had an idea for what I was going to do for this one and I knew it would take a lot of work but I felt confident that I could do it. Then I started working on it. 

I started out with a goal to solve a real-life problem that I found existed in trying to coordinate volunteers during a Sunday morning church service. There are teams and leaders of those teams, but the leaders don't communicate with the other leaders and then no one knows what they're doing. I wanted to create an app that would help everyone communicate better. Leaders would be able to assign roles directly from the app, volunteers would be able to confirm those roles and in my very over zealous imagination, there would be a message board where volunteers and leaders could post to the group and comment on those posts. 

As I started working, it became clear to me that this project was more complicated than I thought it would be. All was well when I started creating the database and the relationships between objects. Things got more complicated when I started  trying to actually use those objects in the MVC framework. I struggled HARD trying to figure out how to create forms that created new instances of my objects and then update them. All the Rails lessons made me feel like Rails would feel like magic, but forms felt like anything but. I understood the lessons as I completed them, but when I went to apply the knowledge, I realized that there was a mental block I didn't know I had. 

When I saw code like the following, I could understand what it was doing. 

```<%= form_for @appointment do |f| %>
  <%= f.datetime_select :appointment_datetime %>
  <%= f.collection_select :doctor, Doctor.all, :id, :name %>
  <%= f.collection_select :patient, Patient.all, :id, :name %>
  <%= f.submit %>
<% end %>```

This form creates a new instance of an appointment by selecting a date and time and then a doctor's  name and a patient's name. What I didn't understand was what all those different options being passed into the `collection_select` field of the form did. I wanted the leaders in my app to be able to assign a role to a user by selecting the user from a drop down menu. This got all the more complicated when considering the fact that the form was for a role but to assign the the user to that role, I needed fields for the join table, `user_roles`. This is where I got stuck. If the task-manage app couldn't assign a user to a role then it was pointless. 

After spending an entire weekend trying without success to get this form to work, I eventually reached out to my cohort leader for help. Between his wisdom and many Google searches, I finally created a form that worked! The main piece I was missing is that I hadn't created a controller action for my user_role table that would update the user_role when the form was submitted. With that little piece of information, I was able to finally assign a role to a user and then with that I was able to get everything working in a way that met project requirements. I had to ditch my dreams of having a forum for users to communicate and it doesn't quite look as neat and clean as I imagined it would,  but in the end, I'm proud of the work I did and have a much deeper understanding about how forms in Rails work. 
