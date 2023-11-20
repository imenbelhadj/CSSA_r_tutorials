---
title: "my_first_rstudio"
author: "Imen Belhadj"
date: "2023-11-20"
output: 
  html_document: 
    keep_md: yes
---



## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
---
title: "first_rstudio"

To create a code chunk, press the green '+C' button, or ctrl+alt+i

R can calculate arithmetic expressions.

```r
5 + 3 * 2
```

```
## [1] 11
```

```r
3 + 5 - 7
```

```
## [1] 1
```

```r
8 / 2 ** 2  #exponential
```

```
## [1] 2
```

```r
55 %% 11    #modulus
```

```
## [1] 0
```

```r
4 %/% 2     #integer division
```

```
## [1] 2
```


5 different data classes in R: numerics, integers, characters, logicals(like Booleans), complex(imaginary)

```r
my_numeric <- 42
my_integer <- 2L #adding an L automatically denotes an integer
my_character <- "universe"
my_logical <- FALSE
my_complex <- 2+4i
```

Can concatenate arithmetic expressions to an vector.

```r
flamingos <- c(5 + 3 * 2, 3 + 5 - 7, 8 / 2 ** 2)
flamingos
```

```
## [1] 11  1  2
```

Concatenate numbers and assign them to a vector.

```r
#list of some California interstate freeways
ca_interstates <- c(5,7,8,9,10,15,40,80,105,110,180,210,280,680)
ca_interstates
```

```
##  [1]   5   7   8   9  10  15  40  80 105 110 180 210 280 680
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
mean (ca_interstates)
```

```
## [1] 124.2143
```

```r
sd(ca_interstates)
```

```
## [1] 182.4956
```

```r
median (ca_interstates)
```

```
## [1] 60
```

```r
quantile(ca_interstates)
```

```
##     0%    25%    50%    75%   100% 
##   5.00   9.25  60.00 162.50 680.00
```

```r
range(ca_interstates)
```

```
## [1]   5 680
```

```r
sum(ca_interstates)
```

```
## [1] 1739
```

```r
min(ca_interstates)
```

```
## [1] 5
```

```r
max(ca_interstates)
```

```
## [1] 680
```

```r
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
ca_colleges <- readr::read_csv("ca_college_data.csv")
```

```
## Rows: 341 Columns: 10
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (4): INSTNM, CITY, STABBR, ZIP
## dbl (6): ADM_RATE, SAT_AVG, PCIP26, COSTT4_A, C150_4_POOLED, PFTFTUG1_EF
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
#Use summary() to see general statistical information about a data set.
summary(ca_colleges)
```

```
##     INSTNM              CITY              STABBR              ZIP           
##  Length:341         Length:341         Length:341         Length:341        
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##                                                                             
##     ADM_RATE         SAT_AVG         PCIP26           COSTT4_A    
##  Min.   :0.0807   Min.   : 870   Min.   :0.00000   Min.   : 7956  
##  1st Qu.:0.4581   1st Qu.: 985   1st Qu.:0.00000   1st Qu.:12578  
##  Median :0.6370   Median :1078   Median :0.00000   Median :16591  
##  Mean   :0.5901   Mean   :1112   Mean   :0.01981   Mean   :26685  
##  3rd Qu.:0.7461   3rd Qu.:1237   3rd Qu.:0.02457   3rd Qu.:39289  
##  Max.   :1.0000   Max.   :1555   Max.   :0.21650   Max.   :69355  
##  NA's   :240      NA's   :276    NA's   :35        NA's   :124    
##  C150_4_POOLED     PFTFTUG1_EF    
##  Min.   :0.0625   Min.   :0.0064  
##  1st Qu.:0.4265   1st Qu.:0.3212  
##  Median :0.5845   Median :0.5016  
##  Mean   :0.5705   Mean   :0.5577  
##  3rd Qu.:0.7162   3rd Qu.:0.8117  
##  Max.   :0.9569   Max.   :1.0000  
##  NA's   :221      NA's   :53
```

```r
glimpse(ca_colleges)
```

```
## Rows: 341
## Columns: 10
## $ INSTNM        <chr> "Grossmont College", "College of the Sequoias", "College…
## $ CITY          <chr> "El Cajon", "Visalia", "San Mateo", "Ventura", "Oxnard",…
## $ STABBR        <chr> "CA", "CA", "CA", "CA", "CA", "CA", "CA", "CA", "CA", "C…
## $ ZIP           <chr> "92020-1799", "93277-2214", "94402-3784", "93003-3872", …
## $ ADM_RATE      <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
## $ SAT_AVG       <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
## $ PCIP26        <dbl> 0.0016, 0.0066, 0.0038, 0.0035, 0.0085, 0.0151, 0.0000, …
## $ COSTT4_A      <dbl> 7956, 8109, 8278, 8407, 8516, 8577, 8580, 9181, 9281, 93…
## $ C150_4_POOLED <dbl> NA, NA, NA, NA, NA, NA, 0.2334, NA, NA, NA, NA, 0.1704, …
## $ PFTFTUG1_EF   <dbl> 0.3546, 0.5413, 0.3567, 0.3824, 0.2753, 0.4286, 0.2307, …
```

