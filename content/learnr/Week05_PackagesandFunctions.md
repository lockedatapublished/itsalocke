---
title: "Good things come in small packages"
author: "Ellen Talbot"
weight: 50
date: "19/01/2018"
output: html_document
---

R functions
===========

In previous sections we've seen R **functions** that are used on objects to perform some activity. Functions seen so far include:

-   `class()` and `is.*()` functions for checking datatypes
-   `as.*` for converting to datatypes
-   `length()` and `names()` for metadata
-   `head()` and `tail()` for getting a small amount of elements from an object
-   `ncol()`, `nrow()`, `colnames()`, and `rownames()` for getting data.frame metadata
-   `Sys.Date()` and `Sys.time()` for getting current date-time values

There are a huge range of functions out there, whether available in R straight away, or from adding extra functionality.

Understanding how functions work and being able to use them correctly will help you learn, and use R effectively.

Using a function
----------------

A function does some computation on an object. The use of a function consists of:

1.  A function's name
2.  Parentheses
3.  0 or more inputs

Each input is provided to an **argument** or parameter within a function.

These arguments have names, although you don't often need to provide the names.

You can find out what arguments a function takes by using the code completion and it's help snippet, or by searching for the function in the Rstudio Help tab.

When you're inside the brackets of a function you can get the list of available arguments and auto-complete them.

<p>
Try getting the code completion to work with the function <code>tail()</code>.
</p>

Examining functions
-------------------

One of the niftiest things about R is being able to see the code for a function. You can examine how many functions work by just typing their name without any parentheses.

``` r
Sys.Date
```

    ## function () 
    ## as.Date(as.POSIXlt(Sys.time()))
    ## <bytecode: 0x11a7a61c8>
    ## <environment: namespace:base>

The first line(s) show how the arguments are specified. Subsequent lines show the code and the final lines starting with `<` can be mostly ignored.

Function input patterns
-----------------------

Functions tend to conform to certain patterns of inputs.

### No inputs

Some functions don't require the user to provide info and so they don't have any arguments. `Sys.Date()` and similar functions do not need user input because the functions provide information about the system.

``` r
Sys.Date
```

    ## function () 
    ## as.Date(as.POSIXlt(Sys.time()))
    ## <bytecode: 0x11a7a61c8>
    ## <environment: namespace:base>

Looking at the function definition, we can see that there are no arguments specified in the first line.

### Single inputs

Other functions only have a single allowed input. `length()` returns the length of an object so it only allows you to provide it with an object.

``` r
length
```

    ## function (x)  .Primitive("length")

We can see in this definition that the function takes the argument `x`.

### Many inputs

Some functions have multiple inputs, although not all of them are necessarily **mandatory**. `head()` and `tail()` have been used so far with only a single input but they take an optional argument as to how many elements should be returned.

``` r
head(letters)
```

    ## [1] "a" "b" "c" "d" "e" "f"

``` r
head(letters, 2)
```

    ## [1] "a" "b"

The `rnorm()` function allows us to generate a vector of values from a normal distribution. We can tell it how many values we need (`n`), and we can optionally provide the mean (`mean`) and standard deviation (`sd`) to describe the Normal curve that values should be selected from.

``` r
rnorm
```

    ## function (n, mean = 0, sd = 1) 
    ## .Call(C_rnorm, n, mean, sd)
    ## <bytecode: 0x25e0ab870>
    ## <environment: namespace:stats>

Looking at how `rnorm` is specified we can see that we're expected to provide `n`, but `mean` and `sd` are given values of 0 and 1 respectively by default.

``` r
rnorm(n=5)
```

    ## [1] -0.3888304 -1.0393453  0.2329764 -1.8130036  2.3513064

``` r
rnorm(n = 5, mean = 10, sd = 2)
```

    ## [1] 10.384046 11.241368  9.433422 12.842187 10.427146

### Unlimited inputs

Other functions can take an unlimited amount of input values. Functions like `sum()` will sum the values from a number of objects.

``` r
sum(1:3, 1:9, pi)
```

    ## [1] 54.14159

The ellipsis (`...`) is used to denote when the user can provide any number of values.

``` r
sum
```

    ## function (..., na.rm = FALSE)  .Primitive("sum")

Naming arguments
----------------

Every input provided to a function is associated with an argument.

Each argument must have a name. Even functions that allow unlimited inputs assign these inputs to a name. Behind the scenes, they get put into a list object and the list gets called `...` (or ellipsis).

There are some typical names for arguments that take your data object. These include:

-   `x`
-   `data`
-   `.data`
-   `df`

You don't usually have to provide the argument names, just put things in the relevant places in the function. Sometimes though, you *will* need to use argument names.

Here are my rules of thumb for knowing when you need to name names:

