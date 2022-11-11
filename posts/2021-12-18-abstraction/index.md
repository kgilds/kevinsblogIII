---
title: Abstraction
author: Kevin
date: '2021-12-18'
slug: []
categories:
  - R
tags:
  - shiny
  - functions
image:
  caption: ''
  focal_point: ''
---

### Introduction

I am preparing for a presentation on shiny modules I am giving in the coming week and it got me thinking. The comparison between the use of modules and functions is on point and I want to dig into the statement some more. 


### Function based approach


> I was once had an analysis pipeline that I compared to a worn down car. You turn it on in the morning and not confident it was really going to start or if it did start was it going to leave you on the side of the road.  

My analysis pipelines used to be long complicated R scripts but I have transitioned to using functions within script files and or Rmd files. What got me on this road was the discussion around the [Drake/Targets Package]().     


The first time someone paid me to develop a Shiny Application the application was a beast with thousands of lines of code and awful to maintain.  


I tried using modules but this did not work out. 

Thankfully, I was soon introduced to the Golem Package and started modularzing my applications. 