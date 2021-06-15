---
title: Handle Spark (writing in progress...)
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

- **RDD (Resilient Distributed Datasets)** that has been firstly created. It is like a
sequence but is distributed over the machines. As you may know, there are two types of operations that can be performed on a RDD: transformations and actions. On the one hand, transformations "transform" a RDD to another one; there are **narrow** transformations where there is no need to re-mix the data (eg: map, flapMap, filter, union...), and **wide** transformations needing synchronization (shuffle), and where all the values of the same key have to be mixed on all the possible partitions (eg: distinct, groupByKey, reduceByKey, join...). On the other hand, actions transform a RDD to something else: an action may be *collect* (a table), *saveAsTextFile* (a file), *reduce* (a single value), *take*, *count*, *foreach*... and at the end, there is something new that is no longer a RDD.

```python
sc.textFile("wikipedia")
  .flatMap(line => line.split(" "))
  .map(word => (word, 1))
  .reduceByKey(_ + _)
  .saveAsTextFile("wordcount")
```

- **Dataframes** that have been introduced with Spark SQL, and structured with columns. It is always a sequence but here it is a sequence of *Map[String, Any]* where we have a column name associated with a value. From an API point of view, things are a little big diffrent compared with a RDD: here, the data are structured in columns, and to make operations here we use the functions and SQL.

```python
import spark.implicits._
import org.apache.spark.sql.functions._

df = sqlContext.read.text("wikipedia") # to create a new DataFrame with words column
wordsDF = df.select(split(df("value"), " ").alias("words")) # equivalent of using flatMap() method on RDD
wordDF = wordsDF.select(explode(wordsDF("words")).alias("word")) # a DataFrame with each line containing single word in the file
wordCountDF = wordDF.groupBy("word").count()
```

- **Datasets** that are the last one created. They are sequence like RDD, and DataFrame is now a special type of Dataset.


## 3. Execution model

In Scala, once launched the program, everything starts with a driver, it is the process that monitors calculations by the executors.

Some words about the vocabular related to the execution model.
- Tasks are processing units for executors.
- A stage is an ensemble of tasks that must be parallelized (distributed) and simultaneously executed.
- Shuffle is between two stages to transfer data through the network across the partitions.
- A job is an ensemble of stages
- Very often, an action is one job
- By default, there is only 1 stage / job
- 1 *"wide"* transformation = 1 new stage

The number of tasks depends on how Spark has been parallelized, and it is data driven.

**Driver and cluster manager:** *Spark shell* vs *spark-submit*
When executed from any machine (inside or outside the cluster depending on the deployment mode), the configuration is created, the resources are deployed, and the driver is launched. This is illustrated on the following figures for ***client mode*** and ***cluster mode***.

![Image](/assets/images/spark_client_mode.jpg#left) ![Image](/assets/images/spark_cluster_mode.jpg#right)

```python
spark-submit # to create a configuration to pass to the cluster manager
    --master yarn # it is the most frequent case, here the cluster type
    --deploy-mode client # the deployment mode: either client or cluster
              # in the client mode, the driver is not inside the cluster
              # The application master communicates with YARN whereas the driver masters the executors

              # the how many ressources to do a job, else default parameters
    --num-executors 2
    --executor-cores 4
    --executor-memory 8G
    --class Myclass # the class to be executed i.e. the programm start
    mypackage.jar
```

## 4. Monitoring

The question here is how I know what's going on in Spark. For this purpose,
there are three systems available: *logging*, *event history*, *metrics*.