1.  You're using the arguments in an order that is different from the function author's intended order (you might be skipping some arguments as the default values are fine or you might just prefer a different order)
2.  The arguments you want to specify show up after the `...` in a function's argument list
3.  You want to give a specific name to a value in a `...` argument

We can provide names for clarity or so we can use arguments out of order if we prefer to.

``` r
rnorm(n = 5, mean = 10, sd = 2)
```

    ## [1] 13.40101 12.03754 10.00946 10.72839 12.97078

``` r
rnorm(mean = 10, sd = 2, n = 5)
```

    ## [1]  6.449526 11.375321 11.859469  8.037803  7.886540

A common behaviour change that you'll need to work with is how missing (`NA`) values get handled. Functions that allow you change this behaviour, usually have an argument called things like `na.rm`, `na.omit`, and `na.action`.

``` r
sum(1:5, NA)
```

    ## [1] NA

``` r
sum(1:5, NA, na.rm = TRUE)
```

    ## [1] 15

In the `sum()` example, I used the `na.rm` argument's name. This is because otherwise the `TRUE` would be considered part of the values being passed for summing. Without the name, the value gets considered as part of the `...`.

``` r
sum(1:5, NA, TRUE)
```

    ## [1] NA

A function will sometimes have `...` at the end of it's list of arguments when it utilises other functions and those have optional / default values.

For instance the `predict()` function allows us to take a model we've built and apply it to some new data.

It works for many different types of model and these different models expect different types of inputs. Some models expect data.frames, others expect time series data, etc.

There's lots of potential variations, the only thing that is mandatory is the model object.

``` r
predict
```

    ## function (object, ...) 
    ## UseMethod("predict")
    ## <bytecode: 0x102683438>
    ## <environment: namespace:stats>

The `predict()` function then determines what type of model object you've provided it and passes the model, and any other values you provided, to the relevant function, returning back the results.

``` r
linearMod<-lm(Sepal.Length~., data=iris)
logisticMod<-glm(Species~., data=iris, family=binomial)

predict(linearMod, iris[1,])
```

    ##        1 
    ## 5.004788

``` r
predict(logisticMod, iris[1,])
```

    ##         1 
    ## -38.02709

R packages
==========

An R package is a bundle of functions and/or datasets. It extends the capabilities that the "base" and "recommended" R packages have. By using packages we can do data manipulation in a variety of ways, produce all sorts of awesome charts, generate books like this, use other languages like Python and JavaScript, and of course, do all sorts of data analysis.

Installing packages
-------------------

Once you've identified a package that contains functions or data you're interested in using, we need to get the package onto our machine.

To get the package, you can use an R function or you can use the Install button on the Packages tab.

``` r
install.packages("datasauRus")
```

If you need to install a number of packages, `install.packages()` takes a vector of package names.

``` r
install.packages(c("datasauRus","tidyverse"))
```

Updating packages involves re-running `install.packages()` and it's usually easier to trigger this by using the Update button on the Packages tab and selecting all the packages you want to update.

### Installing from GitHub and other sources

The `install.packages()` function works with CRAN, CRAN mirrors, and CRAN-like repositories

