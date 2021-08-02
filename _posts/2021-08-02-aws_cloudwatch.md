---
title: Monitoring Infrastructure with CloudWatch (Writing in progress...)
layout: single
header:
    teaser: /assets/images/aws_cloudwatch.png
author_profile: true
categories: projects
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

When you have an infrastructure in AWS (or even on-premise), *CloudWatch* is a
solution to monitor it; resources to monitor may be databases, virtual machines,
disks, web applications... as on-premise solutions like Nagios. CloudWatch allows
to collect **logs**, **metrics** and **events** in order to improve performance
and optimization. It is important to know that an agent has to be installed inside
an AWS instance (or even on-premise) in order to monitor it using CloudWatch.
