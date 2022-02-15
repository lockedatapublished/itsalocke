---
title: "R and RStudio"
author: "Ellen Talbot"
date: "2017-12-08T00:00:00.000Z"
weight: 10
output: html_document
---

About R
-------

R is an open source language released in 2001 that's ideal for [data wrangling](https://en.wikipedia.org/wiki/Data_wrangling) and [data science](https://en.wikipedia.org/wiki/Data_science). It has connectors to pretty every much every data source under the sun, allows you wrangle data like nobody's business, build pretty much every type of model ever thought up, and visualise it in all the niftiest ways. These superlatives are not disingenuous, R really is that broad and amazing.

R is a vibrant ecosystem that enables people to extend, enhance, and replace any part of it. There are many paradigms in R to facilitate object-oriented programming, functional programming, and more. If you can write something in C++, FORTRAN, Python, or JavaScript--and of course, R!--you can write extensions for R.

There are currently more than eleven thousand extensions (referred to as packages) to R in the core ecosystem (which is a fancy word for the collected bits and pieces of R!) and two and a half thousand packages in the genomics ecosystem.

We're also seeing emerging ecosystems and paradigms within CRAN. The [tidyverse](http://tidyverse.org/) is one such ecosystem, focussed primarily on analysing tabular data, and it will be used in future works extensively.

CRAN
----

The core ecosystem is **CRAN**, the Comprehensive R Archive Network. [CRAN](https://cran.r-project.org) is maintained by some great people who put in place a large number of quality gates that an R package must adhere to in order to be made widely available. They then host these packages and do great things like daily re-runs of all package tests to ensure packages are still working. CRAN is the default source of packages for most R users.

If you use RStudio, you'll use a **mirror** of CRAN hosted by RStudio. There are a number of these mirrors scattered over the globe to help reduce the load on the central servers. You can use another one of these mirrors, or even set-up your own internal CRAN.

Key points to know about R
--------------------------

-   R works in-memory which means that the processing is fast but the amount of data you can process is limited to how much RAM your data takes up and how much your computations will require.
-   R is not multi-threaded by default, it works on a single CPU core. Making use of more than one of your cores to spread the load requires additional packages and often additional coding.
-   R is quirky! In some ways, R is a lot like other common programming languages, which can make it pretty easy to pick up. However, because R is still designed to be compatible with S, it's actually pretty darn old and as a result, really odd in places.
-   Coding R will give you the typical gotcha's, and add another: case sensitivity. R is (un)fortunately a language where "Red" and "red" are different and this also extends to variable and function names (which we'll discuss later.) As a consequence, the most common errors you'll find when writing code in R are:
    -   Incorrectly placed or missing commas
    -   Incorrectly placed or missing brackets
    -   Incorrectly placed or missing operators
    -   Incorrect case used when typing
-   With so many packages available to extend R, the answer to "how do I write this?" is usually "there's more than one package for that".

Summary
-------

R is an great language for doing data analysis, data science, and more. It has it's quirks but the community around it is huge and is making R easier to adopt every day.

Why use R?
----------

R as a programming language is brilliant at its core competencies -- statistics and data visualisation. It's also a great "glue" language, by which I mean that you can use it to perform computations in many different languages and combine the results smoothly. As a result, R enables you to be an effective data wrangler, data scientist, and/or data visualisation practitioner.

So, now we've done the hard sell, here's some fun stuff... and you can't even acuse us of being on commision...because R and RStudio are totally free (*yes free*) to download and use what with them being opensource and whatnot.

RStudio
=======

