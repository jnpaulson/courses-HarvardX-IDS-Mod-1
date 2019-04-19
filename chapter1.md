---
title: 'Introduction to Distributions'
description: 'In this course we introduce you to the basics of data visualization and distributions.'
free_preview: true
---

## Normal Distributions - Averages

```yaml
type: NormalExercise
key: 3cceaa1c24
lang: r
xp: 100
skills: 1
```

What proportion of the data is between 69 and 72 inches (taller than 69 but shorter or equal to 72)? Hint: a logical operator and `mean`.

`@instructions`
1. Load the height data set and create a vector `x` with just the male heights:

`@hint`


`@pre_exercise_code`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]
```

`@sample_code`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]
```

`@solution`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]

mean(x>69 & x<=71)
```

`@sct`
```{r}

```

---

## Normal Distributions - Approximations

```yaml
type: NormalExercise
key: 52231e7964
lang: r
xp: 100
skills: 1
```

Suppose all you know about the data is the average and the standard deviation. Use the normal approximation to estimate the proportion you just calculated.

`@instructions`


`@hint`
Hint: Start by computing the average and standard deviation. Then use the `pnorm` function to predict the proportions.

`@pre_exercise_code`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]
```

`@sample_code`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]
```

`@solution`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]

avg <- mean(x)
stdev <- sd(x)
pnorm(71, avg, stdev) - pnorm(69, avg, stdev)
```

`@sct`
```{r}

```

---

## Normal Distributions - Actual vs. Approximation

```yaml
type: NormalExercise
key: 2c9c2604b9
lang: r
xp: 100
skills: 1
```

Notice that the approximation calculated in question 2 is very close to the exact calculation in the first question. Now perform the same task for more extreme values. Compare the exact calculation and the normal approximation for the interval (79,81). How many times bigger is the actual proportion than the approximation?

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]
```

`@sample_code`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]
```

`@solution`
```{r}
library(dslabs)
data(heights)
x <- heights$height[heights$sex=="Male"]

exact <- mean(x>79 & x<=81)
approx <- pnorm(81, avg, stdev) - pnorm(79, avg, stdev)
exact/approx
```

`@sct`
```{r}

```

---

## Normal Distributions - Seven footers

```yaml
type: NormalExercise
key: 4ef61be5bd
lang: r
xp: 100
skills: 1
```

Approximate the distribution of adult men in the world as normally distributed with an average of 69 inches and a standard deviation of 3 inches. Using this approximation, estimate the proportion of adult men that are 7 foot tall or taller, referred to as _seven footers_.

`@instructions`


`@hint`
Hint: use the `pnorm` function.

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}
1 - pnorm(7*12, 68, 3)
```

`@sct`
```{r}

```

---

## Normal Distributions - Proportion

```yaml
type: NormalExercise
key: cbf2bae861
lang: r
xp: 100
skills: 1
```

There are about 1 billion men between the ages of 18 and 40 in the world. Use your answer to the previous question to estimate how many of these men (18-40 year olds) are seven feet tall or taller in the world?

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}
p <- 1 - pnorm(7*12, 68, 3)
round(p * 1.5*10^9)
```

`@sct`
```{r}

```

---

## Normal Distributions - Ranges

```yaml
type: NormalExercise
key: fb137e234c
lang: r
xp: 100
skills: 1
```

There are about 10 National Basketball Association (NBA) players that are 7 feet tall or higher. Using the answer to the previous two questions, what proportion of the world's 18 to 40 year old seven footers are in the NBA?

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}
p <- 1 - pnorm(7*12, 68, 3)
N <- round(p * 1.5*10^9)
10/N
```

`@sct`
```{r}

```

---

## Normal Distributions - Review

```yaml
type: NormalExercise
key: 0d53db0266
lang: r
xp: 100
skills: 1
```

Repeat the calculations performed in the previous question for Lebron James' height: 6 feet 8 inches. There are about 150 players that are that tall.

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}

```

`@solution`
```{r}
p <- 1 - pnorm(6*12 + 8, 68, 3)
N <- round(p * 1.5*10^9)
150/N
```

`@sct`
```{r}

```

---

## Normal Distributions - Overview

```yaml
type: MultipleChoiceExercise
key: 83e1526689
lang: r
xp: 50
skills: 1
```

In answering the previous questions, we found that it is not at all rare for a seven footer to become an NBA player. What would be a fair critique of our calculations:

    A. Practice and talent are what make a great basketball player, not height.
    B. The normal approximation is not appropriate for heights.
    C. As seen in question 3, the normal approximation tends to underestimate the extreme values. It's possible that there are more seven footers than we predicted.
    D. As seen in question 3, the normal approximation tends to overestimate the extreme values. It's possible that there are less seven footers than we predicted.
    
(C) is the answer

`@possible_answers`


`@hint`


`@pre_exercise_code`
```{r}

```

`@sct`
```{r}

```