```r
#Use view() to get an Excel-looking spreadsheet.
view(ca_colleges)
```


```r
# names() and colnames() both output column names!
names(ca_colleges)
```

```
##  [1] "INSTNM"        "CITY"          "STABBR"        "ZIP"          
##  [5] "ADM_RATE"      "SAT_AVG"       "PCIP26"        "COSTT4_A"     
##  [9] "C150_4_POOLED" "PFTFTUG1_EF"
```

```r
colnames(ca_colleges)
```

```
##  [1] "INSTNM"        "CITY"          "STABBR"        "ZIP"          
##  [5] "ADM_RATE"      "SAT_AVG"       "PCIP26"        "COSTT4_A"     
##  [9] "C150_4_POOLED" "PFTFTUG1_EF"
```
head() and foot() functions show top few and bottom few rows

```r
head(ca_colleges, n=3)
```

```
## # A tibble: 3 × 10
##   INSTNM       CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##   <chr>        <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
## 1 Grossmont C… El C… CA     9202…       NA      NA 0.0016     7956            NA
## 2 College of … Visa… CA     9327…       NA      NA 0.0066     8109            NA
## 3 College of … San … CA     9440…       NA      NA 0.0038     8278            NA
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```

```r
tail(ca_colleges, n=2)  #can also select number of rows you want to show for this, here I picked 2
```

```
## # A tibble: 2 × 10
##   INSTNM       CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##   <chr>        <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
## 1 Western Sta… Irvi… CA     9261…       NA      NA     NA       NA            NA
## 2 Thomas Jeff… San … CA     92101       NA      NA     NA       NA            NA
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```

dplyr package 
Part of the tidyverse, `dplyr is used to transform data frames by extracting, rearranging, and summarizing data such that they are focused on a question of interest. This is very helpful,  especially when wrangling large data, and makes dplyr one of most frequently used packages in the tidyverse. The two functions we will use most are `select()` and `filter()`.  

```r
#Use select() to only view specific columns in names(), choose as many as you want.
select(ca_colleges, "ADM_RATE","SAT_AVG")
```

```
## # A tibble: 341 × 2
##    ADM_RATE SAT_AVG
##       <dbl>   <dbl>
##  1       NA      NA
##  2       NA      NA
##  3       NA      NA
##  4       NA      NA
##  5       NA      NA
##  6       NA      NA
##  7       NA      NA
##  8       NA      NA
##  9       NA      NA
## 10       NA      NA
## # ℹ 331 more rows
```
Let's assign these two columns to their own object, college_stats.

```r
 college_stats <- select(ca_colleges, "ADM_RATE","SAT_AVG")
