---
layout: post
title: Mapping Out Baskin
---

I am working on an Indoor Autonomous Robotic Car which can navigate a floorplan of a building.
This car given a destination will be able to traverse its environment and reach the destination without any user input.

There are many aspects of this project, such as mapping, as well as Navigation and Localization.
The domain for this project is called Simultaneous Localization and Mapping (SLAM).

So far I have been using Robot Operating System and the packages that it provides to create a map of a part of the engineering building here at UC Santa Cruz.

Using only the RPLidar 360 Laser scanner that we bought (I am the lead developer for the team), we were able to create part of the map by using HECTOR Mapping.

HECTOR Mapping is a SLAM algorithm for ROS which uses only the Laser Scanner to create accurate 2d-occupancy grid maps of the environment. It uses scan matching.

I was afraid that the hallways in Basin engineering building would not have enough features for the scan matcher to work. But I wanted to test it out anyway.

It turns out that the Baskin hallways have a lot of features (divets, nooks, crannies) in the hallway for the laser matchin algorithm to successfully create a map.

Here is a video demonstration of Mapping and HECTOR Results:

<iframe width="560" height="315" src="https://www.youtube.com/embed/x9NRgX7njaU" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6-KWuDb-EYw" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

The car shown here is a first prototype (ackerman steering) that we had on hand, to mount the laser scanner. A different robotic car will be used oficially in the project (differential drive).

There is significant noise at the beginning since we were holding the car to bring it to the hallway. We were recording data throughout the entire process, so any laser scanner readings which penetrated windows or an outside environment showed up as large rays in the map.

This was our methodology to build the map:

Methodology: Decouple data from Algorithm  

  * First Step: Capture LIDAR data while driving around. No SLAM Algorithm running  (Rosbag)
  * Second Step: Bring up the algorithms and see if nodes set up correctly.  
  * Third Step: Play back data and watch algorithm output.  
  
The end result is a 2-d occupancy grid PGM file.

<p align="center">
  <img src="https://image.ibb.co/ko56JS/oc_grid_map.png" width="600"/>
</p>

As we can see, there is some error as the laser scanner can penetrate glass doors and windows (seen when we pick it up). We also see the required nooks and crannies (defining features) in the hallway for successful mapping. Ive also found that it helps if the robotic car is driven in a zig-zag fashion across a straight hallway (give more definition for laser matching).

In the future, I would like to obtain a bigger map, as this was only tested on two hallways of Baskin Engineering building. The next steps are to setup the Navigation stack and tailor it to our robotic car.
  
