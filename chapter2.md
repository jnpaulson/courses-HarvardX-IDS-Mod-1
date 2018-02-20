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
library(dslabs)
data(heights)
male <- heights$height[heights$sex=="Male"]
female <- heights$height[heights$sex=="Female"]

length(male)
length(female)
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:b66abf907d
## Quantiles 2

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
library(dslabs)
data(heights)
male <- heights$height[heights$sex=="Male"]
female <- heights$height[heights$sex=="Female"]

female_percentiles <- quantile(female, seq(0.1, 0.9, 0.2))
male_percentiles <- quantile(male, seq(0.1, 0.9, 0.2))
data.frame(female_percentiles, male_percentiles)    
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:1305c717d1
## Quantiles 3

Study the following boxplots showing us populations sizes by country:

Which continent has the country with the biggest population size?


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =sample_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =solution
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
cat("Asia")
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:473fe736e1
## Quantiles 4

What continent has the largest median population size?

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =solution
```{r}
cat("Africa")
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:2481169bf1
## Quantiles 5

What is the median population size for Africa to the nearest million? 

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =sample_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =solution
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")

cat("10-15 is acceptable") 
##we can check with     
##round(median(tab$population[tab$continent=="Africa"]/10^6,),-1)
```

*** =sct
```{r}

```
--- type:NormalExercise lang:r xp:100 skills:1 key:242558837d
## Quantiles 6

What proportion of countries in Europe have populations below 14 million?

  A. 0.99
  B. 0.75
  C. 0.50
  D. 0.25
  
ANSWER IS B


*** =instructions

*** =hint
Use the `r cat` function to report either 'A','B','C', or 'D'.

*** =pre_exercise_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =sample_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =solution
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")

cat("B")
```

*** =sct
```{r}

```
--- type:NormalExercise lang:r xp:100 skills:1 key:0ff5833c3f
## Quantiles 7

If we use a log transformation, which continent shown below has the largest interquartile range?


*** =instructions

*** =hint
Use the `r cat` function to report the continent name.

*** =pre_exercise_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =sample_code
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")
```

*** =solution
```{r}
library(tidyverse)
library(dslabs)
ds_theme_set()
data(gapminder)
tab <- gapminder %>% filter(year == 2010) %>% group_by(continent) %>% select(continent, population)  
tab %>% ggplot(aes(x=continent, y=population/10^6)) + geom_boxplot() + scale_y_continuous(trans = "log10", breaks = c(1,10,100,1000)) + ylab("Population in millions")

cat("Americas")
```

*** =sct
```{r}

```
