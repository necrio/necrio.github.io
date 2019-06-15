---
layout: post
title:      "CLI Project"
date:       2019-06-15 13:07:11 +0000
permalink:  cli_project
---

This was by far my favorite part of this entire course.

While it has been a journey thus far, I feel very limited with the knowledge I was gaining. 

To eloborate slightly, I feel like the videos are completely too long and do not share enough information.  For example, the two example videos given were rather limited, incredibly long. What I would like to see is an edited version of these videos for the core parts and explaining them. Because as they are right now, they are recorded lectures. 

So, I found this awesome video that really  ( https://www.youtube.com/watch?v=b3CLEUBdWwQ&t=970s ) amazing at explaining scrapping and nokogiri. It was 30 mins of fantastic explanation. Despite how awesome it was at explaining the core of scrapping and nokogiri, it was limited on how to get more information.

In my research creating the scrapper tool, I had to learn about different layers of div. I did my project on the top 150 indie games on Steam. They labeled everything div. 

My first problem was the whole list was in <div main.ranking> and all 150 games were a child of that labeled <div#1-150>. In one example I found, they used div#1-50 to iterate through. However, everytime I did that it would return an empty array or an error. So, what I did find that empted is using nth-child. In the nokogiri selectors, they have a line of code <div main.ranking div:nth-child(n)> where you'd replace n with the child you want. In my case, it would be 2 to get the 150 games. 

I finally had everything working properly! Well, not exactly. It only game me the title, game release date, and genre. There was a lot of information available, but most importantly my CLI project was about game *ranks*. So, I had to get more information. Although, the rank was attached to the game title. 

So,  I had to get 3 more pieces of information. Since I had the previous 3 sets of information, I should be able to get the last three just by adding it. Votes, score, and rating. I plugged it into the scrapper.. Got empty arrays, an error, or more commonly just the first game's information. So, I was back to square one! 

I tried switching the n in the div:nth-child(n) to 3, since it appeared to be the next child. And it worked! --- Well, not exactly. It worked to get the votes, score, and ranking. But now I cannot see the game title, release date, or genre. Eventually, I figued out the simple solution.


In my code, I had it iterate through <div main.ranking div:nth-child(2)>.each do |game| 

game title: game.css('span.title')


But I had to be more specific with those last three. So I coded it as such.

votes: parsed_page.css(div main.ranking div:nth-child(3)>.css('span.votes')


Once that was done. Everything worked perfectly. I have never felt more happy about anything in my life. 
