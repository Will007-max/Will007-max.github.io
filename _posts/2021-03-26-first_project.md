---
published: true
title: Organizing my first ML project
collection: ml
layout: single
author_profile: true
read_time: true
categories: [machinelearning]
excerpt : "Writing"
header :
    #overlay_image: "https://maelfabien.github.io/assets/images/wolf.jpg"
    #teaser : "https://maelfabien.github.io/assets/images/wolf.jpg"
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

<!--src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script> -->

Here are some words about how I wrote and organized my first project. Who know, it may be useful in some context.

## I. Context

Completing my data science bootcamp, I wanted to realize a great interesting project allowing me to develop new skills and deeply apply the majort part of what I learned. And, for me, what could be better than ***Deep Learning*** ? Based on my knowledge on some possible machine learning applications around us, in my project I wanted to analyze video streaming in order to detect and predict emotions. It could be interesting for many applications like security cameras, job interviews, improving the quality of customer service...

Because emotions may be expressed on faces and/or via voice tones, a priori, this can be done by simultaneously processing video streaming, audio and *(transcripted)* text. I was wondering if this sort of project could be achieved within the time frame (less than a month). Basically, I have a good scientific background, so I can quickly learn a lot of things. But, I didn't know if it was enough since I never managed this kind of project, in addition it was not my main scientific topic (so, many things to learn from scratch).

I was even wondering where to find data to feed to my machine learning algorithms, and how to train them ? I meant what kind of models could be applied in order to have great performances. In addition, could I locally train my models ? or must I use cloud infrastructures and/or online notebooks and frameworks ? Another point was to getting started and to learn the main concepts to master and manage my project. One of my supervisor suggests me to simply start with audio and text processing since it might be quite tricky with the three channels.

One goal was to online deploy the project: using a web app with Flask, a REST API with FastAPI, and Heroku, Plotly Express and Dash, or even Streamlit... indeed during the training, we learn some interesting ways for doing this kind of implementation even including Docker and Kubernetes to deploy on servers in the Cloud. I thought this part of my project was the easiest because I was able to handle it comfortably.

## II. First steps

As suggested by a supervisor, I started by taking a look at all **HuggingFace** libraries where several pre-trained models (in natural language processing as well as voice processing) are available and just need to be fine-tuned with additional data. There are always many resources in other languages like German and Spanish... A main concept in HuggingFace website deals with ***transformers***: it is a kind of state-of-the-art, but several others libraries are available and could always be used... As in most cases, handling new tools is still challenging, in order to start mastering it, I looked at basic examples where *transformers* are used.

In order to train machine learning models, we have to use data. Those data must be appropriate for the current problem in order to draw the best conclusions. Firstly, I found some available datasets on Kaggle: [Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS)](https://zenodo.org/record/1188976#.YF5hwC1Q2Rs). So, this part could already considered as done. Another point was to start implementing on Google Colab in order to leverage GPU computing; in addition, HuggingFace already contains many *Colab* notebooks to fine-tune algorithms.

Since I had to use *Google Colab*, I started by importing all needed files in my *Google Drive*.
