---
title       : Fuel Consumption Estimator
subtitle    : MPG Estimator based on transmission type, car weight, HP and number of cylinders
author      : J-G Blouin
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

An application calculating gas consumption per mile is proposed.
The user must select

* Transmission type
* Number of cylinders
* Car weight (in 1000 lbs)
* Horse Power

A confidence interval can be selected, indicating a requested precision.

---
## How it works

Caluculations are based on a linear model approximation relating MPG 
to the selected variables. The model thus built is then used for interpolation.
The Result tab contains 
* the estimated value for MPG called fit 
* the lower bound for the confidence interval, called lwr
* the upper bound for the confidence interval, called upr

The Plot tab contains a representation of the confidence interval.  

The model is given by

```r
fit <- lm(mpg ~ factor(am) + wt + factor(cyl) + hp, data=mtcars)
```

---
## The Data

The data used to define the model comes from the mtcvars data set and looks like


```
##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```
where am is the transmission type:
* 0 for automatic
* 1 for manual

---

## The Model Summarized

The residual standard error is given by

```
## [1] 2.41012
```
The F-statistic is given by

```
##    value    numdf    dendf 
## 33.57121  5.00000 26.00000
```
The multiple R-squared and adjusted R-squared are given respectively by

```
## [1] 0.8658799
```

```
## [1] 0.8400875
```
And, lastly, the p-value is approximately null.
