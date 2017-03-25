---
layout: post
title:  "Machine Learning for Diabetic Retinopathy"
date:   2017-03-24 23:05:00 -0400
categories: machine-learning
---

This is a page for my talk given at [FCHacks 2017](http://fchacks.io) at Fox Chapel High School on March 25th, 2017. I will add more detail here after the hackathon!

## Data
Get the data from [here]({{ site.url }}/assets/data/dr.csv) (right click, save as).

## Prerequisites
* Python 3.5.X

## Setup
1. Open your terminal/command prompt.
1. Verify Python 3.5.X is installed by running `python -V` (or `python3 -V` for systems where Python is alt-installed).
1. Create a folder to run the project in (this is where you should save the data from above).
1. Install `virtualenv` using `pip install virtualenv`.
1. Install and activate your virtual environment.
    1. Install: `virtualenv venv`
    1. Activate:
        * Linux/Mac: `. venv/bin/activate`
        * Windows: `venv\Scripts\active`
        * (you'll now have a running virtual environment. Execute `deactivate` at any time to leave the venv.)
1. Install the following packages via `pip` (By running `pip install package-name`):
    * ipython[all]
    * numpy
    * pandas
    * scikit-learn
1. Launch your iPython Notebook using `jupyter notebook --no-browser` (on Python 2.7.X, this is `ipython notebook --no-browser`).
1. Go to the URL printed on the terminal (example: `http://localhost:8888/?token=99829e106fd00819d113c7a232a0fa343f8f265c04ea94b2`).

## Notebook
If you're on mobile, view the notebook [here]({{ site.url }}/assets/fchacks-dr-nb-2017.pdf).
<object data="{{ site.url }}/assets/fchacks-dr-nb-2017.pdf" type="application/pdf" width="100%" height="800px">
  <p>It appears you don't have a PDF plugin for this browser.</p>
</object>

## Slides
These aren't too helpful as the majority of this talk was interactive, but it gives an intro to ML.
If you're on mobile, view the slides [here]({{ site.url }}/assets/fchacks-dr-2017.pdf).
<object data="{{ site.url }}/assets/fchacks-dr-2017.pdf" type="application/pdf" width="100%" height="800px">
  <p>It appears you don't have a PDF plugin for this browser.</p>
</object>
