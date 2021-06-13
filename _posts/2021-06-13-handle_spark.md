---
title: Handle Spark
layout: single
header:
    teaser: /assets/images/spark_cluster_mode.jpg
author_profile: true
categories: tech_blog
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

## 1. Introduction

Here, we will deal with job optimizations: understanding and mastering the performance of Spark applications. To know how to optimize the traffic with Spark, you have to answer this question: How will Spark process the data ? This article is about how Spark works.
First, we will talk about the Spark API. Then, there is the execution model i.e. everything that is involved in the execution of a Spark job, how it runs. Then, there is the monitoring: we have an execution model and we know more or less what's going on, the idea is to monitor what's going on, how we can have an idea of what Spark is doing when it does its calculations. Finally, we'll talk about *Catalyst* which is the system that processes SQL queries and dataset queries in Spark, and which is a sort of main engine of Spark.

## 2. Spark API

When working with Spark, there are 3 possible API:

- RDD (Resilient Distributed Datasets) that has been firstly created,

- Dataframes (introduced with SQL, and structured with columns)

- Datasets (the last one)
