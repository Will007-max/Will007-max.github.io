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
First, we will talk about the **Spark APIs**. Then, there is the **execution model** i.e. everything that is involved in the execution of a Spark job, how it runs. Then, there is the **monitoring**: we have an execution model and we know more or less what's going on, the idea is to monitor what's going on, how we can have an idea of what Spark is doing when it does its calculations. Finally, we'll talk about ***Catalyst*** which is the system that processes SQL queries and dataset queries in Spark, and which is a sort of main engine of Spark.

## 2. Spark APIs

When working with Spark, there are 3 possible API:

- RDD (Resilient Distributed Datasets) that has been firstly created. It is like a
sequence but is distributed over the machines. As you may know, there are two types of operations that can be performed on a RDD: transformations and actions. On the one hand, transformations "transform" a RDD to another one; there are **narrow** transformations where there is no need to re-mix the data (eg: map, flapMap, filter, union...), and **wide** transformations needing synchronization, and where all the values of the same key have to be mixed on all the possible partitions (eg: distinct, groupByKey, reduceByKey, join...). On the other hand, actions transform a RDD to something else: an action may be
*collect* (a table), *saveAsTextFile* (a file), *reduce* (a single value), *take*,
*count*, *foreach*... and at the end, there is something new that is no longer a RDD.

- Dataframes (introduced with SQL, and structured with columns)

- Datasets (the last one)
