---
title: "Basic Operations"

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

R adheres to **BODMAS**[1] so you can construct safe calculations that combine operators in reliable ways.

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

The pipe, or bar (`|`)[2] allows us to do an OR check, which is "are either of these things true?".

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

Homework... It's turtle time!
-----------------------------

We're going to use a package you probably haven't seen since primary school...

Copy the code below into your script.

``` r
install.packages("TurtleGraphics")
```

    ## Error in install.packages : Updating loaded packages

``` r
library(TurtleGraphics)
turtle_init() # This starts off the turtle
```

![](Week05_BasicOperators_files/figure-markdown_github/turtle-1.png)

``` r
turtle_down() # This means that when you feed instructions to your turtle, it leaves a mark.
```

Use "turtle\_left()" and place the number of an angle between the brackets to turn your turtle. The same applies for "turtle\_right()"

Use "turtle\_forward()" and "turtle\_backward()" to move him around and draw something. Inbetween the brackets should be a number specifying the number of "steps" the turtle should take.

Here's the twist. Use what you've learned today with the basic maths operations and create your drawing using sums instead of numbers. If you're brave you could investigate the help file and figure out how to do other code-ish type things like changing his colour!

Tweet your turtle\_doodle to @lockedata and show off your handywork!

