---
title: Spark for machine learning
layout: single
header:
    teaser: /assets/images/spark_mllib.png
author_profile: true
categories: technos
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

The two reasons why PySpark is useful for data scientists are: it enables
scalable analysis, ML pipelines. It is also easy to work with because of its
familiarities with Scikit-learn and Pandas. The main drawback of Scikit-learn and
Pandas when building predictive models is that Scikit-learn **doesn't scale to**
**large datasets** in a distributed environment (no task parallelisation). Spark can be used for scalable machine learning, and SparkML aims to do in a distributed way
all the possible algorithms of Scikit-learn.

Some reminders...

- *spark = SparkSession.builder.appName('spark test').getOrCreate()* to build a Spark
session.

- *df = spark.read.load(path, header...)* allows to load data and Spark finds itself the data type.
And for instance, to load a CSV file, you may especially use the **spark.read.csv()** method

- *df_table = df.registerTemplate('table_name')* allows to create a database table
to save data from a dataframe, and it is now possible to do SQL queries using *spark_sql.sql(SELECT * FROM table_name)*, where *spark_sql = SQLContext(spark)*
is a created Spark SQLContext.

- To convert a PySpark dataframe into a Pandas one, you can use the **toPandas()**
method. Be careful when using it because all data are **loaded into memory** on
the driver node and prevents operations from being performed in a **distributed mode**

```python
df_pandas = df_spark.select('*').toPandas()
```
Here all the dataframe columns have been saved.



Some tricks...

- MLlib has many features and functions: **basic statistics** (hypothesis tests, correlation, random generators...), **multidimensional exploration** (unsupervised classification, dimensionality reduction...), **learning linear methods** (SVM, gradient boosting, regression...)

- The different datatypes in MLlib are **DataFrame and RDD** (natively), **Vector** (Dense, and Sparse that stores only the non-zero elements), **LabeledPoint** (for example, the label is given and followed by a list of all the features values),
**Local matrix and Distributed matrix** (only in Java and Scala)

- Machine learning algorithms are found in **pyspark.mllib.regresion**,
**pyspark.mllib.classification** and **pyspark.mllib.clustering**

- When working with supervised algorithms, MLlib expects a column of features. So, before the training of your algorithm in MLlib, you need to create a **vector**
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
