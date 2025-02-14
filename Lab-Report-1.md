Lab Report 1
================

``` r
knitr::opts_chunk$set(
        echo = TRUE,
        warning = FALSE,
  fig.width = 6,
  fig.asp = .6,
  out.width = "90%"
)

theme_set(theme_minimal() +theme(legend.position = "bottom"))

options(
  ggplot2.continuous.color = "viridis",
  ggplot2.continuous.fill = "viridis"
)

scale_color_discrete = scale_colour_viridis_d
scale_fill_discrete = scale_fill_viridis_d
```

``` r
# importing and cleaning the data
weekly_ili = read_csv(file = "./data/da_ILINet.csv") |> 
  janitor::clean_names() |> 
  select(-florida)
```

    ## Rows: 52 Columns: 55
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## dbl  (53): Alabama, Alaska, Arizona, Arkansas, California, Colorado, Connect...
    ## lgl   (1): Florida
    ## date  (1): Date
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

# Question 1

Explore the dataset and answer the following questions:

## 1.1

What variables does the dataset contain? How many weeks are included for
each variable in the dataset? (Hint: what function gives the column
names? What function gives the number of rows in a data frame?)

The data set contain a date variable to denote one day per week from
September 30, 2018 to September 22, 2019, for a total of 52 weeks. The
other variables are 50 U.S. states (although there is no data recorded
for Florida) and U.S. territories such as Puerto Rico and the Virgin
Islands. The dataset also includes two city variables: Washington D.C.
and New York City.

## 1.2

What state are you from? What was the ILI in the 2nd week of the season
for your state? (Note if you are from out of the States or Florida (the
CDC did not have data for Florida that season), please use New York City
instead).

I am from New York, and the ILI in the 2nd week of the season was 982.

## 1.3

Suppose you store the dataset in a variable called ‘ili’. What do the
outputs from the following commands represent? NOTE: Specify the date(s)
and location(s); do not copy & paste the output.

``` r
ili = weekly_ili |> 
  pivot_longer(
    cols = alabama:wyoming,
    names_to = "state",
    values_to = "ili"
  )
```

The outputs from the following commands represent the influenza-like
illness per 100,000 cases recorded for that week.

### part a

ili \[2, 6\]

### part b

ili \[30, 5:14\]

### part c

ili \[, 5\]

### part d

ili \[36, ‘New.York.City’\] (Note: R does not ‘like’ space in variable
names, so replace space with ‘.’ here)

## 1.4

What are the mean and maximum ILI levels for New York City,
respectively? (hint: you can use the ‘summary’ function to print the
summary statistics for each column. Or use the function ‘mean’ and ‘max’
to get the results respectively)

The mean ILI level for New York City is 2290. The maximum ILI level for
New York City is 4383.

## 1.5

When did New York City have its peak ILI (i.e. maximum ILI) that flu
season?

New York City had its peak ILI on December 23, 2018 that flu season.

# Question 2

Plot the weekly ILI in New York City (column: New.York.City) over time.

``` r
nyc = ggplot(weekly_ili, aes(x = date, y = new_york_city, color = date)) +
  geom_point(alpha = 0.6) +
  geom_smooth() +
  labs(title = "Weekly ILI in New York City", 
       x = "Date", 
       y = "Influenza-like Illness (per 100,000)")
```

# Question 3

New York City is in New York State. To compare ILI in NYC to that in NY
State, superimpose the weekly ILI for NY State to the above plot (Q2).

``` r
ny_state = ggplot(weekly_ili, aes(x = date, y = new_york, color = date)) +
  geom_point(alpha = 0.6) +
  geom_smooth() +
  labs(title = "Weekly ILI in New York State", 
       x = "Date", 
       y = "Influenza-like Illness (per 100,000)")
```

``` r
nyc + ny_state
```

    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'
    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

<img src="Lab-Report-1_files/figure-gfm/unnamed-chunk-6-1.png" width="90%" />

# Question 4

When you have multiple variables/categories and each has a lot of data
points, boxplot is an effective way to display the distributions of the
variables/categories. Use boxplot to show the variation in ILI among all
states/cities for each week in the last flu season.

``` r
ggplot(ili, aes(x = date, y = ili, color = state)) +
  geom_boxplot()
```

<img src="Lab-Report-1_files/figure-gfm/unnamed-chunk-7-1.png" width="90%" />

# Math Operations & Function

# Question 5

We know that the solutions of the quadratic equation ax^2 + bx + c = 0
are: Write a script in R to find the solutions for the following
equations:

## part a

2x^2 + 10x + 3 = 0

``` r
a = 2
b = 10
c = 3
```

``` r
discriminant = b^2 - 4* a * c
```

``` r
if (discriminant > 0) {
  root1 = (-b + sqrt(discriminant)) / (2 * a)
  root2 = (-b - sqrt(discriminant)) / (2 * a)
  print(c(root1, root2))
} else if (discriminant == 0) {
  root = -b / (2 * a)
  print(root)
} else {
  realPart = -b / (2 * a)
  imaginaryPart = sqrt(-discriminant) / (2 * a)
  print(paste(realPart, "+", imaginaryPart, "i"))
  print(paste(realPart, "-", imaginaryPart, "i"))
}
```

    ## [1] -0.3205505 -4.6794495

## part b

5x^2 - 6x + 1 = 0

``` r
a = 5
b = -6
c = 1
```

``` r
discriminant = b^2 - 4* a * c
```

``` r
if (discriminant > 0) {
  root1 = (-b + sqrt(discriminant)) / (2 * a)
  root2 = (-b - sqrt(discriminant)) / (2 * a)
  print(c(root1, root2))
} else if (discriminant == 0) {
  root = -b / (2 * a)
  print(root)
} else {
  realPart = -b / (2 * a)
  imaginaryPart = sqrt(-discriminant) / (2 * a)
  print(paste(realPart, "+", imaginaryPart, "i"))
  print(paste(realPart, "-", imaginaryPart, "i"))
}
```

    ## [1] 1.0 0.2

# Question 6

To make implementation of Question 5 easier, create a function to find
the solutions for any quadratic equation with constants a, b, and
c. Your function should be able to return the two solutions once you
specify the three constants, For instance, suppose you name the function
Fn_sol_quadratic, the command Fn_sol_quadratic(a=2, b=10, c=3) will
return the two solutions for equation 2x^2 +10x +3 = 0

``` r
quadratic = function (a, b, c) {
  
  discriminant = b^2 - 4*a*c
  
  if (discriminant > 0) {
    root1 = (-b + sqrt(discriminant)) / (2*a)
    root2 = (-b - sqrt(discriminant)) / (2*a)
    return(c(root1, root2))
    
  } else if (discriminant == 0) {
    
    root = -b / (2*a)
    return(root)
    
    } else {
      real_part = -b / (2*a)
      imaginary_part = sqrt(-discriminant) / (2*a)
      return(c(real = real_part, imaginary = imaginary_part))
  }
}
```

2x^2 + 10x + 3 = 0

``` r
quadratic(2, 10, 3)
```

    ## [1] -0.3205505 -4.6794495

5x^2 - 6x + 1 = 0

``` r
quadratic(5, -6, 1)
```

    ## [1] 1.0 0.2
