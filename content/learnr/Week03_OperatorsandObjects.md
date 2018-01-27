---
title: "Operators and Objects"
weight: 30
---

Basic operations
================

Now that we have some datatypes, we can start learning what we can do with them.

Maths
-----

In R, we have our common **operators** that you're probably used to if you've performed calculations on computers before.

| Action             | Operator | Example        |
|--------------------|----------|----------------|
| Subtract           | -        | `5 - 4` = 1    |
| Add                | +        | `5 + 4` = 9    |
| Multiply           | \*       | `5 * 4` = 20   |
| Divide             | /        | `5 / 4` = 1.25 |
| Raise to the power | ^        | `5 ^ 4` = 625  |

R adheres to **BODMAS** so you can construct safe calculations that combine operators in reliable ways.

Additionally, there are some other operators worth knowing about.

| Action           | Operator | Example         |
|------------------|----------|-----------------|
| Basic sequence   | :        | `1:3` = 1, 2, 3 |
| Integer division | %/%      | `9 %/% 4` = 2   |
| Modulus          | %%       | `9 %% 4` = 1    |

The colon (`:`) is a really snazzy way of generating a sequence of numbers that step by 1. You specify a beginning number and an end number and R will produce all the whole numbers including and between the two numbers. This even works for negative numbers or producing descending values.

**Integer division** (`%/%`) tells you how many times the first number can be divided by the second without returning a fractional value.

``` r
1:8
```

    ## [1] 1 2 3 4 5 6 7 8

``` r
1:8 %/% 3
```

    ## [1] 0 0 1 1 1 2 2 2

``` r
1:8 %/% 4
```

    ## [1] 0 0 0 1 1 1 1 2

The **modulus** (`%%`) tells you how much is left over after performing an integer division.

``` r
1:8
```

    ## [1] 1 2 3 4 5 6 7 8

``` r
1:8 %% 3
```

    ## [1] 1 2 0 1 2 0 1 2

``` r
1:8 %% 4
```

    ## [1] 1 2 3 0 1 2 3 0

For reasons not worth worrying about yet, R uses the `%` sign as the start of special operators -- usually these are custom built, contain text, or reserved symbols.

Comparison
----------

The next important thing to know about is how to write comparisons; ways of looking at two or more things and finding out if they're the same, or different.

### Common operators

The less thans and greater thans are symbols that are in pretty much every language for comparisons, but the test to see if two values are the same or not can often vary across languages.

### Summary

| Action            | Operator    | Example                               |
|-------------------|-------------|---------------------------------------|
| Less than (lt)    | &lt;        | `5 < 5` = FALSE                       |
| lt or equal to    | &lt;=       | `5 <= 5` = TRUE                       |
| Greater than (gt) | &gt;        | `5 > 5` = FALSE                       |
| gt or equal to    | &gt;=       | `5 >= 5` = TRUE                       |
| Exactly equal     | ==          | `(0.5 - 0.3) == (0.3 - 0.1)` is FALSE |
| Exactly equal     | ==          | 2 == 2 is TRUE                        |
| Not equal         | !=          | `(0.5 - 0.3) != (0.3 - 0.1)` is TRUE  |
| Not equal         | !=          | 2 != 2 is FALSE                       |
| Equal             | all.equal() | `all.equal(0.5-0.3,0.3-0.1)` is TRUE  |
| In                | %in%        | `"Red" %in% c("Blue","Red")` is TRUE  |

Let's have a closer look at the nitty gritty of those last few; there's good reason for them

Testing for equality can get a little weird with R because it uses a different way of storing numbers than we would expect. It doesn't store numbers quite as precisely as we expect - somewhere at the very end of a large number of decimal places, the value can be rounded incorrectly. It doesn't make a difference to most of our calculations but it will often hit when you're comparing two decimal values.

Let's see an example.

Both these calculation return what we think of as `0.2`

``` r
0.5 - 0.3
```

    ## [1] 0.2

``` r
0.6 - 0.4
```

    ## [1] 0.2

