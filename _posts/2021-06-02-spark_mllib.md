---
title: Spark for machine learning
layout: single
header:
    teaser: /assets/images/spark_mllib.png
author_profile: true
categories: tech_blog
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

Some tricks...

- To load a CSV file, you may use the **spark.read.csv()** method

- The different datatypes in MLlib are DataFrame and RDD, Vector, LabeledPoint,
Local matrix and Distributed matrix (only in Java and Scala)

- The two reasons why PySpark is useful for data scientists are: it enables
scalable analysis, ML pipelines. It is also easy to work with because of its
familiarities with Scikit-learn and Pandas. The main drawback of Scikit-learn and
Pandas when building predictive models is that Scikit-learn **doesn't scale to**
**large datasets** in a distributed environment (no task parallelisation)

- To convert a PySpark dataframe into a Pandas one, you can use the **toPandas()**
method. Be careful when using it because all data are **loaded into memory** on
the driver node and prevents operations from being performed in a **distributed mode**

- Before the training of your algorithm in MLlib, you need to create a **vector**
**representation** of the features that you'll use, as in the following:

```python

from pyspark.ml.feature import VectorAssembler

assembler = VectorAssembler(inputCols=['col1', 'col2', 'col3'],
                            outputCol='features')
train_df = assembler.transform(df)

```

- It is easy to make predictions on a test set:

```python

pipeline = Pipeline(stages=[vector_assembler, classifier])

model = pipeline.fit(train)

predictions = model.transform(test)

```

- You can combine multiple algorithms (transformers and an estimator) into a
single pipeline with **SparkML**
