# Real-Time Noise Reduction App
Real-Time Implementation and
Evaluation of Wide Dynamic Range
Compression and Noise Reduction

This repository contains the project shell and algorithms needed for the implementation of
an Android smartphone app that implements functions used in hearing aids
consisting of wide dynamic range compression (WDRC) and noise reduction (NR).


## Algorithm Explanation

The Android application was designed and implemented using the flowchart
shown below. The application was designed to process audio in real-time
with a sampling frequency of 48000 Hz and where each input frame has 256
samples. As seen in the flowchart. Each input audio frame is processed by the voice activity detection (VAD) 
and sound pressure level (SPL) functions, which measure the probability of speech presence and
SPL for each frame. After retrieving VAD and SPL values, the algorithm uses
the values to update the WDRC flag and NR flag, which are used to selected
the most suitable filter for that specific frame. The filter used in this app
comes from a FIR filter bank consisting of 6 FIR filters that was specifically
designed for gain adjustments in different frequency bands. The filter value
obtained for each frame is the stored in an array that will be capturing filter
values until the decision rate is met. The decision is defined to be performed
every few frames with 50% overlap (e.g. is the decision rate is 200 frames
we set a step size of 100 frames for decisions). Once the decision rate
is met, a majority voting mechanism is used to decide what filter to apply
on the following frames based on the filters computed for previous frames
processed. The filter chosen is then used to filter the upcoming frames until
decision rate is met again. This process it performed many times until the
audio is fully processed.


<p align="center">
  <img src="./images/algo_flowchart.jpg" />
</p>

## Project Documentation & Experimental Evaluation

Click [here](https://github.com/ilucasgoncalves/real-timeNoiseReductionApp/blob/main/Project_Documentation.pdf) to access the project's documentation file.

In the documentation file you will have acess to the following:

1. Introduction
1. First list item
   - 2.1 Implementing the App
   - 2.2 Experimental Evaluation
     - 2.2.1 Real-world Captured Audios Evaluation
     - 2.2.2 Decision Rates Evaluation
     - 2.2.3 Thresholds Evaluation
     - 2.2.4 Application Decision Algorithm Evaluation
   - 2.3 Discussion
3. Android App GUI - User’s Guide
   - 3.1 Main Screen
   - 3.2 Settings
   - 3.3 Output Files
4. Code-Organization - User’s Guide
   - 4.1 Project Organization
   - 4.2 Functions Used
   - 4.3 MatlabNative.c

