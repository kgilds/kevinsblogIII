---
title: TIL
author: Kevin
date: '2021-12-19'
slug: []
categories:
  - R
tags: [dplyr, functions]
image:
  caption: ''
  focal_point: ''
---

I wrote some functions and  scripts had to complete troubleshooting to make them work

I am not sure why I could not recall how to filter multiple values under on variable but here we are! The `slice` function is also becoming one of my favorite tools. 

```r
pre_numeric <- pre_summary %>%
  dplyr::filter(skim_type == "numeric") %>%
  dplyr::slice_tail(n = 6) %>%
  dplyr::filter(skim_variable == "var2_avg" |
                  skim_variable == "var1_avg" |
                  skim_variable == "var3_avg") 
                  
```

In this function,  I have to make sure that NA values are converted to zero before I can determine success or failure. The `df` has to be called first and then start the new dplyr statement.  

```r
get_var_score <- function(df){
  
    df <- dplyr::mutate(df, var_adjusted = 4 - sc1) 
    df <- dplyr::mutate(df, var_avg = sc0 / var_adjusted) 
    df$var_avg <- tidyr::replace_na(df$var_avg, 0)
    df 
    dplyr::mutate(df, var_success = if_else(var_avg >= 4.45, TRUE, FALSE))
    
    
}
```



Here I needed to actually filter `na`values in this column to see troubled records.  
```r
issue_13 <- survey %>%
  dplyr::filter(is.na(initials_1)) 
  
```

