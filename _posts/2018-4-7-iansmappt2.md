---
layout: post
title: Indoor Autonomous System Mapping with Odometry
---

From my previous post "Mapping Out Baskin", I am working on my senior thesis project involving robotic navigation (IANS Project). The hardware has finally arrived and we have a fully driveable robot with a 360 Laser Scanner and Encoders (ticks from motors to give odometry). 

For the past two weeks I have been working on using a ROS Differential Drive package to convert Encoder ticks into Odometry (PoseWithCovariance message). We have a Low Level microcontroller which handles the control and communication potentially dangerous electronic devices such as our Brushed Uxcell DC Motors and H-Bridge PWM signals. 

The Low Level microcontroller (Teensy) connects to the Raspberry Pi via USB. The Raspberry Pi is the main computing unit which runs the algorithms necessary for Localization, Navigation, and Web Client (User Interface) communications. Using the Pi's GPIO to directly connect to something like a DC Motor is extremely irresponsible engineering practice, which is why we have this high-level - low-level decouplement. 

After wrangling with odometry calibration, today I have finally achieved an important Mile-stone, which is to create a Map of Baskin Engineering 3rd floor with a rospackage called GMapping. GMapping is a SLAM Algorithm which uses a Rao-Blackwellized Particle filter (Improved Particle Filter). This rospackage requires calibrated odometry data as well as laser scan (where HECTOR only needs laser). My previous post on mapping relied on a scan matching-only algorithm (HECTOR SLAM) that works extremely well in feature rich environments. 

The successful usage of GMapping gives confirmation that our Odometry data is accurate since it relies on odometry data (Extremly important for navigation). With GMapping our robot can optimally create maps of any environment, especially environments that have small amount of features and long hallways (narrow hallway with no doors). HECTOR Slam would not work in long, featureless corridors and has no loop closing ability (returning to same spot improves the map).

The map we created with GMapping is below (Jack Baskin 3rd floor):

<p align="center">
  <img src="https://preview.ibb.co/eGgMNH/image.png" width="600"/>
</p>
* Image is annotated

Notice that in this map we have a long and featureless hallway, which is captured perfectly with GMapping since it also relies on odometry data to create its map. One thing to notice is the small error in angle along the top right long horizontal hallway (with 3 divets) due to imperfection of odometric data.  Probabilistic methods are amazing, but they aren't perfect. 

Small errors in the map are not worrisome however since the probabilistic nature of the AMCL (adaptive monte carlo localization) package  we will be able to localize adequately in this map.

This was a monumental day as it confirms the accuracy (relatively speaking) of odometry which sets the stage for localization and navigation portions of IANS.

Until next time

-Kelvin
