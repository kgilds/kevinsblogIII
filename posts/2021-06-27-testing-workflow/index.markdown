---
title: Testing Workflow
author: Kevin
date: '2021-06-27'
slug: []
categories:
  - R
tags: ["pointblank", "testthat", "git"]
image:
  caption: ''
  focal_point: ''
---


> Formalize your test

# Introduction

Working on a report I realized a function was not working as expected. It was an easy fix; I forgot to rename a variable. 😭

When I was about to make the git commit, I recalled it is good practice to also create and commit a test file associated with the change. 🤗

Using testthat is challenging for me but fortunately the [`pointblank`](https://rich-iannone.github.io/pointblank/reference/write_testthat_file.html) package makes it easier. With pointblank you can create an agent, and use that to write to testthat script. There is one step that trips me up so I am going to walk through it.

### Load the libraries



```r
library(pointblank)
library(tidyverse)
```




> When I use the `create_agent` function--I need to use the `read_fn argument`.



```r
head(small_table)
```



```
## # A tibble: 6 x 8
##   date_time           date           a b             c      d e     f    
##   <dttm>              <date>     <int> <chr>     <dbl>  <dbl> <lgl> <chr>
## 1 2016-01-04 11:00:00 2016-01-04     2 1-bcd-345     3  3423. TRUE  high 
## 2 2016-01-04 00:32:00 2016-01-04     3 5-egh-163     8 10000. TRUE  low  
## 3 2016-01-05 13:32:00 2016-01-05     6 8-kdg-938     3  2343. TRUE  high 
## 4 2016-01-06 17:23:00 2016-01-06     2 5-jdo-903    NA  3892. FALSE mid  
## 5 2016-01-09 12:36:00 2016-01-09     8 3-ldm-038     7   284. TRUE  low  
## 6 2016-01-11 06:15:00 2016-01-11     4 2-dhe-923     4  3291. TRUE  mid
```





```r
# A pointblank `agent` object is now
# created and the `al` object is provided
# to the agent; the static thresholds
# provided by `al` make reports a bit
# more useful after interrogation
agent <- 
  create_agent(
    read_fn = ~ small_table,
    label = "An example."
  
  ) %>%
  col_exists(vars(date, date_time)) %>%
  col_vals_regex(
    vars(b),
    regex = "[0-9]-[a-z]{3}-[0-9]{3}"
  ) %>%
  col_vals_gt(vars(d), value = 100) %>%
  col_vals_lte(vars(c), value = 5) %>%
  interrogate()

# This agent and all of the checks can
# be transformed into a testthat file
# with `write_testthat_file()`; the `stop`
# thresholds will be ported over
```





```r
write_testthat_file(
  agent = agent,
  name = "small_table",
  path = "."
)
```



This script above will create a testthat script in your testthat directory. If you are testing a function output, I suggest using the same name of the file where the function is located. You may need to modify the script such as adding the library calls and setting up the data.

When you want a report of the results of your testthat tests, the [`covrpage`](https://github.com/yonicd/covrpage) is a great tool when you want run all your tests and generate a report of the output--I love the time stamp on the report and it works hand in hand with the [`covr`](https://github.com/r-lib/covr)

# Conclusion

The `pointblank` packages has many other great features and makes testing approachable.
