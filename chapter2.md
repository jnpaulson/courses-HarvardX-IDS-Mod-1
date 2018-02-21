---
title       : Data Types and Quantiles, Percentiles, and Boxplots
description : Quantile-Quantile Plots, Percentiles, Boxplots, Distribution of Female Heights




--- type:NormalExercise lang:r xp:100 skills:1 key:e70afa5dad
## Variable names

Variable names can be useful for remembering as well as referenced from data frames.

Load the motivating data example using the code:

```{r}
library(dslabs)
data(heights)
```

*** =instructions

What are the two variable names within the `heights` dataset?

*** =hint
Use the `names` function.

*** =pre_exercise_code
```{r}
library(dslabs)
data(heights)
```

*** =sample_code
```{r}

```

*** =solution
```{r}
names(heights)
```

*** =sct
```{r}
test_error()
test_output_contains("names(heights)", incorrect_msg = "Are you calling the function on the correct dataset?")
test_function("names", incorrect_msg = "You should be using a specific function to grab the names of the heights dataset")
success_msg("Nice work!")
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:e6b1d336ad
## Variable type

The type of the first variable is from the previous exercise?

Rerun the code if you need help remembering:
```{r}
library(dslabs)
data(heights)
names(heights)
```

*** =instructions
- Continuous
- Categorical
- Ordinal
- None of the above

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
data(heights)
names(heights)
```

*** =sct
```{r}
msg1 = "Incorrect. Looking at the correct variable?"
msg2 = "Correct! Good Job"
msg3 = "Incorrect. Try again!"
msg4 = "Incorrect. It is one of the above"
test_mc(2, c(msg1, msg2, msg3, msg4))
```
--- type:NormalExercise lang:r xp:100 skills:1 key:7ea8b2ef03
## Numerical values

Use the `unique` and `length` function in R to determine how many unique heights were reported.

*** =instructions
Report the number of unique heights.

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
data(heights)
```

*** =sample_code
```{r}
library(dslabs)
data(heights)
```

*** =solution
```{r}
library(dslabs)
data(heights)
length(unique(heights$height))
```

*** =sct
```{r}
test_error()
test_output_contains("139", incorrect_msg = "Are you calling the function on the correct dataset?")
test_function("unique", incorrect_msg = "You should be using unique for this exercise")
test_function("length", incorrect_msg = "You should be using length for this exercise")
success_msg("Nice work!")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:2047247be5
## Tables

Use the `table` function to create an object, call it `tab`, that tells how often each value of height was reported.


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
data(heights)
```

*** =sample_code
```{r}
library(dslabs)
data(heights)
```

*** =solution
```{r}
library(dslabs)
data(heights)
tab <- table(heights$height)
```

*** =sct
```{r}
test_error()
test_object("tab", incorrect_msg = "Are you calling the `table` function on the correct dataset?")
test_function("table", incorrect_msg = "You should be using table for this exercise")
success_msg("Nice work!")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:89f473fdd1
## Indicator variables

How many values were reported exactly once?


*** =instructions
Report the sum of values reported exactly once.

*** =hint
Use the function `sum` to count the number of times entries in `tab` are equal to 1.

*** =pre_exercise_code
```{r}
library(dslabs)
data(heights)
tab <- table(heights$height)
```

*** =sample_code
```{r}
library(dslabs)
data(heights)
```

*** =solution
```{r}
library(dslabs)
data(heights)
tab <- table(heights$height)
sum(tab==1)
```

*** =sct
```{r}
test_error()
test_output_contains("sum(tab==1)", incorrect_msg = "Are you calling the `sum` function on the table you created?")
test_function("sum", incorrect_msg = "You should be using `sum` function for this exercise")
success_msg("Nice work!")
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ce3b6a5f17
## Data types - heights

Since there are a finite number of reported heights and technically the height can be considered ordinal, which of the following is true:

*** =instructions
- It is more effective to consider heights to be numerical given the number of unique values we observe and even more we can potentially observe.
- It is actually preferable to consider heights ordinal since on a computer there are only a finite number of possibilities
- This is actually a categorical variable: tall, medium or short.
- This is a numerical variable because numbers are used to represent it.

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg1 = "Correct!  Good Job!"
msg2 = "Incorrect. Try again"
msg3 = "Incorrect. Try again"
msg4 = "Incorrect. Try again"
test_mc(1, c(msg1, msg2, msg3, msg4))
```
--- type:NormalExercise lang:r xp:100 skills:1 key:56141be397
## Quantiles

Define variables containing the heights of males and females like this.



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
