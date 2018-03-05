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

Here is a video demonstration:

<object width="425" height="350">
  <param name="movie" value="https://www.youtube.com/watch?v=x9NRgX7njaU" />
  <param name="wmode" value="transparent" />
  <embed src="https://www.youtube.com/watch?v=x9NRgX7njaU"
         type="application/x-shockwave-flash"
         wmode="transparent" width="425" height="350" />
</object>
