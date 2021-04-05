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

Before the introduction of *transformers*, *MFCC coefficients* have been the state of the art in audio natural language processing. Research continues to be conducted for a better exploitation of audio to improve the applications of artificial intelligence in everyday life. Considering this point, I found it appropriate to use these two approaches to extract interesting features to feed to machine learning algorithms for prediction.

## I. Working with MFCC features using Librosa

Many Python librairies deal with signal and audio processing, here I only talk about Librosa. For a better understanding, I would start by reminding some concepts upstream of the MFCC coefficients.

### I.1. Audio representations

#### I.1.1. Audio wave

Sound is a mechanical wave that is transmitted from a source in an elastic medium. The perturbation is a local change of the atmospheric pressure causing the vibrations of the air molecules. Human beings and many animals feel this wave through the sense of hearing.

Typically, an audio wave has a form as represented in the following figure, where the time-evolution of the perturbation amplitude is represented.

![Image](/assets/images/audio_wave.png#right)

#### I.1.2. Spectrogram

Since for audio signals, there is time-evolution of the frequencies, the well-known Fast Fourier transform (FFT) allows to visualize the spectrum of each time window, and the spectrogram is obtained when FFT is computed on overlapping windows of the signal.

A  visualisation is shown on the following figure where time is on x-axis, frequency on y-axis and relative intensity on the colorbar.

![Image](/assets/images/spectrogram.png#right)

Spectrogram is aa way to process audio data in order to extract interesting features, but for this project I used Mel Frequency Cepstral Coefficients (MFCC) taking into account human perception for sensitivity at frequencies.

#### I.1.3. MFCC features

MFCC are widely used features for audio and speech recognition, and have been the state-of-the-art ever since as they represent the shape of the vocal tract. Following are steps to get insight of how they are computed:

- The audio signal is divided into short frames (20 - 40 ms).
- For each frame, the periodogram (Fast Fourier Transform) estimate of the power spectrum is calculated.
- In order to consider our human sensitivity of frequencies, the mel filterbank to the power spectra is applied and, the energy in each filter is summed.
- The logarithm of all filterbank energies is taken, as we don't hear loudness in a linear scale.
- Take the Discrete Cosine Transform (DCT) of the log filterbank energies in order to decorrelate computed energies since mel filters are all overlapping.

It is easy to compute MFCC using Librosa, and they are shown in the following figure.

![Image](/assets/images/mfcc.png#right)


## II. Audio features with Wav2Vec2

Wav2Vec2 is a vectorized representation of audio files that is feeded to machine learning algorithms. It is similar to word2vec used for word embeddings in natural language processing. After training to learn these features, this vector supposedly carries more representation information than other types of features, these are recent advancements in audio processing.
