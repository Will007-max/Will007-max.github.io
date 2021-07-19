---
title: AWS (writing in progress...)
layout: single
header:
    teaser: /assets/images/aws_storage.png
author_profile: true
categories: projects
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

Amazon S3 (standing for *Simple Storage Service*) is a service used by many
companies and it enables storage of files. For instance, it is possible to host
static websites on Amazon S3, store images and videos, archives, save application
states (logs). It is part of what is called *object storage*.

The goal here has been to create storage spaces via S3, know how to use the S3
service, how to use an image already stored in the Cloud.

It started by connecting on the AWS Management Console, and I choosed S3 in the
**Storage** group, then I had this page (see the following figure) suggesting to
create a bucket. The **bucket** can be seen as a container to store the **objects**
representing our files and images. For information, on S3, objects have a size
limit (of about 160 GB), there can be a maximum of 100 buckets per AWS account,
however each bucket can contain as many objects as desired and thus allows to
store a "virtually" unlimited amount of data. One constraint is the unicity of the
bucket name over Internet since it appears on the files URLs. Amazon S3 provides
APIs to manage all these resources.

![Image](/assets/images/aws_storage_s3_bucket.png#center)

As you can see in the following figure, I created a bucket and inside I uploaded some files. In AWS S3, each uploaded file has an URL enabling its access from a browser but  before, you have to make public both the bucket (containing the file) and the file so that
you don't get a (by default) denied access.

![Image](/assets/images/aws_s3_bucket_files.jpg#center)

The created and uploaded files are from a small HTML page. In "img" HTML tags, I
put the corresponding URL from S3 as values of the "src" attributes, and as you
can see in the next figure the web page is well displayed with everything that is
stored in an AWS S3 bucket.

![Image](/assets/images/aws_s3_bucket_webpage.jpg#center)
