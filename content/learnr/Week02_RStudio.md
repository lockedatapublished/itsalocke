+++ 
title = "RStudio" 
lastmod = "2017-12-20" 
date = "2017-12-20"
[elements] 
footer = true 
contact = true

[menu.footer] 
name = "About Locke Data" 
weight = 10

[style] 
center = false 
+++

RStudio
=======

[RStudio](http://rstudio.com) is a coding interface to R that makes it
easier for you to be productive.

The interface will be split up into a top menu and then four panes,
although only three may be visible when you first start RStudio.

The console
-----------

The (bottom) left hand section is the console. This is where you can
execute R code directly.

To use the console you type some code alongside the `>` and hit
<kbd>Enter</kbd> for the code to be executed. The result will then
appear underneath your line of code.

If the code you entered wasn't a complete statement e.g. `1 + 2 +`, when
you hit <kbd>Enter</kbd> , you'll get a new line only the `>` will now
be a `+`. This indicates the code you're writing is a continuation of
the previous line. R will allow you to continue building up a complete
chunk of code this way. It'll run all the lines you entered as one block
once it's been completed. 

*But - if the extra '+' was a mistake, hit <kbd> Esc</kbd> and you'll be right back on track.*

*You'll do this a lot. I know. I do it a lot.*


If you want to clean your console and start afresh, hit <kbd>Ctrl</kbd>
+ <kbd>L</kbd> to remove whatever has been executed in the console this
session.

You can use your up and down arrow keys to navigate through previous
code you've written and executed.

Scripts
-------

RStudio allows you to create and work with files containing code. These
files give you a way to store and manage your code.

The most common file types you might use are R files (`.R`) and
rmarkdown files (`.Rmd`). You can create one of these files by going to
*File &gt; New &gt; R Script*, the New File button, or with the hotkey
combo of <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>N</kbd> .

In an R script you can type code and execute it by hitting
<kbd>Ctrl</kbd> + <kbd>Enter</kbd>, or selecting the code to run and
hitting the Run button.

You can execute all the code in a script by hitting <kbd>Ctrl</kbd> +
<kbd>Shift</kbd> + <kbd>Enter</kbd> or hitting the Source button.

Code completion
---------------

Whilst writing scripts or typing in our console, we can get help and be
more productive by using **code completion**. Code completion will pick
up from what we've typed so far and provide a navigable list of
suggestions.

As we navigate through the list, it'll provide help text where possible
and then it will complete the code we were typing.

-   You access the code completion by hitting <kbd>Tab</kbd> whilst
    typing
-   Once it's up you can keep typing to refine the list
-   Your arrow keys allow you to navigate the list
-   Hit <kbd>Esc</kbd> to back out of the completion capability
-   Hit <kbd>Tab</kbd> to accept whatever value in the list is currently
    highlighted

Projects
--------

So far you've seen R as a scratch-pad (via the console) and for making
an isolated script, but a lot of the time we have to put data, multiple
scripts, documentation and more into a **project**.

An RStudio project is a folder with an extra file. This file can be used
to open RStudio, with everything laid out like it was before you closed
the project. It can store preferences to allow projects to vary from the
way you normally do things.

You can, and should, create a new R project when embarking on a new area
of work. To create a project go to *File &gt; New Project*.

This will popup a dialogue that gives you the option to create a brand
new project directory, create one from some existing directory you might
already have, or create one with the content of a project in your source
control system (we'll talk about source control in a later book.)

Most commonly, you'll want to create a new directory project. Once
selected it'll then give you the option to create an empty project, a
Shiny project (a feature for creating amazing dynamic reports,) or an R
package. You'll normally select the empty projects. Once an option is
selected, provide a name and where the project should go.

Summary
-------

RStudio is a fantastic environment for learning R and writing R code
going forward.

Using code completion can be a great help in finding what to write and
how to write it.

Other areas of the RStudio interface will be introduced as we go forward
but taking the time to get to know the environment now will help you be
more productive in future.

Homework for the keen beans
---------------------------

-   Watch these intro videos consolidating the above.
    -   Using the console
        [youtu.be/2hg1Qg7uLwU](https://youtu.be/2hg1Qg7uLwU).
    -   New Scripts
        [youtu.be/rWHV2VlQo2w](https://youtu.be/rWHV2VlQo2w).
    -   Code completion [youtu.be/pGOF4gTyeXA](youtu.be/pGOF4gTyeXA).
    -   New projects
        [youtu.be/etkSsF6r2iU](https://youtu.be/etkSsF6r2iU).
-   Set up an R Project called "Locke\_Homework"
-   Create an R Script in your project.

