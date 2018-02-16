---
title       : Quantiles, Percentiles, and Boxplots
description : Quantile-Quantile Plots, Percentiles, Boxplots, Distribution of Female Heights

--- type:NormalExercise lang:r xp:100 skills:1 key:56141be397
## Quantiles

Define variables containing the heights of males and females like this.

How many measurements do we have for each?

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
data(heights)
male <- heights$height[heights$sex=="Male"]
female <- heights$height[heights$sex=="Female"]
```

*** =sample_code
```{r}
library(dslabs)
data(heights)
male <- heights$height[heights$sex=="Male"]
female <- heights$height[heights$sex=="Female"]
```

*** =solution
```{r}
length(male)
length(female)
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:b66abf907d
## Quantiles

Suppose we can't make a plot and want to compare the distributions side by side. We can't just list all the numbers. Instead we will look at the percentiles. Create a five row table showing `female_percentiles` and `male_percentiles` with the 10th, 30th, 50th, ..., 90th percentiles for each sex. Then create a data frame with these two as columns.


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
data(heights)
male <- heights$height[heights$sex=="Male"]
female <- heights$height[heights$sex=="Female"]
```

*** =sample_code
```{r}
library(dslabs)
data(heights)
male <- heights$height[heights$sex=="Male"]
female <- heights$height[heights$sex=="Female"]
```

*** =solution
```{r}
female_percentiles <- quantile(female, seq(0.1, 0.9, 0.2))
male_percentiles <- quantile(male, seq(0.1, 0.9, 0.2))
data.frame(female_percentiles, male_percentiles)    
```

*** =sct
```{r}

```
