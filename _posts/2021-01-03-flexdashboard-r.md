---
title: 'Flexdashboards in R'
date: 2021-01-03
permalink: /posts/2021/flexdashboard-r/
tags:
  - Flexdashboard
  - R
  - Docker
  - Docker Compose
  - Shinyproxy
  - Heroku
---

Dashboards have become quite popular recently because of their ability to summarize the data in an easy and inituitative manner. A prime example have been COVID-19 dashboards which have been quite powerful to keep track of the several metrics of COVID-19 cases, infections, recoveries and finally deaths etc., Flexdashboards are 

Flexdashboard are an easy interactive dashboards for R built using `flexdashboard` package in R. They

* Use R Markdown to publish a group of related data visualizations as a dashboard.

* Support for a wide variety of components including htmlwidgets; base, lattice, and grid graphics; tabular data; gauges and value boxes; and text annotations.

* Flexible and easy to specify row and column-based layouts. Components are intelligently re-sized to fill the browser and adapted for display on mobile devices.

* Storyboard layouts for presenting sequences of visualizations and related commentary.

* Optionally use Shiny to drive visualizations dynamically.

In this series of blogposts, I am going to show how you can create flexdashboard in R, package it, create an login page, deploy it on cloud etc., Here are the topics which will be covered in details in full

1. [How to create a flexdashboard in R](https://upendrak.github.io/posts/2021/flexdashboard-r/create-flexdashboard-r)

2. [How to package the flexdashboard using Docker and Docker Compose](https://upendrak.github.io/posts/2021/flexdashboard-r/package-flexdashboard-r-docker)

3. [Create a log-in page for the flexdashboard using Shinyproxy](https://upendrak.github.io/posts/2021/flexdashboard-r/create-login-flexdashboard-r)

4. [How to deploy the flexdashboard using Heroku](https://upendrak.github.io/posts/2021/flexdashboard-r/deploy-flexdashboard-r)