[RStudio](http://rstudio.com) is a coding interface to R that makes it easier for you to be productive.

The interface will be split up into a top menu and then four panes, although only three may be visible when you first start RStudio.

The console
-----------

The (bottom) left hand section is the console. This is where you can execute R code directly.

To use the console you type some code alongside the `>` and hit <kbd>Enter</kbd> for the code to be executed. The result will then appear underneath your line of code.

If the code you entered wasn't a complete statement e.g. `1 + 2 +`, when you hit <kbd>Enter</kbd> , you'll get a new line only the `>` will now be a `+`. This indicates the code you're writing is a continuation of the previous line. R will allow you to continue building up a complete chunk of code this way. It'll run all the lines you entered as one block once it's been completed.

If you want to clean your console and start afresh, hit <kbd>Ctrl</kbd> + <kbd>L</kbd> to remove whatever has been executed in the console this session.

You can use your up and down arrow keys to navigate through previous code you've written and executed.

Scripts
-------

RStudio allows you to create and work with files containing code. These files give you a way to store and manage your code.

The most common file types you might use are R files (`.R`) and rmarkdown files (`.Rmd`). You can create one of these files by going to *File &gt; New &gt; R Script*, the New File button, or with the hotkey combo of <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>N</kbd> .

In an R script you can type code and execute it by hitting <kbd>Ctrl</kbd> + <kbd>Enter</kbd>, or selecting the code to run and hitting the Run button.

You can execute all the code in a script by hitting <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Enter</kbd> or hitting the Source button.

Code completion
---------------

Whilst writing scripts or typing in our console, we can get help and be more productive by using **code completion**. Code completion will pick up from what we've typed so far and provide a navigable list of suggestions.

As we navigate through the list, it'll provide help text where possible and then it will complete the code we were typing.

-   You access the code completion by hitting <kbd>Tab</kbd> whilst typing
-   Once it's up you can keep typing to refine the list
-   Your arrow keys allow you to navigate the list
-   Hit <kbd>Esc</kbd> to back out of the completion capability
-   Hit <kbd>Tab</kbd> to accept whatever value in the list is currently highlighted

Projects
--------

So far you've seen R as a scratch-pad (via the console) and for making an isolated script, but a lot of the time we have to put data, multiple scripts, documentation and more into a **project**.

An RStudio project is a folder with an extra file. This file can be used to open RStudio, with everything laid out like it was before you closed the project. It can store preferences to allow projects to vary from the way you normally do things.

You can, and should, create a new R project when embarking on a new area of work. To create a project go to *File &gt; New Project*.

This will popup a dialogue that gives you the option to create a brand new project directory, create one from some existing directory you might already have, or create one with the content of a project in your source control system (we'll talk about source control in a later book.)

Most commonly, you'll want to create a new directory project. Once selected it'll then give you the option to create an empty project, a Shiny project (a feature for creating amazing dynamic reports,) or an R package. You'll normally select the empty projects. Once an option is selected, provide a name and where the project should go.

Summary
-------

RStudio is a fantastic environment for learning R and writing R code going forward.

Using code completion can be a great help in finding what to write and how to write it.

Other areas of the RStudio interface will be introduced as we go forward but taking the time to get to know the environment now will help you be more productive in future.

Homework and extra reading for the real keen beans
-----------
- Here at Locke Data have been working hard on putting together a series of quick reference videos to go alongside this series, so watch our first instalment to consolidate everything we've covered today - and to put a face to the name behind the series (and the dodgy dad jokes).

{{< youtube 8BAb0irAK2U >}}

-   If you don't already have it, you should [install R and RStudio](http://www.rstudio.com/products/rstudio/download/#download).
-   Find and follow three R or RStudio related twitter accounts or blogs \*hint: use the hashtag \#rstats
-   Have a flick through this great all round guide! - **R for Data Science: Visualize, Model, Transform, Tidy, and Import Data** An end-to-end introduction to R [geni.us/rfords](http://geni.us/rfords)
-   Watch these intro videos showing what we've talked about above.
    -   [Using the console] (https://youtu.be/2hg1Qg7uLwU).
    -   [New Scripts](https://youtu.be/rWHV2VlQo2w).
    -   [Code completion](youtu.be/pGOF4gTyeXA).
    -   [New projects](https://youtu.be/etkSsF6r2iU).
-   Set up an R Project called "Locke\_Homework"
-   Create an R Script in your project.


*Still not had enough? Here's an optional extension task you could do if you need to look busy at work in the awkward five minutes before you can go and wash your mug to kill another five minutes before you can go home.*

- Andy Field has built an awesome R Package to go alongside his book "Adventures in R". If you're not quite box fresh new to R and R Studio, go and have a look at [his website](http://milton-the-cat.rocks/home/index.html) and work through his first adventure!



