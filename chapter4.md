---
title       : Customizing plots
description : Layers, Tinkering, Scales, Labels, and Colors, Add-on Packages, Other Examples

--- type:PureMultipleChoiceExercise xp:50 skills:1 key:40d2cf051e
## Customizing plots - Pie charts
    

*** =possible_answers
A. When we want to display percentages.
B. When `ggplot2` is not available.
C. When I am in a bakery.
D. Never. Barplots and tables are always better.

*** =hint

*** =feedbacks


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c2c488beec
## Customizing plots - What's wrong?

A. The values are wrong. The final vote was 306 to 232.
B. The axis does not start at 0. Judging by the length, it appears Trump received 3 times as many votes when in fact it was about 30% more. 
C. The colors should be the same.
D. Percentages should be shown as a pie chart.

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
data(us_contagious_diseases)
library(tidyverse)
ds_theme_set()

data.frame(candidate=c("Clinton","Trump"), electoral_votes = c(232, 306)) %>%
  ggplot(aes(candidate, electoral_votes)) +
  geom_bar(stat = "identity", width=0.5, color =1, fill = c("Blue","Red")) +
 coord_cartesian(ylim=c(200,310)) +
  ylab("Electoral Votes") +
  xlab("") +
  ggtitle("Result of Presidential Election 2016")
```

*** =sct
```{r}

```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ed1bcbbf11
## Customizing plots - What's wrong 2?

Take a look at the following two plots. They show the same information: 1928 rates of Measles across the 50 states.

Which plot is easier to read if you are interested in determining which are the best and worst states in terms of rates and why?

A. They provide the same information so they are both equally as good.
B. The plot on the right is better because it orders the states alphabetically.
C. The plot on the right is better because alphabetical order has nothing to do with the disease and by ordering according to actual rate, we quickly see the states with most and least rates.
D. Both plots should be a pie chart.

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
library(tidyverse)
library(gridExtra)
data(us_contagious_diseases)

p1 <- us_contagious_diseases %>% 
  filter(year == 1928 & disease=="Measles" & count>0 & !is.na(population)) %>% 
  mutate(rate = count / population * 10000 * 52 / weeks_reporting) %>%
  ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() +
  xlab("")
p2 <- us_contagious_diseases %>% 
  filter(year == 1928 & disease=="Measles" & count>0 & !is.na(population)) %>% 
  mutate(rate = count / population * 10000*52 / weeks_reporting) %>%
  mutate(state = reorder(state, rate)) %>%
  ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() +
  xlab("")
grid.arrange(p1, p2, ncol = 2)
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:fde8033e56
## Customizing plots - watch and learn

To make the plot on the left, we have to reorder the levels of the states' variables.


*** =instructions
Redefine the `state` object so that the levels are re-ordered. Print the new object `state` and its levels so you can see that the vector is not re-ordered by the levels.

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
library(tidyverse)
library(gridExtra)
data(us_contagious_diseases)
dat <- us_contagious_diseases %>%  
      filter(year == 1967 & disease=="Measles" & !is.na(population)) %>%
      mutate(rate = count / population * 10000 * 52 / weeks_reporting)
dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() 

state <- dat$state
rate <- dat$count/dat$population*10000*52/dat$weeks_reporting
```

*** =sample_code
```{r}
library(dslabs)
library(tidyverse)
library(gridExtra)
data(us_contagious_diseases)
dat <- us_contagious_diseases %>%  
      filter(year == 1967 & disease=="Measles" & !is.na(population)) %>%
      mutate(rate = count / population * 10000 * 52 / weeks_reporting)
dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() 

state <- dat$state
rate <- dat$count/dat$population*10000*52/dat$weeks_reporting
```

*** =solution
```{r}
library(dslabs)
library(tidyverse)
library(gridExtra)
data(us_contagious_diseases)
dat <- us_contagious_diseases %>%  
      filter(year == 1967 & disease=="Measles" & !is.na(population)) %>%
      mutate(rate = count / population * 10000 * 52 / weeks_reporting)
dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() 

state <- dat$state
rate <- dat$count/dat$population*10000*52/dat$weeks_reporting

state <- reorder(state, rate)
print(state)
levels(state)
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:c63feefa1a
## Customizing plots - redefining


*** =instructions
Now with one line of code, define the `dat` table as done above, but change the use mutate to create a rate variable and reorder state variable so that the levels are reordered by this variable. Then make a bar plot using the code above, but for this new dat.


*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
library(tidyverse)
library(gridExtra)
data(us_contagious_diseases)
dat <- us_contagious_diseases %>%  
      filter(year == 1967 & disease=="Measles" & !is.na(population)) %>%
      mutate(rate = count / population * 10000 * 52 / weeks_reporting)
dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() 

dat <- us_contagious_diseases %>%  filter(year == 1967 & disease=="Measles" & count>0 & !is.na(population)) %>%
  mutate(res = dat$count/dat$population*10000*52/dat$weeks_reporting) %>%
  mutate(state = reorder(state, res))

dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip()
```