Indeed, if we test `0.2` is the same as `0.2` we get a `TRUE` which matches our expectations.

``` r
0.2 == 0.2
```

    ## [1] TRUE

But, when we perform two calculations, even though they come out to the same value to us, there's a little bit of imprecision in how they're stored that stops them from being *exactly the same* number.

``` r
(0.6 - 0.4) == (0.5 - 0.3)
```

    ## [1] FALSE

To avoid this issue, if you're comparing decimal values that result from calculations it is better to use the `all.equal()` function. `all.equal()` adds a tolerance to the comparison which means the very subtle imprecision is ignored. The default tolerance is 1.5 × 10<sup>−8</sup>, in other words the imprecision is *very, very small*.

``` r
all.equal(0.6 - 0.4 , 0.5 - 0.3)
```

    ## [1] TRUE

Logic
-----

Once we can do a single check, we inevitably want to do multiple checks at the same time.

To combine multiple checks, we can use *logical operators*.

### Common operators

The ampersand (`&`) allows us to combine two checks to do an AND check, which is "are both things true?".

``` r
TRUE & TRUE
```

    ## [1] TRUE

``` r
TRUE & FALSE
```

    ## [1] FALSE

``` r
FALSE & FALSE
```

    ## [1] FALSE

``` r
(2 < 3) & (4 == 4)
```

    ## [1] TRUE

``` r
(2 < 3) & (4 != 4)
```

    ## [1] FALSE

The pipe, or bar (`|`) allows us to do an OR check, which is "are either of these things true?".

``` r
TRUE | TRUE
```

    ## [1] TRUE

``` r
TRUE | FALSE
```

    ## [1] TRUE

``` r
FALSE | FALSE
```

    ## [1] FALSE

``` r
(2 < 3) | (4 == 4)
```

    ## [1] TRUE

``` r
(2 < 3) | (4 != 4)
```

    ## [1] TRUE

The exclamation point (`!`) allows us to a perform a NOT check, by negating or swapping a check's result. This allows you say things like "is this check true and that check not true?".

``` r
TRUE & TRUE
```

    ## [1] TRUE

``` r
TRUE & !FALSE
```

    ## [1] TRUE

``` r
!FALSE & !FALSE
```

    ## [1] TRUE

``` r
(2 < 3) & (4 == 4)
```

    ## [1] TRUE

``` r
(2 < 3) & !(4 != 4)
```

    ## [1] TRUE

### Other operators

Less commonly, there other logical checks you might to perform.

We can do an XOR, where one and only one of two values being checked is true.

``` r
xor(TRUE, FALSE)
```

    ## [1] TRUE

``` r
xor(TRUE, TRUE)
```

    ## [1] FALSE

``` r
xor(FALSE, FALSE)
```

    ## [1] FALSE

### Summary

We can produce sophisticated checks from a few simple building blocks. This will come in very handy down the line when doing things like filtering datasets or creating new fields in your data.

| Action | Operator | Example                                       |
|--------|----------|-----------------------------------------------|
| Not    | !        | `!TRUE` is FALSE                              |
| And    | &        | `TRUE & FALSE` is FALSE                       |
| And    | &        | `c(TRUE,TRUE) & c(FALSE,TRUE)` is FALSE, TRUE |
| Or     | `|`      | `TRUE | FALSE` is TRUE                        |
| Xor    | xor()    | `xor(TRUE,FALSE)` is TRUE                     |

Summary
-------

This basic operations section has hopefully taught you how to manipulate values and construct comparisons. These are important building blocks in data analysis, and whilst we've been working with only a single value at a time, in the next section we'll see how it works with more data.

R objects
=========

So far we've just worked with some single values to get to grips with how some of the various operations work. Of course, we rarely work with a single value! If we did, we could just use a calculator.

This week you'll get to grips with some different ways of storing data and how to manipulate your datasets in the "traditional" way. This will help you understand a lot of code written in the past, and will equip you to understand data manipulation of tabular data.

Storing values
--------------

