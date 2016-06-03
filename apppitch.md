---
title       : Pitch of eGFR app 
subtitle    : Comparison of calculations via old and new formula
author      : PAC
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Why is this important 

1. Clinicians want to know the difference between new and old formula
2. The new formula works better at the extreme values
3. It is a part of my project

--- .class #id 

## How is it build

### In the sidebarpanel there are two sections.

1. Documentation  
        Documenting what to do to make the app run.
2. Input boxes  
        Two numeric input boxes with default values and limits  
        One select input box with default and two options  
        One action button -to send values to the plot  

### In the mainpanel there are also two sections.

1. Showing the output of the two calculations
2. Plot displaying the current values -after pressing the action button
  
The next slide show the formulas used for calculation.

The last slide show evaluation of the formulas.

---

## Formulas for calculation


```r
NewEgfr<-function(increa,insex,inage){
        if (insex=="Female" & increa>62)
                return(round(144*(increa/(0.7*88.4))^-1.209*0.993^inage))
        if(insex=="Female" & increa<63)
                return(round(144*(increa/(0.7*88.4))^-0.329*0.993^inage))
        if (insex=="Male" & increa>80)
                return(round(141*(increa/(0.9*88.4))^-1.209*0.993^inage))
        if (insex=="Male" & increa<81)
                return(round(141*(increa/(0.9*88.4))^-0.411*0.993^inage))
}
OldEgfr<-function(increa,insex,inage){
        if (insex=="Male")
                return(round(175*(increa/(88.4))^-1.154*inage^-0.203))
        if(insex=="Female")
                return(round(175*(increa/(88.4))^-1.154*inage^-0.203*0.742))
}
```

---

### Evaluation of formulas with two examples

```r
NewEgfr(60,"Male",80)
```

```
## [1] 90
```

```r
OldEgfr(60,"Male",80)
```

```
## [1] 112
```

```r
NewEgfr(4,"Male",80)
```

```
## [1] 275
```

```r
OldEgfr(4,"Male",80) #end
```

```
## [1] 2559
```
