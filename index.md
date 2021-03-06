---
title       : "Analyzing MPG Performance vs Automobile Design"
subtitle    : Developing Data Products Project Part 2
author      : "paperless247"
job         : Reproducible Pitch Presentation
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Dataset

`mtcars` dataset is used to analyze automobile performance and create ShinyApp (for Part 1)

### Motor Trend mtcars Dataset

> The mtcars data was extracted from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance.


```r
library(datasets)
head(mtcars, 5)
```

```
##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
```

--- .class #id 

## Dataset Description

**Dataset has 32 observations on 11 variables**

| Index | Variable | Description |
------- | ----- | ------ |
| 1 | mpg | Miles/(US) gallon |
| 2  | cyl | Number of cylinders |
| 3  | disp | Displacement (cu.in.) |
| 4  | hp | Gross horsepower |
| 5	| drat | Rear axle ratio |
| 6	| wt | Weight (lb/1000) |
| 7	| qsec | 1/4 mile time |
| 8	| vs | V/S |
| 9	| am | Transmission (0 = automatic, 1 = manual) |
| 10	| gear | Number of forward gears |
| 11	| carb | Number of carburetors |

--- .class #id 

## Analysis

Then main script:

```r
  formulaTextPoint <- reactive({
    paste("mpg ~", "as.integer(", input$variable, ")")  })
  
  fit <- reactive({
    lm(as.formula(formulaTextPoint()), data=mpgData)  })
  ...
  output$fit <- renderPrint({
    summary(fit()) })
  
  output$mpgPlot <- renderPlot({
    with(mpgData, {
      plot(as.formula(formulaTextPoint()))
      abline(fit(), col=2)
    })  })
```

---

## Shiny Application and Github Repository

### Shiny Application

URL: *https://etran.shinyapps.io/test/*

### Github Repository

URL: *https://github.com/paperless247/DS9_Proj_1*

Thank you for reading and grading!