```

You can select several columns adjacent to each other.

```r
select(ca_colleges, CITY:COSTT4_A)
```

```
## # A tibble: 341 × 7
##    CITY      STABBR ZIP        ADM_RATE SAT_AVG PCIP26 COSTT4_A
##    <chr>     <chr>  <chr>         <dbl>   <dbl>  <dbl>    <dbl>
##  1 El Cajon  CA     92020-1799       NA      NA 0.0016     7956
##  2 Visalia   CA     93277-2214       NA      NA 0.0066     8109
##  3 San Mateo CA     94402-3784       NA      NA 0.0038     8278
##  4 Ventura   CA     93003-3872       NA      NA 0.0035     8407
##  5 Oxnard    CA     93033-6699       NA      NA 0.0085     8516
##  6 Moorpark  CA     93021-1695       NA      NA 0.0151     8577
##  7 San Bruno CA     94066-1698       NA      NA 0          8580
##  8 Glendale  CA     91208-2894       NA      NA 0.002      9181
##  9 Glendora  CA     91741-1899       NA      NA 0.0021     9281
## 10 Fresno    CA     93741            NA      NA 0.0324     9370
## # ℹ 331 more rows
```
Other ways to use select():

```r
select(ca_colleges, contains("C"))
```

```
## # A tibble: 341 × 4
##    CITY      PCIP26 COSTT4_A C150_4_POOLED
##    <chr>      <dbl>    <dbl>         <dbl>
##  1 El Cajon  0.0016     7956        NA    
##  2 Visalia   0.0066     8109        NA    
##  3 San Mateo 0.0038     8278        NA    
##  4 Ventura   0.0035     8407        NA    
##  5 Oxnard    0.0085     8516        NA    
##  6 Moorpark  0.0151     8577        NA    
##  7 San Bruno 0          8580         0.233
##  8 Glendale  0.002      9181        NA    
##  9 Glendora  0.0021     9281        NA    
## 10 Fresno    0.0324     9370        NA    
## # ℹ 331 more rows
```

```r
#select all except specified column names
select(ca_colleges, -INSTNM, -ZIP, -C150_4_POOLED)
```

```
## # A tibble: 341 × 7
##    CITY      STABBR ADM_RATE SAT_AVG PCIP26 COSTT4_A PFTFTUG1_EF
##    <chr>     <chr>     <dbl>   <dbl>  <dbl>    <dbl>       <dbl>
##  1 El Cajon  CA           NA      NA 0.0016     7956       0.355
##  2 Visalia   CA           NA      NA 0.0066     8109       0.541
##  3 San Mateo CA           NA      NA 0.0038     8278       0.357
##  4 Ventura   CA           NA      NA 0.0035     8407       0.382
##  5 Oxnard    CA           NA      NA 0.0085     8516       0.275
##  6 Moorpark  CA           NA      NA 0.0151     8577       0.429
##  7 San Bruno CA           NA      NA 0          8580       0.231
##  8 Glendale  CA           NA      NA 0.002      9181       0.421
##  9 Glendora  CA           NA      NA 0.0021     9281       0.440
## 10 Fresno    CA           NA      NA 0.0324     9370       0.366
## # ℹ 331 more rows
```

```r
#select columns based on starting letter(s)
select(ca_colleges, starts_with("S"))
```

```
## # A tibble: 341 × 2
##    STABBR SAT_AVG
##    <chr>    <dbl>
##  1 CA          NA
##  2 CA          NA
##  3 CA          NA
##  4 CA          NA
##  5 CA          NA
##  6 CA          NA
##  7 CA          NA
##  8 CA          NA
##  9 CA          NA
## 10 CA          NA
## # ℹ 331 more rows
```

```r
#select columns based on ending letter(s)
select(ca_colleges, ends_with("E"))
```

```
## # A tibble: 341 × 1
##    ADM_RATE
##       <dbl>
##  1       NA
##  2       NA
##  3       NA
##  4       NA
##  5       NA
##  6       NA
##  7       NA
##  8       NA
##  9       NA
## 10       NA
## # ℹ 331 more rows
```
You can also rename your column names with rename().

```r
ca_colleges <- rename(ca_colleges,inst_name="INSTNM")  #this is one but you can change as many as you want, just seperate with commas 
ca_colleges  #check your work
```

```
## # A tibble: 341 × 10
##    inst_name   CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##    <chr>       <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
##  1 Grossmont … El C… CA     9202…       NA      NA 0.0016     7956        NA    
##  2 College of… Visa… CA     9327…       NA      NA 0.0066     8109        NA    
##  3 College of… San … CA     9440…       NA      NA 0.0038     8278        NA    
##  4 Ventura Co… Vent… CA     9300…       NA      NA 0.0035     8407        NA    
##  5 Oxnard Col… Oxna… CA     9303…       NA      NA 0.0085     8516        NA    
##  6 Moorpark C… Moor… CA     9302…       NA      NA 0.0151     8577        NA    
##  7 Skyline Co… San … CA     9406…       NA      NA 0          8580         0.233
##  8 Glendale C… Glen… CA     9120…       NA      NA 0.002      9181        NA    
##  9 Citrus Col… Glen… CA     9174…       NA      NA 0.0021     9281        NA    
## 10 Fresno Cit… Fres… CA     93741       NA      NA 0.0324     9370        NA    
## # ℹ 331 more rows
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```

Now for the filter() function. `filter()` allows us to extract data that meet specific criteria within a variable. Let's use this to find UC Davis.

```r
filter(ca_colleges, CITY=="Davis") 
```

```
## # A tibble: 1 × 10
##   inst_name    CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##   <chr>        <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
## 1 University … Davis CA     9561…    0.423    1218  0.198    33904         0.850
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```
Try to find another CA college of your choice.


`filter()` allows all of the expected operators; i.e. >, >=, <, <=, != (not equal), and == (equal).

What colleges have an admission rate between 10% and 50%?

```r
filter(ca_colleges, between(ADM_RATE, .1, .5))
```

```
## # A tibble: 32 × 10
##    inst_name   CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##    <chr>       <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
##  1 California… Cars… CA     9074…    0.479      NA 0.03      13027         0.384
##  2 California… Nort… CA     91330    0.482     918 0.0341    16591         0.502
##  3 California… Full… CA     9283…    0.482    1017 0.0323    17049         0.621
##  4 California… Long… CA     9084…    0.319    1052 0.0377    18192         0.679
##  5 San Diego … San … CA     92182    0.346    1132 0.0389    22056         0.706
##  6 California… San … CA     93407    0.295    1270 0.0651    25300         0.776
##  7 University… La J… CA     92093    0.357    1324 0.216     31043         0.872
##  8 University… Irvi… CA     92697    0.406    1206 0.107     31198         0.876
##  9 University… Los … CA     9009…    0.180    1334 0.155     33078         0.911
## 10 University… Davis CA     9561…    0.423    1218 0.198     33904         0.850
## # ℹ 22 more rows
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```

How about 100%? 

```r
filter(ca_colleges, ADM_RATE == 1.0)
```

```
## # A tibble: 4 × 10
##   inst_name    CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##   <chr>        <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
## 1 California … Fres… CA     93727        1      NA      0    13869         0.176
## 2 Shasta Bibl… Redd… CA     96002        1      NA      0    22005         0.426
## 3 North-West … West… CA     91790        1      NA      0       NA        NA    
## 4 Concorde Ca… San … CA     9211…        1      NA      0       NA        NA    
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```

You can also specify a tolerance range (or range of allowed error).

```r
#here we are looking for colleges with a 30% exceptance rate, give or take 1%
filter(ca_colleges, near(ADM_RATE, .3, tol = 0.01)) 
```

```
## # A tibble: 2 × 10
##   inst_name    CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##   <chr>        <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
## 1 California … San … CA     93407    0.295    1270 0.0651    25300         0.776
## 2 Scripps Col… Clar… CA     9171…    0.299    1353 0.152     66060         0.871
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```
You can also use filter() to look at multiple parameters at once. 

```r
filter(ca_colleges, CITY == "San Francisco" & COSTT4_A >= 20000) #here we are looking for colleges in San Francisco with a cost 4 attendance >= $20000
```

```
## # A tibble: 9 × 10
##   inst_name    CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##   <chr>        <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
## 1 San Francis… San … CA     94132    0.682     979 0.0729    22396         0.522
## 2 Argosy Univ… San … CA     9410…   NA          NA 0         28125         0.304
## 3 Academy of … San … CA     94105   NA          NA 0         38000         0.370
## 4 FIDM-Fashio… San … CA     9410…    0.363      NA 0         43881         0.651
## 5 American Co… San … CA     9410…   NA          NA 0         47827        NA    
## 6 California … San … CA     9410…    0.648      NA 0         59502         0.595
## 7 San Francis… San … CA     9410…    0.418      NA 0         60410         0.718
## 8 University … San … CA     9411…    0.714    1150 0.0531    61072         0.716
## 9 San Francis… San … CA     9413…    0.926      NA 0         65453         0.388
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```
Watch out! There's quite a difference between | and &. | is 'or'.

```r
filter(ca_colleges, CITY == "San Francisco" | COSTT4_A >= 20000)  #here we are looking for colleges in San Francisco or colleges with a cost 4 attendance >= $20000
```

```
## # A tibble: 106 × 10
##    inst_name   CITY  STABBR ZIP   ADM_RATE SAT_AVG PCIP26 COSTT4_A C150_4_POOLED
##    <chr>       <chr> <chr>  <chr>    <dbl>   <dbl>  <dbl>    <dbl>         <dbl>
##  1 City Colle… San … CA     9411…   NA          NA 0.0032    10333        NA    
##  2 Santa Barb… Bake… CA     93309   NA          NA 0         20028         0.466
##  3 California… Hayw… CA     94542    0.698      NA 0.0501    20303         0.465
##  4 Lincoln Un… Oakl… CA     9461…   NA          NA 0         21195         0.697
##  5 California… Pomo… CA     91768    0.592    1045 0.0453    21223         0.652
##  6 Shasta Bib… Redd… CA     96002    1          NA 0         22005         0.426
##  7 San Diego … San … CA     92182    0.346    1132 0.0389    22056         0.706
##  8 California… Vall… CA     94590    0.682      NA 0         22204         0.599
##  9 Southern C… Whit… CA     90604   NA          NA 0.136     22229        NA    
## 10 San Franci… San … CA     94132    0.682     979 0.0729    22396         0.522
## # ℹ 96 more rows
## # ℹ 1 more variable: PFTFTUG1_EF <dbl>
```

That's enough for today...let's knit and save.

