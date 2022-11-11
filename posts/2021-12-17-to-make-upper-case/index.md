---
title: To make upper case
author: Kevin
date: '2021-12-17'
slug: []
categories:
  - R
tags: [til]
image:
  caption: ''
  focal_point: ''
---

I needed to make the values in a column consistent and was struggling to add in the base R function of ```toupper``` in a dplyr 
pipeline. I found the `str_to_upper(string, locale = "en")` function in the [stringr package](https://stringr.tidyverse.org/reference/case.html) and made it work. 