*** =sample_code
```{r}
library(dslabs)
library(tidyverse)
library(gridExtra)
data(us_contagious_diseases)
dat <- us_contagious_diseases %>%  
      filter(year == 1967 & disease=="Measles" & !is.na(population)) %>%
      mutate(rate = count / population * 10000 * 52 / weeks_reporting)
dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() 

```

*** =solution
```{r}
library(dslabs)
library(tidyverse)
library(gridExtra)
data(us_contagious_diseases)
dat <- us_contagious_diseases %>%  
      filter(year == 1967 & disease=="Measles" & !is.na(population)) %>%
      mutate(rate = count / population * 10000 * 52 / weeks_reporting)
dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip() 

dat <- us_contagious_diseases %>%  filter(year == 1967 & disease=="Measles" & count>0 & !is.na(population)) %>%
  mutate(res = dat$count/dat$population*10000*52/dat$weeks_reporting) %>%
  mutate(state = reorder(state, res))

dat %>% ggplot(aes(state, rate)) +
  geom_bar(stat="identity") +
  coord_flip()
```

*** =sct
```{r}

```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:688855b651
## Customizing plots - Final

Say we are interested in comparing gun homicide rates across regions of the US. We see this plot:

```r
library(dslabs)
data("murders")
murders %>% mutate(rate = total/population*100000) %>%
  group_by(region) %>%
  summarize(avg = mean(rate)) %>%
  mutate(region = factor(region)) %>%
  ggplot(aes(region, avg)) +
  geom_bar(stat="identity") +
  ylab("Murder Rate Average")
```
and decide to move to a state in the western region. What is the main problem with this interpretaion?

A. The categories are ordered alphabetically.
B. The graph does not show standard errors.
C. It does not show all the data. We do not see the variability within a region and it's possible that the safest states are not in the West.
D. The Northeast has the lowest average.

*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(dslabs)
data("murders")
murders %>% mutate(rate = total/population*100000) %>%
  group_by(region) %>%
  summarize(avg = mean(rate)) %>%
  mutate(region = factor(region)) %>%
  ggplot(aes(region, avg)) +
  geom_bar(stat="identity") +
  ylab("Murder Rate Average")
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:fd7566b82b
## Boxplots


Make a box plot of the murder rates by region, showing all the points and ordering the regions by their median rate.



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
data("murders")
murders %>% mutate(rate = total/population*100000) 
```

*** =sample_code
```{r}
data("murders")
```

*** =solution
```{r}
data("murders")
murders %>% mutate(rate = total/population*100000) %>%
  mutate(region=reorder(region, rate, FUN=median)) %>%
  ggplot(aes(region, rate)) +
  geom_boxplot() +
  geom_point()
```

*** =sct
```{r}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:d35b68763d
## Boxplots - 2

The plots below shows the for three continuous variables. 

The line $x=2$ appears to separate the points. But it is actually not the case, which we can see by plotting the data in a couple of two dimensinal points.
  

Why is this happening?

A. Humans are not good at reading pseudo 3D plots.
B. There must be an error in the code
C. The colors confuse us.
D. Scatter plots should not be used to compare two variables when we have access to 3.


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(scatterplot3d)
library(RColorBrewer)
rafalib::mypar(1,1)
set.seed(1)
n <- 25
group <- rep(1,n)
group[1:(round(n/2))] <- 2
x <- rnorm(n, group, .33)
y <- rnorm(n, group, .33)
z <- rnorm(n)

scatterplot3d(x,y,z, color = group, pch=16)
abline(v=4, col=3)


mypar(1,2)
plot(x,y, col=group, pch =16)
abline(v=2, col=3)
plot(x,z,col=group, pch=16)
abline(v=2, col=3)
```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
