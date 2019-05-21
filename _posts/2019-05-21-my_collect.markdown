---
layout: post
title:      "My Collect"
date:       2019-05-21 18:18:44 +0000
permalink:  my_collect
---


I'm a little over a month into my Software Engineering journey and so far, so good. I find myself falling asleep thinking about possible solutions to a lab I'm trying to solve. Each day, I seem to understand something more fully than I did the day before. With each new solution to a lab, I feel more confident in my decision to pursue this new career. 

When I think about the labs I've already completed, there is one that I would love to never revisit (which is why I should definitely revisit it). The one that jumps out is the "My Collect" lab. I prefer to do things as simply as possible, and this lab seemed to complicate the `#collect` method that I had just learned a few lessons ago. If we have this method, why bother learning to make it myself? 

But having done this lab, I realize that learning the complexities behind the simple helps to deepen my understanding of the logic. And that logic is really the lesson that I need to understand as a programmer. Labs like this help to show that there is more than one solution to any problem, and knowing that allows me to try new approaches to solving problems. This seems like a pretty important skill.

Let me walk you through `#my_collect`. This lab asked me to create a method that accepted an argument of an array and return a new array with each item of the array altered in some way without using the `#collect` method.  

Here's how I solved this problem: 

```
def my_collect(array)
  counter = 0 
  new_array = []
  while counter < array.length
    new_array << yield(array[counter])
    counter += 1 
    end
  new_array
end 
```



I struggled through this lab and it's only really looking back, having practiced more coding challenges and completing more labs since then, that each piece truly makes sense. What is my method above doing? 

It sets a counter equal to 0. This counter could also be referred to as the index, because that's really what it indicates. Then it sets a new, empty array. Then it starts looping. Anything after `while` continues until the counter is less than the length of the array. In other words, the loop continues for as long as there are items in the array. Each time it loops, an item of the array is yielded to a block of code that changes that item and then shovels it into the new array. Then the counter is increased by one, or the index increases by one, each round until it is equal to the length of the array. When it finishes looping, it displays the new array with the altered items. 

I'm pretty proud of the fact that I can go through and explain all of that. Yes, it would be much easier to call `#collect` on the array, but because I had to complete this lab, I understand "while" loops better. I understand how to use a counter that represents an index and how to call a single item of an array using it. I understand how I could change this to make it look more like an `#each` or `#select` method. I've solved similar coding challenges using the logic I used in this lab. 

I'm excited to keep learning and growing and finding new challenges that frustrate me, becuase ultimately they teach me how to think through the problems I'll eventually face every day.
