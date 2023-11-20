---
title: "r_you_with_me"
author: "Imen Belhadj"
date: "2023-11-20"
output: 
  html_document: 
    keep_md: yes
---



## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


To create a code chunk, press the green '+C' button, or ctrl+alt+i

R can calculate arithmetic expressions.



5 different data classes in R: numerics, integers, characters, logicals(like Booleans), complex(imaginary)

```r
my_numeric <- 42
my_integer <- 2L #adding an L automatically denotes an integer
my_character <- "universe"
my_logical <- FALSE
my_complex <- 2+4i
```

Can concatenate arithmetic expressions to an vector.


Concatenate numbers and assign them to a vector.

```r
#list of some California interstate freeways
```

Many vectors "stacked together" is a data matrix.

```r
Philosophers_Stone <- c(317.5, 657.1)
Chamber_of_Secrets <- c(261.9, 616.9)
Prisoner_of_Azkaban <- c(249.5, 547.1)
Goblet_of_Fire <- c(290.0, 606.8)
Order_of_the_Phoenix <- c(292.0, 647.8)
Half_Blood_Prince <- c(301.9, 632.4)
Deathly_Hallows_1 <- c(295.9, 664.3)
Deathly_Hallows_2 <- c(381.0, 960.5)
```
These are all individual vectors of the profit in millions at the box office in the US and globally. 
Lets concatenate all of them.

```r
box_office <- c(Philosophers_Stone, Chamber_of_Secrets, Prisoner_of_Azkaban, Goblet_of_Fire, Order_of_the_Phoenix, Half_Blood_Prince, Deathly_Hallows_1, Deathly_Hallows_2)
box_office
```

```
##  [1] 317.5 657.1 261.9 616.9 249.5 547.1 290.0 606.8 292.0 647.8 301.9 632.4
## [13] 295.9 664.3 381.0 960.5
```


R can run statistical operations.

```r
#each calculation will appear in order
#mean (ca_interstates)
#sd(ca_interstates)
#median (ca_interstates)
#quantile(ca_interstates)
#range(ca_interstates)
#sum(ca_interstates)
#min(ca_interstates)
#max(ca_interstates)
#and so many more!
```
Load the tidyverse (after downloading in console)
CAUTION: Loading more than once can cause problems! comment this line out after first run once you're ready to knit.

```r
library(tidyverse)
```

```
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.4     ✔ readr     2.1.4
## ✔ forcats   1.0.0     ✔ stringr   1.5.1
## ✔ ggplot2   3.4.4     ✔ tibble    3.2.1
## ✔ lubridate 1.9.3     ✔ tidyr     1.3.0
## ✔ purrr     1.0.2     
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```
Let's input some data! We'll use a .csv


```r
#Use summary() to see general statistical information about a data set.
```

```r
#glimpse(ca_colleges)
```

```r
#Use view() to get an Excel-looking spreadsheet.
```


```r
# names() and colnames() both output column names!
```
head() and foot() functions show top few and bottom few rows


```r
  #can also select number of rows you want to show for this, here I picked 2
```

dplyr package 
Part of the tidyverse, `dplyr is used to transform data frames by extracting, rearranging, and summarizing data such that they are focused on a question of interest. This is very helpful,  especially when wrangling large data, and makes dplyr one of most frequently used packages in the tidyverse. The two functions we will use most are `select()` and `filter()`.  

```r
#Use select() to only view specific columns in names(), choose as many as you want.
```
Let's assign these two columns to their own object, college_stats.


You can select several columns adjacent to each other.

Other ways to use select():


```r
#select all except specified column names
```

```r
#select columns based on starting letter(s)
```

```r
#select columns based on ending letter(s)
```
You can also rename your column names with rename().

```r
#this is one but you can change as many as you want, just seperate with commas 
#check your work
```

Now for the filter() function. `filter()` allows us to extract data that meet specific criteria within a variable. Let's use this to find UC Davis.

Try to find another CA college of your choice.


`filter()` allows all of the expected operators; i.e. >, >=, <, <=, != (not equal), and == (equal).

What colleges have an admission rate between 10% and 50%?


How about 100%? 


You can also specify a tolerance range (or range of allowed error).

```r
#here we are looking for colleges with a 30% exceptance rate, give or take 1%
```
You can also use filter() to look at multiple parameters at once. 

```r
#here we are looking for colleges in San Francisco with a cost 4 attendance >= $20000
```
Watch out! There's quite a difference between | and &. | is 'or'.

```r
#here we are looking for colleges in San Francisco or colleges with a cost 4 attendance >= $20000
```

That's enough for today...let's knit and save.

