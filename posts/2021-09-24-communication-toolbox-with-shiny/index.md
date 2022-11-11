---
title: Communication Toolbox with Shiny
author: Kevin
date: '2021-09-24'
slug: []
categories:
  - R
tags:
  - Shiny
---

### The Toolbox🧰

Last Wednesday, I presented the *User* *Feedback* chapter from [Mastering Shiny](https://mastering-shiny.org/action-feedback.html) for Cohort 2 of the book club from [r4ds](https://r4ds.github.io/bookclub-mshiny/). My goal was to emphasize that a shiny application is a communication mechanism and that functions such as:

-   Validation

-   Notifications

-   Progress Bars

-   Modal Dialogues

are tools in your toolbox to improve the communication between you and your users.

### Validation

I depend on the validation function in `shiny` to communicate to my users when there is no data entry for a given grant or within a given time frame.

    output$grant_level_tbl <- DT::renderDT({
          tbl <- source_level()
          if(source_level() %>% nrow() < 1) {
            validate("Sorry, no data available") ##the order of this matters
          }
          tbl <- outcome_tbl(tbl) %>%
            janitor::adorn_ns() %>%
          DT::datatable(tbl, rownames = FALSE,
                        extensions = "Buttons",
                        options = list(
                          dom = 'tB',
                          buttons = c('copy', 'print', 'csv')
                        ))
        })

The source_level() is reactive data and given input there may be hundreds of data points or none. My validation line states if the reactive value has less than 1 row the following message is displayed

> *Sorry, no data available*.

This communicates to the program manager that surveys have not been entered yet. Most likely this is expected, but the message communicates that there is no data here to display.

The alternative to a validation statement is a blank graph canvas and a ugly error message with table the output.

### Conclusion

I was thinking of the validation function in terms of a practical tool but I see the importance of it as a communication tool as well. What I enjoy most about participating in the book club, is picking up detail and the opportunity for reflection.
