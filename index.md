---
title       : DevDataProd Shiny Application
subtitle    : Reproducible Pitch Presentation
author      : Datarch
job         : Developing Data Product Course Participant
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Shiny Application and Reproducible Pitch

This presentation is created in scope of the Developing Data Product Course Project in [Coursera](https://www.coursera.org/course/devdataprod) to provide a quick reproducible presentation on the created shiny application, also including some R expressions.

The **DevDataProd** Shiny Application is available on [shinyapps.io](https://datarched.shinyapps.io/DevDataProd), the application R codes (ui.R and server.R) are published on [GitHub](https://github.com/Datarch/DevDataProd).

The application calculates the Body Composition using a statistical model published by:

Paul Deurenberg, Jan A. Weststrate and Jaap C. Seidell (1991). Body mass index as a measure of body fatness: age- and sex-specific prediction formulas. British Journal of Nutrition, 65, pp 105-114. doi:10.1079/BJN19910073.

The abstract available [here](http://dx.doi.org/10.1079/BJN19910073).

---

## Body mass index as a measure of body fatness

The relationship between densitometrically-determined body fat percentage (BF%) and BMI, taking age and sex (males =1, females = 0) into account, was analysed on the collected data.

The created statistical model based on a data set contains 1229 subjects, 521 males and 708 females, with a wide range in body mass index (BMI; 13.9-40.9 kg/m2), and an age range of 7-83 years, body composition was determined by densitometry and anthropometry.

For children aged 15 years and younger, the relationship differed from that in adults, due to the height-related increase in BMI in children.

---

## How to use the DevDataProd Shiny Application

First the input data need to be entered or selected:
* Weight in kilogram
* Height in meter
* Age in years
* Sex: Male or Female

Based on the input data, after pushing Submit button the application:
* calculates the body mass index (BMI)
* classify body fatness (underweight / normal / overweight / obese)
* calculates the body fat persentage

---

## Simulation Experiment


```r
# BMI and BF functions are used for calculation
BMI <- function(weight, height) round(weight / height^2, 2)
BF <- function(weight, height, sex, age) {
        if (sex == "Male") s <- 1
        else s <-0
        if (age > 15) round(1.2 * (weight / height^2) + 0.23 * age - 10.8 * s - 5.4, 2)
        else round(1.51 * (weight / height^2) - 0.70 * age - 3.6 * s + 1.4, 2)
        }
# Calculate BMI and BF%:
BMI(62, 1.65); BF(62, 1.65, "Female", 38)
```

```
## [1] 22.77
```

```
## [1] 30.67
```


