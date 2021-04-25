---
title: Video streaming analysis to detect emotions
layout: single
tilte: 'My Projects'
permalink: /projects/
author_profile: true
read_time: true
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

Currently, I am realizing several machine learning projects, the main is focused on deep learning for processing audio and videos in order to determine emotions in communication.

The analysis of emotions in a video streaming can be done by exploiting two channels: audio streaming, and the image sequence. In a first step, I only focused on audio.

*MFCC coefficients* have been the state of the art in audio natural language processing. Research continues to be conducted for a better exploitation of audio to improve the applications of artificial intelligence in everyday life. Considering this point, I found it appropriate to use this first approach to extract interesting features to feed to machine learning algorithms for prediction.

# I. Working with audio files

## I.1. MFCC features using Librosa

Many Python librairies deal with signal and audio processing, here I only talk about Librosa. For a better understanding, I would start by reminding some concepts upstream of the MFCC coefficients.

### I.1.1. Audio representations

#### I.1.1.1. Audio wave

Sound is a mechanical wave that is transmitted from a source in an elastic medium. The perturbation is a local change of the atmospheric pressure causing the vibrations of the air molecules. Human beings and many animals feel this wave through the sense of hearing.

Typically, an audio wave has a form as represented in the following figure, where the time-evolution of the perturbation amplitude is represented.

![Image](/assets/images/audio_wave.png#right)

#### I.1.1.2. Spectrogram

Since for audio signals, there is time-evolution of the frequencies, the well-known Fast Fourier transform (FFT) allows to visualize the spectrum of each time window, and the spectrogram is obtained when FFT is computed on overlapping windows of the signal.

A  visualisation is shown on the following figure where time is on x-axis, frequency on y-axis and relative intensity on the colorbar.

![Image](/assets/images/spectrogram.png#right)

Spectrogram is a way to process audio data in order to extract interesting features, but for this project I used Mel Frequency Cepstral Coefficients (MFCC) taking into account human perception for sensitivity at frequencies.

#### I.1.1.3. MFCC features

MFCC are widely used features for audio and speech recognition, and have been the state-of-the-art ever since as they represent the shape of the vocal tract. Following are steps to get insight of how they are computed:

- The audio signal is divided into short frames (20 - 40 ms).
- For each frame, the periodogram (Fast Fourier Transform) estimate of the power spectrum is calculated.
- In order to consider our human sensitivity of frequencies, the mel filterbank to the power spectra is applied and, the energy in each filter is summed.
- The logarithm of all filterbank energies is taken, as we don't hear loudness in a linear scale.
- Take the Discrete Cosine Transform (DCT) of the log filterbank energies in order to decorrelate computed energies since mel filters are all overlapping.

It is easy to compute MFCC using Librosa, and they are shown in the following figure where time is on the x-axis.

![Image](/assets/images/mfcc.png#right)

#### I.1.2. Results and discussions

#### I.1.2.1 First implementations and first conclusions

Firstly, I used audio files in [RAVDESS](https://zenodo.org/record/1188976#.YF5hwC1Q2Rs) dataset. For each file, I only took the first seconds in order to have feature vectors of same size, and I computed their MFCC features. MFCC features are represented in the form of a matrix where there are time windows in x-axis, and for each windows, we have MFCC features. At the end, an audio file is represented in the way of an image and therefore, it can be analyzed like an image.

Many classical machine learning algorithms need a feature vector as an input, so sometimes, the average of MFCC through time is computed and it is used to train these machine learning models. By this way, many informations are lost. It is possible to do better with deep learning. In order to use these new features to feed a neural network, I choose to re-implement a model found in the literature.

The model is a convolutional neural network whosee architecture is given in the following:

I clearly conclude that model overfit (even with dropout) as train score is around 0.99 while validation score is around 0.65. Increasing *dropout* leads to underfit (decrease of the train score to 0.8) keeping overfitting (train and validation scores remaining too separated), as it can be shown in the following figure.

![Image](/assets/images/val_curve1.png#right)

I was looking insights to increase the validation score: data augmentation on the same dataset, add new data sets, change the architecture of the neural network...

[comment]:<(#### I.1.2.2 Analyzing with new datasets)>

I started with another dataset: Toronto emotional speech set [(TESS)](https://www.kaggle.com/ejlok1/toronto-emotional-speech-set-tess). It is little different from the previous RAVDESS as the duration of audio is mainly smaller than 2 seconds. Training the same (previous) neural network (and with large dropout probability) with only this dataset led to great performances (larger than 0.98 for both train and validation sets, even for number of epochs smaller than 35).

In order to train model with several types of audio, for variety and diversity, I used the both datasets, even if it may be challenging to accurately use data from different sources.

- Using RAVDESS and TESS, with the same neural network architecture, I got a training score of 0.86 and a validation score of 0.8

#### I.1.2.2. Improving processing and models

## I.2. Audio features with Wav2Vec2

Wav2Vec2 is a vectorized representation of audio files that is feeded to machine learning algorithms. It is similar to word2vec used for word embeddings in natural language processing. After training to learn these features, this vector supposedly carries more representation information than other types of features, these are recent advancements in audio processing.

Currently, my understanding of Wav2Vec2 library for this emotion detection was limited, in addition I got good validation scores with MFCC features, so I only implemented emotion detection based on MFCC features.


# II. Working with video files (images frames)
