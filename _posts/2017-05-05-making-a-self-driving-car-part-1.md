---
title: "(WIP) Making a Self Driving Car - Part 1"
layout: page
date: '2017-05-05 02:05:14'
categories: self-driving machine-learning
---

I just graduated from the University of Pittsburgh and have some time to relax before starting my job, so my dad and I decided to build a self-driving car. While challenging, we believe we have the skills to do it, and to learn some cool stuff in the process. The goal is to start simple and build as we go.

# Step 1 - Car Data
Before doing anything in the world of machine learning, we need to:
1. Understand the problem.
2. Understand the required data.
3. Get the data.

Since we're starting very simply, we aimed to create a self-driving car that would simply look at the road and turn the steering wheel by itself. We would manually provide braking and acceleration as needed. But first, we need a lot of training data. There is a terrific paper by NVIDIA titled ["End to End Learning for Self-Driving Cars"](https://arxiv.org/pdf/1604.07316.pdf) that details a very simple self-driving car. It relies on camera input and the angle of the steering wheel as inputs to a CNN, which produces steering angle as an output. Let's work on getting the steering angle!  

## CAN Bus
Modern cars are computers with wheels. Made up of many microcontrollers and **ECUs** (engine control units) that all control various systems in the car, from the engine and the drivetrain to the infotainment systems and the air conditioning. These controllers read and write data to their connected systems in order to control the car.  

Having so many systems is a networking nightmare. Data has to be sent around the car since it is used in multiple places, which means miles of wiring underneath the car. This is not only inefficient, but also cost ineffective. To solve this issue, the **CAN Bus** was created.  

{:refdef: style="text-align: center;"}
![CAN diagram]({{ site.url }}/static/ml/sdp1-1.jpg)
{: refdef}
{:center: style="text-align: center"}
Image obtained from Volkswagen Audi.
{:center}

(Note: the following is not a comprehensive CAN guide, it's just enough to give you the gist of what's going on! I learned the majority of this from Wikipedia, car repair manuals, and [this](http://www.volkspage.net/technik/ssp/ssp/SSP_238.pdf) wonderful presentation by Volkswagen Audi.)

CAN, standing for **controller area network**, is a protocol in which all control units in the car send digital signals over a copper wire bus (in the future, this will be fiber optics) at a max rate of 1000 kbps. There are generally three separate CAN systems in a modern vehicle:
1. High-speed drive train CAN Bus generally operating at 500 kbps (500,000 baud).
2. Low-speed infotainment CAN Bus generally operating at 100 kbps (100,000 baud).