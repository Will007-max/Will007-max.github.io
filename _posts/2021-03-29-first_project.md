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

Completing my data science bootcamp, I wanted to realize a great interesting project allowing me to develop new skills and deeply apply the majort part of what I learned. And, for me, what could be better than ***Deep Learning*** ? ... as in this context, models are trained with a large amount of data, many of them are already pre-trained, and we apply *transfer learning* to have great performances.  Based on my knowledge on some possible machine learning applications around us, in my project I wanted to analyze video streaming in order to detect and predict emotions. It could be interesting for many applications like security cameras, job interviews, call centers, improving the quality of customer service, and why not in our interactions with smart devices...

Because emotions may be expressed on faces (facial expressions), via voice tones and body language, a priori, this can be done by simultaneously processing video and audio streaming. I was wondering if this sort of project could be achieved within the time frame (less than a month). Basically, I have a good scientific background, so I can quickly learn a lot of things. But, I didn't know if it was enough since I never managed this kind of project, in addition it was not my main scientific topic (so, many things to learn from scratch).

I was even wondering where to find data to feed to my machine learning algorithms, and how to train them ? I meant what kind of models could be applied in order to have great performances. In addition, could I locally train my models ? or must I use cloud infrastructures and/or online notebooks and frameworks ? Another point was to getting started and to learn the main concepts to master and manage my project. One of my supervisor suggested me to simply start with audio processing since for a start, it might be quite challenging to work on both channels.

One goal was to online deploy the project: using a web app with [Flask](https://flask.palletsprojects.com/), a REST API with [FastAPI]('https://fastapi.tiangolo.com'), [Plotly Express](https://plotly.com/python/plotly-express/) and [Dash](https://dash-gallery.plotly.host/Portal/), or even [Streamlit](https://streamlit.io)... indeed during the data science training, we learn some interesting ways for doing this kind of implementation even including Docker and Kubernetes to deploy on servers in the Cloud. I thought this part of my project was the easiest because I was able to handle it comfortably.

## II. First steps

As suggested by a supervisor, I started by taking a look at all **HuggingFace** libraries where several pre-trained models (in natural language processing as well as voice processing) are available and just need to be fine-tuned with additional data. There are always many resources in other languages like German and Spanish... A main concept in HuggingFace deals with ***transformers***: it is a kind of state-of-the-art, but several others libraries are available and could always be used... As in most cases, handling new tools is still challenging, in order to start mastering it, I looked at basic examples where *transformers* are used.

We need data to train machine learning models, and in order to draw the best conclusions, they must be appropriate for the current problem we want to solve. Some audio datasets are available on Kaggle, one specifically very interesting is the [Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS)](https://zenodo.org/record/1188976#.YF5hwC1Q2Rs) dataset, as it contains both audio and video recordings. So, this part could already be considered as done. Another point was to start implementing on *Google Colab* in order to leverage GPU computing; in addition, HuggingFace already contains many *Colab* notebooks to fine-tune algorithms.

Since I had to use *Google Colab*, I started by importing all needed files in my *Google Drive*. I wanted to extract features from different files in order to feed a machine learning model. The dataset contains many files grouped in folders (voice categories, actors...) and the name of each voice file contains informations: in that order there are in sequence  *modality* (01 = audio and video, 02 = video only, 03 = audio only), *voice channel* (01 = speech, 02 = song), *emotion* **(01 = neutral, 02 = calm, 03 = happy, 04 = sad, 05 = angry, 06 = fearful, 07 = disgust, 08 = surprised)**, *emotional intensity* (01 = normal, 02 = strong). For each file, it is necessary to match the extracted features with its corresponding name (path) and label, and stored all in a dataframe to ease future data manipulations.

## III. Starting with HuggingFace and Librosa libraries

My first research about *transformers* applied to audio led me to automatic speech recognition (ASR). A library dealing with audio files is Wav2Vec, it is similar to Word2Vec which is used for word embeddings: *meaningful embeddings (vectors) are learned from raw data* (audio or text).

It is usually established that emotion detection in speech may be done through linguistics (words are used for semantics) and/or paralinguistics (acoustic waves from audio).

Talking about transformers, in the case of speech emotion recognition, we can ask to ourselves if the trained *contextual* representations of raw audio (obtained from Wav2Vec for instance) also contain emotional content. To answer this question, it might be interesting to compare performance resulting of the use of these representations to performance with other descriptors like the spectrogram features or Mel-Frequency Cepstral Coefficients (MFCC) resulting from Fourier analysis of the audio file in the frequency domain.

### III.1. Extraction of MFCC features using Librosa


### III.2. Audio features with Wav2Vec2
