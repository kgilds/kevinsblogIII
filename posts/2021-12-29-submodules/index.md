---
title: Submodules
author: Kevin
date: '2021-12-29'
slug: []
categories:
  - Shiny
  - R
tags: [ns, golem]
image:
  caption: ''
  focal_point: ''
---


> Don't forget the ns!

I was trying to incorporate submodules into my Shiny Application.  When I ran my application it was drawing blanks, but I don't recall if there was an error message in the console. 

This [stack overflow post](https://stackoverflow.com/questions/66569152/how-can-i-have-a-shinyapp-calling-a-module-which-in-turn-calls-another-module) helped me figure it out. Nothing complicated-- I just forgot the `ns` values in my submodules as well.

Here is some additional resources on [namespacing](https://engineering-shiny.org/structuring-project.html)