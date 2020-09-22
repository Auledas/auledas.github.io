# ROS installation

In earlier posts we installed Ubuntu and some interesting applications to work with robotics. Now it is time to install the Robot Operating System, a middleware that provides many utilities to develop robotic systems. The table of contents is:

1. TOC
{:toc}

## Pick the distribution

As commented in previous posts, you need to check what distribution of ROS you can install on [ROS Installation Options](http://wiki.ros.org/ROS/Installation).

![](/images/rosdistributions.png "There are several ROS distributions available")

Once you have checked that the ROS distribution you want to install is compatible with your Ubuntu operating system it is time to roll!

## Installation

There are specific tutorials to install each distribution, and the process is quite simple! For example, these are the guidelines for [ROS Kinetic Kame](http://wiki.ros.org/kinetic/Installation/Ubuntu). The only part that can be confusing is how to enable "restricted," "universe," and "multiverse" repositories. To do this, just go to System Settings, Software & Updates, and tick the boxes shown in the figure below.

![](/images/repositories.png "Configure your Ubuntu repositories")

Once you have done this, just open your terminal pressing Ctrl+Alt+T and follow the instructions on the ROS installation page!
