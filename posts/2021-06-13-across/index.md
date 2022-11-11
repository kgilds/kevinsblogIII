---
title: Across
author: Kevin
date: '2021-06-13'
slug: []
categories:
  - R
tags: ["dplyr", "across", "forcats" ]
image:
  caption: ''
  focal_point: ''
---

> I made that more difficult than it had to be. 




I was working on analyzing twenty plus survey questions and wanted to use the `forcats` function collapse on all of them.  I was desperately trying to combine [`dplyr::across`](https://dplyr.tidyverse.org/reference/across.html) with the [`forcats` function `collapse`](https://forcats.tidyverse.org/reference/fct_collapse.html).




Thankfully, I found this [Stackoverflow Post](https://stackoverflow.com/questions/66142322/fct-collapse-function-to-multiple-columns-at-once)

```
library(dplyr)
library(forcats)
df %>% 
    mutate(across(-pid, ~ fct_collapse(.,
     yes = c('y', 'Y'), no = c('no', 'NO', 'n'))))
     
```

My mistake was that I was trying to close the `across` function paren too soon and hence errors. Here is an example of one way I was doing it wrong.   

```
library(dplyr)
library(forcats)
df %>% 
    mutate(across(-pid), ~ fct_collapse(.,
     yes = c('y', 'Y'), no = c('no', 'NO', 'n'))))
     
````


# Conclusion

I am hoping that digging into the reason for this trouble helps me remember for next time. 