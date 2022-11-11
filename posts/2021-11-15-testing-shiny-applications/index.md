---
title: Testing Shiny Applications
author: Kevin
date: '2021-11-15'
slug: []
categories:
  - R
tags: [shiny, testing, til]
---

At some point last year, I jumped into unit testing with the help of the [pointblank package](https://rich-iannone.github.io/pointblank/). Since then, I have improved my ability to work with the [testthat package](https://testthat.r-lib.org/).

However, I could not get a good grasp of unit tests for a shiny application. I was reading the [*Mastering Shiny Book*](https://mastering-shiny.org/) and still could not grasp it. I did find this [article](https://shiny.rstudio.com/articles/testing-overview.html) that got me going. The exercise of running the script below and playing with the application and tests helped me understand the testing process for Shiny Applications.

``` r
shinyAppTemplate("myapp")
```

I was able to implement a couple of simple automated tests in my own shiny applications. The only roadblock I ran into is that I had not exported my modules and the testing engine could not find the server I was testing.

I start with simple tests and work towards more complexity. My favorite basic tests is to count the number of columns. Here is the form:

``` r
testServer(mod_home_server, {

expect_equal(ncol(sites()), 4)

})

testServer(mod_home_server, {

expect_equal(colnames(program()), c("time", "site", "grant", "id_code"))

})
```
