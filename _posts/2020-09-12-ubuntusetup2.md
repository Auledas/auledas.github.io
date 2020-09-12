# Ubuntu installation II

In the previous post, we learnt how to install a Ubuntu distribution. However, to work with ROS, there are several utilities and drivers that should be installed. Here's the table of contents:

1. TOC
{:toc}

## NVidia drivers

Firstly, if the computer has an NVidia graphics card, we should install the drivers for it. To do so, open the terminal pressing Ctrl+Alt+T or by searching 'terminal' on the application menu. Then, on the terminal, run the following command:

    sudo add-apt-repository ppa:graphics-drivers/ppa

You will be asked to write your password, type it and press Enter. Note that there will be no visual feedback while you type due to security reasons. Then, type the following line of code:

    sudo apt update

Finally, open the System Settings utility, click on Software & Updates, go to Additional Drivers, then choose *Using NVIDIA binary driver - version 418.56 from nvidia-418*, and finally press Apply Changes.

![](/images/nvidia-drivers.png "The drivers for your NVidia graphics card can be found on the additional drivers tab")

## Terminator

Terminator is an application that improves your terminal. You can split one window into multiple terminals, create tabs, customize the cosmetics of your terminal, change the keybindings, etc.

Usually, working with ROS, you will need to open many terminals. Using Terminator can help arrange all these terminals. If you want to install it, just type on your terminal:

    sudo apt-get install terminator

Then, if you want to change anything just right click on the terminal, click on preferences and start modifying as you prefer!

![](/images/terminator.png "Terminator is a useful application to work with multiple terminals and customize them")

## Kazam

The next interesting application to have on your Ubuntu machine is Kazam. Kazam is a program that lets you capture images or video from your screen. If you want to easily record how to do something Kazam is very helpful! To install it, type the following command on your terminal:

    sudo apt-get install kazam 

The GUI is easy to use, as you can see below, so it is quite straight forward to use.

![](/images/kazam.png "Kazam is a screen capture/recorder application")
