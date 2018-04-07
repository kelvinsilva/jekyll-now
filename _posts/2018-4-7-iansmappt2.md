---
layout: post
title: Indoor Autonomous System Mapping and Localization
---

From my previous post "Mapping Out Baskin", I am working on my senior thesis project involving robotic navigation. The hardware has finally arrived and we have a fully driveable robot with a 360 Laser Scanner and Encoders (ticks from motors to give odometry). 

For the past two weeks I have been working on using a ROS Differential Drive package to convert Encoder ticks into Odometry (PoseWithCovariance message). We have a Low Level microcontroller which handles the control and communication potentially dangerous electronic devices such as our Brushed Uxcell DC Motors and H-Bridge PWM signals. The Low Level microcontroller (Teensy) connects to the Raspberry Pi via USB. The Raspberry Pi is the main computing unit which runs the algorithms necessary for Localization, Navigation, and Web Client (User Interface) communications. Using the Pi's GPIO to directly connect to something like a DC Motor is extremely irresponsible engineering practice, which is why we have this high-level - low-level decouplement. 

After wrangling with odometry calibration, today I have finally achieved an important Mile-stone, which is to create a Map of Baskin Engineering 3rd floor with a rospackage called GMapping. GMapping is a SLAM Algorithm which uses a Rao-Blackwellized Particle filter (Improved Particle Filter). This rospackage requires calibrated odometry data as well as laser scan (where HECTOR only needs laser). My previous post on mapping relied on a scan matching-only algorithm (HECTOR SLAM) that works extremely well in feature rich environments. The successful usage of GMapping gives confirmation that our Odometry data is accurate since it relies on odometry data (Extremly important for navigation). With GMapping our robot can optimally create maps of any environment, especially environments that have small amount of features and long hallways (narrow hallway with no doors). HECTOR Slam would not work in long, featureless corridors and has no loop closing ability (returning to same spot improves the map).

The map we created with GMapping is below:

<p align="center">
  <img src="https://preview.ibb.co/eGgMNH/image.png" width="600"/>
</p>


