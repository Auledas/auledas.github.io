# ROS setup

In this post I will explain how to set up a computer to work with the Robot Operating System (ROS). Here's the table of contents:

1. TOC
{:toc}

## ROS distributions

The first step required to work with ROS is to decide which [distribution](http://wiki.ros.org/Distributions) we are going to use. At the time of writting, September 2020, there are two recommended ROS distributions: 

- ROS 2 Foxy Fitzroy
- ROS 1 Noetic Ninjemys

However, it is also common to work with older versions of ROS. Some packages can only be used on specific distributions, and this can be a decisive factor to use an older version. For this reason, ROS 1 Kinetic Kame is still quite popular, even though it was released on May 2016.

## Create a bootable Ubuntu USB stick

Once a ROS distribution has been chosen, we need to check which operating systems are supported. [ROS Noetic Ninjemys](http://wiki.ros.org/noetic), for example, should be used with Ubuntu 20.04 (Focal). On the other hand, [ROS Kinetic Kame](http://wiki.ros.org/kinetic) is primarily targeted at the Ubuntu 16.04 (Xenial) release.

If we want to install ROS Kinetic Kame, for example, we should download the 16.04 Xenial Xerius distribution on [Ubuntu releases](https://releases.ubuntu.com/). Then, we can follow the tutorials to create a bootable usb stick. There are both tutorials to do so from [Ubuntu](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview) or [Windows](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview).

## Install Ubuntu

Then, when the bootable USB stick has been prepared, we can proceed to install Ubuntu. To do so, we must restart the computer and enter the BIOS (usually pressing F2 or DEL while opening). Then, boot the system from the USB stick.

If you boot from the USB stick correctly the following screen will be presented to you. To continue click on install.

![](/images/1ubuntu.JPG "Try or install selection")

The next screen will offer the possibility of installing updates and third-party software, do not tick the boxes, just click continue.

![](/images/2ubuntu.JPG "Updates and third-party software selection")

The next screen allows you to choose if you want to erase the whole computer's disk and install Ubuntu or do something else. The option 'something else' is used in dual boot computers, that have both Windows and Ubuntu, for example. As an example, we will take a look at this option.

![](/images/3ubuntu.JPG "Installation type")

In this space, assuming we want to completely delete de disk and install only Ubuntu, we must press DEL to all the partitions. Then, only free space will remain. In this free space we will create 3 partitions: root, swap and home.

![](/images/4ubuntu.JPG "Partition table")

To start new partitions press on the + sign. The first partition will be dedicated to the root. About 20 GB is enough for it. Then, select Ext 4 as file type and write / as the mount point (which means root). Finally, click ok.

![](/images/5ubuntu.JPG "Create first partition")

You will go back to the partition screen. The second partition we need to create is the swap area. Again, click on the + sign. The swap size should be double of RAM. In this case, you should use the swap area file type. Once completed, click ok.

![](/images/6ubuntu.JPG "Create second partition")

Finally, we will create the home partition. Allocate all the remaining free space in this partition and click ok.

![](/images/7ubuntu.JPG "Create third partition")

If you have followed the steps correctly, the partition table should look like the following image.

![](/images/8ubuntu.JPG "Finished partition table")

Make sure that the mount point, type and size of each partition is correct. If everything is fine, you can install Ubuntu. After the installation you will be asked to provide a username, password, timezone etc. When you finish this setup, restart the computer. You see a purple screen and Ubuntu will pop up. Enjoy the freshly installed Ubuntu! In the following posts I will explain how to install ROS and several interesting packages.