When we were performing operations, we got some values output to the console. One of the key principles in writing code is Don't Repeat Yourself (DRY) so we need to know how we can avoid repeating ourselves in R. One of the ways you can do that is to store a value for use later.

In R, we can store values by **assigning** them a name. This makes a **variable** or **object**. We can do this with a few different operators, but the traditional operator is a `<-`. The format for assigning a value is `nameofthing <- value`.

Add this operation into your script for use later on.

``` r
my_variable <- 5 + 3
my_variable*2
```

    ## [1] 16

Valid names for a variable include upper-case letters, lower case letters, numbers anywhere but the beginning, periods (`.`), and hyphens (`_`).

There are a number of different competing conventions for how you name variables. The most common conventions are shown below. I have no strong feelings for any system and only ask that you pick one and stick with it within a single script. Whatever you do, don't forget names are case sensitive!

``` r
myfirstvariable <- 1
myFirstVariable <- 1
MyFirstVariable <- 1
my_first_variable <- 1
my.first.variable <- 1
```

You can create names breaking the rules governing valid names by placing the rule breaking name between two back-ticks (\`). I don't recommend you do this with variables you'll create, but you'll often end up with names that break conventions when importing data, especially when you import from spreadsheets.

Variables you store get stored in-memory. This means they'll hang around whilst R is open and will be gone after that. You can see variables you've created in the Environment tab.

RStudio will by default save your variables for you so that next time you open it up, your variables are stored.

\*This is both a blessing and a curse. RStudio saving your variables is a blessing because you don't have to worry about keeping RStudio open the all time.

BUT you'll inevitably create something at some point through the console or an Untitled R file and then lose that bit of code. Now when you're script runs in a fresh session it'll fail. You'll risk tearing your hair out and worse as you go through the pain of debugging this.

I recommend you get in the habit early of not working with your session being saved. Turn it off in *Tools &gt; Global Options*, untick "Restore .RData into workspace at startup"\*

If you need to manage what's been stored you can remove them with `rm()`.

Try removing 'my\_variable' you created earlier.

You can also achieve the same results by using the broom symbol in the Environment tab in RStudio.

Vectors
-------

A **vector** is a collection of values that hold the same datatype. It is **one-dimensional** in that none of the **elements** in the collection correspond to other values like they might in a table of values.

A single value is actually a vector of **length** 1.

When I introduced the colon (`:`) as a means of generating a sequence, we were in fact generating a vector where each element was a number in the sequence. The vector has a length which is as long as the number of values generated by the sequence.

``` r
-1:1
```

    ## [1] -1  0  1

Another way of producing a vector is to use the combine function (`c()`). This is great for combining a number of disparate character strings into a vector.

``` r
c("red","yellow","blue")
```

    ## [1] "red"    "yellow" "blue"

A single value is a still a vector. What we see when we use the `c()` function is that we're combining vectors. As a result we can also use it on longer vectors too.

``` r
c(1:3, 2:1, 5:8)
```

    ## [1] 1 2 3 2 1 5 6 7 8

When we combine values into a single vector, R will change everything to the same datatype using some conversions.

Getting information about vectors
---------------------------------

Our `class()` function will still work with a vector with a length greater than 1 to get you it's datatype.

Let's look at a sequence of numbers and one of the built-in vectors that contains the alphabet.

``` r
class(1:10)
```

    ## [1] "integer"

``` r
LETTERS
```

    ##  [1] "A" "B" "C" "D" "E" "F" "G" "H" "I" "J" "K" "L" "M" "N" "O" "P" "Q"
    ## [18] "R" "S" "T" "U" "V" "W" "X" "Y" "Z"

``` r
class(LETTERS)
```

    ## [1] "character"

We can use the `length()` function to find out the number of elements in a vector.

``` r
length(pi)
```

    ## [1] 1

``` r
length(LETTERS)
```

    ## [1] 26

To extract the names of values in a vector, we can use the `names()` function.

``` r
steph<-c(Steph="forename", Locke="surname")
names(steph)
```

    ## [1] "Steph" "Locke"

Calculations on multiple vectors
--------------------------------

When we perform calculations on two vectors, R will try to perform the operation for each set of elements. This is an **element-wise** or **pair-wise** calculation methodology.

In SQL, it's equivalent to where you might write `colA*colB` and you'll get the answer calculated for every row in the table. In Excel, it's equivalent to a Fill Down of multiplying two values on the same row.

Let's looks at how this works in practice in R.

We have two vectors, each containing two elements.

``` r
vecA <- 1:2
vecB <- 2:3
```

    ## [1] 1 2

    ## [1] 2 3

If we want to multiply the two vectors by each other, R will match each element in the first vector with it's counterpart in the second and multiply the two values together to make a new element.

You can also use this functionality of making a vector the same length as another, known as **recycling**, work for other mis-matched vector sizes. The only rule is that one of the vector lengths must divide cleanly by the other.

-   Two vectors of the same length divide by the other's length exactly one time and won't need to recycle
-   A vector of length one always cleanly divides any other vector's length and so will be recycled
-   A vector of length 2, will divide any vector with an even length and so will be recycled in those cases, but it cannot recycle cleanly for odd length vectors

``` r
1:10 * 2
1:10 * 2:3
1:10 * 2:4
```

    ##  [1]  2  4  6  8 10 12 14 16 18 20

    ##  [1]  2  6  6 12 10 18 14 24 18 30

    ## [1] "longer object length is not a multiple of shorter object length"

![](img/vectormultrecycle.png)

Vector recycling is useful and dangerous -- it can help you make elegant code or give you unexpected results. Especially when starting out, I recommend you make your vectors either the same length or length 1.

### Bitwise

Our logical operators that we covered earlier, work in a pairwise fashion. They'll return a vector of the same length as the longest one used in your logical statement.

``` r
a<-1:2>1
b<-2:3>1
```

    ## [1] FALSE  TRUE

    ## [1] TRUE TRUE

Making logical statements returns vectors with a logical datatype.

``` r
a&b
```

    ## [1] FALSE  TRUE

``` r
a|b
```

    ## [1] TRUE TRUE

Occasionally, you expect to only be operating on a single pair of values and want to enforce that R should only do the calculation on the first pair. In R, this called a **bitwise** AND (`&&`) or OR (`||`).

A bitwise logical statement will only do the check for the first elements in the vectors and ignore all the others.

``` r
a&&b
```

    ## [1] FALSE

``` r
a||b
```

    ## [1] TRUE

Use bitwise operators with extreme care!

Homework... It's turtle time!
-----------------------------

We're going to use a package you probably haven't seen since primary school...

Copy the code below into your script.

``` r
install.packages("TurtleGraphics")
```

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/bl/fy55z4g50x17rgtgn2hxwvr00000gn/T//Rtmpj0fv0g/downloaded_packages

``` r
library(TurtleGraphics)
```

    ## Loading required package: grid

``` r
turtle_init() # This starts off the turtle
```

![](Week03_OperatorsandObjects_files/figure-markdown_github/turtle-1.png)

``` r
turtle_down() # This means that when you feed instructions to your turtle, it leaves a mark.
```

Use "turtle\_left()" and place the number of an angle between the brackets to turn your turtle. The same applies for "turtle\_right()"

Use "turtle\_forward()" and "turtle\_backward()" to move him around and draw something. Inbetween the brackets should be a number specifying the number of "steps" the turtle should take.

Here's the twist. Use what you've learned today with the basic maths operations and create your drawing using sums instead of numbers. If you're brave you could investigate the help file and figure out how to do other code-ish type things like changing his colour!

Tweet your turtle\_doodle to @lockedata and show off your handywork!

Optional extras (this week - an excuse for a brew and a biscuit)
-----------------------

Well done everyone - You're half way through the basics course! Make yourself a brew and have a biscuit for every R Blogs you read that interest you and is relevant to your intended eventual use of R.
