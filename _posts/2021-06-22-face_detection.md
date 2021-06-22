---
title: Face detection and recognition using AI algorithms (writing in progress)
layout: single
header:
    teaser: /assets/images/face_detection_banner.jpg
author_profile: true
categories: project
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

The purpose of this project is to learn to recognize *detected* faces.
First of all, it is a question of detecting the faces (answer the question how to
detect a face), and then, in a second step, it is a question of recognizing the
detected faces (for instance answer the question who is the person in the image).
The applications of face recognition are present in the current life: to unlock mobile phones (for instance Face ID present since the iPhone X), or even in China to control citizens and to assign behavioral scores to them.


## 1. Tools and Python modules

The idea is to consider the similarity between the faces: a small distance if it
concerns the same person, and a large one if it concerns two different persons.
The aim is to obtain a vector that represents a face in a unique way.

I have used several modules:

- *matplotlib.pyplot* to load images and plot them
- *numpy* for manipulating vectors and matrices and computing the distances
- *face_recognition* to have **embeddings** of images, this module contains several trained
deep learning models giving representative vectors of images
- *Open-CV* because there is computer vision, and it can also be used to draw bounding boxes
