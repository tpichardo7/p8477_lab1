Lab Report 1
================

# Question 1

Explore the dataset and answer the following questions:

## 1.1

What variables does the dataset contain? How many weeks are included for
each variable in the dataset? (Hint: what function gives the column
names? What function gives the number of rows in a data frame?)

## 1.2

What state are you from? What was the ILI in the 2nd week of the season
for your state? (Note if you are from out of the States or Florida (the
CDC did not have data for Florida that season), please use New York City
instead).

## 1.3

Suppose you store the dataset in a variable called ‘ili’. What do the
outputs from the following commands represent? NOTE: Specify the date(s)
and location(s); do not copy & paste the output.

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

## 1.5

When did New York City have its peak ILI (i.e. maximum ILI) that flu
season?

# Question 2

Plot the weekly ILI in New York City (column: New.York.City) over time.

# Question 3

New York City is in New York State. To compare ILI in NYC to that in NY
State, superimpose the weekly ILI for NY State to the above plot (Q2).

# Question 4

When you have multiple variables/categories and each has a lot of data
points, boxplot is an effective way toay the distributions of the
variables/categories. Use boxplot to show the variation in ILI among all
states/cities for each week in the last flu season.

# Math Operations & Function

# Question 5

We know that the solutions of the quadratic equation ax^2 + bx + c = 0
are: Write a script in R to find the solutions for the followinf
equations:

## part a

2x^2 + 10x + 3 = 0

## part b

5x^2 - 6x + 1 = 0

# Question 6

To make implementation of Question 5 easier, create a function to find
the solutions for any quadratic equation with constants a, b, and
c. Your function should be able to return the two solutions once you
specify the three constants, For instance, suppose you name the function
Fn_sol_quadratic, the command Fn_sol_quadratic(a=2, b=10, c=3) will
return the two solutions for equation 2x^2 +10x +3 = 0
