+++
draft = false
thumbnail = "/img/MachineLearning.png"
date = "2017-06-26"
title = "Data + Docker = Discombobulating?"
tags = ["infrastructure","docker"]
categories = ["DataOps"]
+++

Learn about Docker and how you can store data in Docker containers safely.

## Abstract
If you’re like me, you like your data to stick around for a long time and most importantly you want to know it’s *safe*.

In the Docker world, there’s the maxim of “never patch”, always make a new container with the latest version of the application. If we’re sticking in our database in a container like Microsoft are doing with SQL Server now, what happens when we need to apply the latest patches? Will we lose our data?

In this talk, we’ll look at the sorts of data we need to think about (it’s not just databases!) and how Docker containers work. We’ll then look at how we can save our data from disappearing when we load a new version of our Docker container. Once we know how to safeguard ourselves, we’ll look at some of the architectural options you have when working with data and Docker.

## Slides
View the presentation [full screen](http://stephlocke.info/datadockerdisconbobulating/datadockerdisconbobulating.html) or view it below. Hit the Space bar to navigate through the slides.

<iframe src="http://stephlocke.info/datadockerdisconbobulating/datadockerdisconbobulating.html" width="960" height="540"></iframe>

Get more info and supporting scripts in the [repository](https://github.com/stephlocke/datadockerdisconbobulating).

## Videos
{{< vimeo 204426728 >}}

## Presentation history
- November 3rd, 2016 - [Bris.tech](http://2016.bris.tech/)
- January 18th, 2017 - [NDC London](http://ndc-london.com/)
- June 26th, 2017 - [R & SQL Northeast](http://attending.io/events/r-north-june-26-2017)
- July 4th, 2017 - [Devteach](http://www.devteach.com)

