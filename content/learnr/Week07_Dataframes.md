---
title: "Dataframes"
---

data.frames
-----------

A **data.frame** is a table similar to what we're used to working with in most data analysis tools. It will contain a number of rows with columns containing different pieces of information. Each column in a data.frame has a datatype but it does not have to be the same datatype as the other columns.

We can construct a data.frame from individual vectors via the `data.frame()` function.

``` r
data.frame(a=1:2,b=c("blue","red"))
```

    ##   a    b
    ## 1 1 blue
    ## 2 2  red

You can also give row names to the rows you end up making, however, I recommend you add these in as a column instead as it'll make them easier to work with long-term.

``` r
baddf <- data.frame(a = 1:2,
                   b = c("blue","red"),
                   row.names = c("First","Second"))

gooddf <- data.frame(a = 1:2,
                   b = c("blue","red"),
                   ID = c("First","Second"))
```

Throughout many of the examples, I'll use the example datasets that are available by default in R.

``` r
View(iris)
```

|  Sepal.Length|  Sepal.Width|  Petal.Length|  Petal.Width| Species |
|-------------:|------------:|-------------:|------------:|:--------|
|           5.1|          3.5|           1.4|          0.2| setosa  |
|           4.9|          3.0|           1.4|          0.2| setosa  |
|           4.7|          3.2|           1.3|          0.2| setosa  |
|           4.6|          3.1|           1.5|          0.2| setosa  |
|           5.0|          3.6|           1.4|          0.2| setosa  |
|           5.4|          3.9|           1.7|          0.4| setosa  |

The `View()` function is specific to RStudio and provides a nice visual grid view of a data.frame and it allows you to search and sort the table for some initial exploration.

More commonly, we'll import data from an outside source.

Importing data.frames
---------------------

You can import data via code, but one of the easiest ways of getting started is to load data via RStudio and have it generate the code for you.

To import data...

1.  Go to the Environment tab and select Import Dataset
2.  Select the relevant type of data you want to import
3.  Browse to the file you want to upload.

You can tweak the advanced settings and then select the *Import* button to load the data directly into memory. Alternatively, you can copy the code it generated for you and paste it into a script. By doing this copy and pasting, you will make the import reproducible. Next time you need to load the data you can just run the code, instead of using the interface again.

If you were tying to do this import you may have gotten an error when you tried to load a file because you don't have some of the required functionality that RStudio expects you to have.

It will tell you the name of the thing you're missing.

Getting information about data.frames
-------------------------------------

Our data.frames are **composites**, they are the result of combining a number of vectors with different data types. As a consequence, when we run our `class()` function, it tells us an object is a `data.frame` and no longer returns the underlying datatype.

``` r
class(iris)
```

    ## [1] "data.frame"

You do not get the number of rows in a data.frame when you run the `length()` function, instead you get the number of columns (This is because a data.frame is actually just a prettily printed list, and each column in an element in said list, and length returns the number of elements overall). Alternatively, you can run the more clearly named `ncol()` function to return the number of columns in a data.frame.

You can get the number of rows via the `nrow()` function.

Similarly to `length()`, the `names()` function when applied to data.frame's only works on the columns, so you can use it to get column names. A clearer alternative is to use the `colnames()` function. You can use `rownames()` to get names for rows, if they exist.

Lists
-----

**List**s are a catch-all object. They literally hold any and all types of the objects covered in this section, including list objects!

You can create lists with the `list()` function, and like with our other objects you can have named and unnamed elements.

At least initially, most people tend to work with their data in a data.frame and may only interact with a list as a consequence of doing something like building a linear regression model. Lists are very common outputs to statistical functions because you need things like a formula, fitted results, coefficients, model metrics, and more. If you do build a model though, there's a bunch of helper functions for extracting different components so you don't even have to think about the fact you're working with a list.

### Getting information about lists

The `length()` function will tell you how many elements there are in a list.

Other object types
------------------

There a number of other object types in R. We aren't going to cover them in detail, because they tend to be used by a small fraction of R users.

-   A **matrix** is a two-dimensional object that can only contain one datatype
-   An **array** is a multi-dimensional object that also can contain only one datatype
-   A **table** object is similar to a matrix but is created by producing a contingency table

In R, developers can also create other object types specific to their requirements. People use this to create geospatial objects and more. I don't recommend you think about creating your own custom objects, especially at this point in your R writing career. If/when you want to write your own custom classes then my preferred package for that is `R6`.

Useful functions
----------------

Whatever the object type, there are some functions that come in handy for exploring it and getting some useful metadata.

You get the contents of any object by writing it's name.

However, if you're working with a lot of data, you probably don't want to fill up your console that way. R has two functions, `head()` and `tail()`, which allow you to see values from the beginning or end of an object. For objects containing many elements, such as lists or data.tables, `head()` and `tail()` returns the first or last 5 values respectively.

If you want to examine an R object, you can use the `str()` function to get the structure of the object.

Summary
-------

You can perform calculations on the fly or store results for later use. You can assign values with the `<-` operator.

Functions like `class()`, `length()`, and `head()` work well to extract information about R objects.

R performs calculations over vectors so that you only have to provide two or more vector names and the operation you want performed. R will then perform this operation pair-wise for the vectors.

You can import datasets in R by using the "Import Dataset" function. This will also give you the code to use so that you can write code that another person will be able to use. This is great because it makes your work reproducible and automatable!

As well as vectors and data.frames, there are list object types and some other object types. These are less commonly used, although lists are quite common when getting outputs from statistical functions.

Homework on objects - this includes some from last week to refresh your memory.
-------------------------------------------------------------------------------

Make a new script and save your code in there.

1.  See what's in the built-in variable `letters`
2.  Write a check to see if "A" is present in `letters`
3.  Find out which values in the sequence 1 to 10 are greater than or equal to 3 and less than 7
4.  Make a vector containing the numbers 1 to 50
5.  Make a vector containing two words
6.  What happens when you combine these two vectors?
7.  Make a data.frame using the two vectors
8.  What happened to your text vector?
9.  Make a list containing some of the variables you've created so far
10. Retrieve the head or tail of the `iris` dataset