If you want to install BioConductor packages, there are some helper scripts available from the BioConductor website, [bioconductor.org](http://www.bioconductor.org/install/).

Other package sources, such as GitHub, will involve building packages before they can be installed. If you're on Windows, this means you need an additional piece of software called [Rtools](http://cran.r-project.org/bin/windows/Rtools/). The other handy thing you'll need is the package `devtools` (available from CRAN). `devtools` provides a number of functions designed to make it easier to install from GitHub, BitBucket, and other sources.

``` r
library(devtools)
install_github("lockedata/pRojects")
```

Recommended packages
--------------------

Here are my recommended packages -- many of these will be covered later on.

### tidyverse

The `tidyverse` is a suite of packages designed to make your life easier. It's well worth installing and many of the packages in this recommendations section are part of the `tidyverse`.

``` r
install.packages("tidyverse")
```

### Getting data in and out of R

The following packages can be used to get data into, and out of R:

-   Working with databases, you can use the `DBI` package and it's companion `odbc` to connect to most databases
-   To get data from web pages, you can use `rvest`
-   To work with APIs, you use `httr`
-   To work with CSVs, you can use `readr` or `data.table`.[6]
-   To work with SPSS, SAS, and Stata files, use `readr` and `haven`

### Data manipulation

The `tidyverse` contains great packages for data manipulation including `dplyr` and `purrr`.

Additionally, a favourite data manipulation package of mine is `data.table`. `data.table` tends to have a bit of a steeper learning curve than the `tidyverse` but it's phenomenal for brevity and performance.

### Data visualisation

-   For static graphics `ggplot2` is fantastic - it adds a sensible vocabulary to help you construct charts with ease
-   `plotly` helps you build interactive charts from scratch or make `ggplot2` charts interactive
-   `leaflet` is a great maps package
-   `ggraph` helps you build effective network diagrams

### Data science

-   `caret` is an interface package to many model algorithms and has a raft of insanely useful features itself
-   `broom` takes outputs from model functions and makes them into nice data.frames
-   `modelr` helps build samples and supplement result sets
-   `reticulate` is a package for talking to Python and, therefore, enables you to work with any deep learning framework that is based in Python. `tensorflow` is a package based on `reticulate` and allows you to work with tensorflow in R
-   `sparklyr` allows you to run and work with Spark processes on your R data
-   `h2o` is a package for working with H2O, a super nifty machine learning platform

### Presenting results

-   `rmarkdown` is the core package for combining text and code and being able to produce outputs like HTML pages, PDFs, and Word documents
-   `bookdown` facilitates books like this
-   `revealjs` allows you to make slide decks using `rmarkdown`
-   `flexdashboard` and `shiny` allow you to make interactive, reactive dashboards and other analytical apps

### Finding packages

As well as using online search facilities like [CRAN](http://cran.r-project.org/search.html) and [rdrr.io](http://rdrr.io) for packages, there are some handy packages that help you find other packages!

-   `ctv` allows you to get all the packages in a given [CRAN task view](http://cran.r-project.org/web/views/), which are maintained lists of package for various tasks
-   `sos` allows you to search for packages and functions that match a keyword

Loading a package
-----------------

To make functions and data from a package available to use, we need to run the `library()` function.

``` r
library("utils")
```

The `library()` function accepts a vector of length 1, so you need to perform multiple calls to the function to load up multiple packages.

``` r
library("utils")
library("stats")
```

Once a package is loaded, you can then use any of it's functions.

You can find what functions are available in a package by looking at it's help page.

Alternatively, you can type the package's name and hit Tab. This auto-completes the package's name, adds two colons (`::`) and then shows the list of available functions for that package. The double colon trick is very helpful for when you want to browse package functionality.

``` r
utils::find()
```

<p>
Any function in R can be prefixed with it's package name and the double colon (<code>::</code>) - this is great for telling people where functions are coming from and for tracking dependencies in long scripts.
</p>

Learning how to use a package
-----------------------------

R documentation is some of the best out there.

Yes, I will complain about the impenetrable statistical jargon some package authors use, but the CRAN gatekeepers require that packages generally have a really high standard of documentation.

Every function you use will have a help page associated with it. This page usually contains a description, shows what parameters the function has, what those parameters are, and most importantly, there's usually examples.

To navigate to the help page of an individual function in an R package you:

-   Hit F1 on a function name in a script
-   Type `??fnName` and send to the console

``` r
??mean
```

-   Search in the Help tab
-   Use the `help()` function to open up the packages index page and navigate to the relevant function

``` r
help(package="utils")
```

-   Find the relevant package in the Packages tab and click on it. Scroll through the index that opens up on the Help page to find the right function

As well as the function level documentation, good packages also provide a higher level of documentation that covers workflows using the packages, how to extend package functionality, or outlines any methodologies or research that led to the package.

These pieces of documentation are called **vignettes**. They are accessible on the package's index page or you can use the function `vignette()` to read them.

``` r
vignette("multi")
```

Summary
-------

R uses functions as the means of performing operations.

Functions can take 0 or more arguments. All arguments may be mandatory, but some can be optional or even undefined.

You can use argument names to provide arguments in different orders to that defined by the function author or to provide them in the case where an ellipsis (`...`) is used in a function.

R functions Exercises
---------------------

Using what you've learned about investigating the components of functions...

1.  Use `pmin()` to find the smallest values element-wise of the three vector `1:51`, `25:75`, `30:-20`
2.  Use `paste()` to combine the upper case letters into a single string with `", "` between each letter
3.  Use `list.files()` to see what files are in your current directory. Return the fully qualified names not just the file names
4.  View the code for `ncol()` and work out how the number of columns is being determined

## R packages bundle functionality and/or data.

You can install packages from the central public repository (CRAN) via `install.packages()` or install them from GitHub with the package `devtools`. R packages contain documentation that helps you understand how functions work and how the package overall works.

When you want to make use of functionality from a package you can either load all of a package's functionality by using the `library()` function or refer to a specific function by prefixing the function with the package name and two colons (`::`) e.g. `utils::help("mean")`.

There are many packages out there for different activities and domain-specific types of analysis. Use online search facilities like [rdrr.io](http://rdrr.io) or [CRAN task views](http://cran.r-project.org/web/views/) to find ones specific to your requirements.

R packages Exercises
--------------------

1.  Install `datasauRus`
2.  Load the library `datasauRus`
3.  Browse `datasauRus`'s help pages
4.  Read the `datasauRus` vignette

