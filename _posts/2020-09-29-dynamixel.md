# Controlling a Dynamixel actuator with ROS

Now that we have ROS installed in our system, we can start to develop our robotic systems! In many applications you will want to control a motor, in this post I will show how to do it. Before we start, you need to know the basics about how to use the Linux terminal and ROS. Take a look at the table of contents and let's dive in:

1. TOC
{:toc}

## Dynamixel actuators

Dynamixel is a brand of actuators developed by Robotis, the company that created the Turtlebot. These actuators are compatible with ROS, check this [link](https://robots.ros.org/dynamixel/) for more information. In this post I will control one of their motors, a [Dynamixel XL430-W250-T](https://emanual.robotis.com/docs/en/dxl/x/xl430-w250/). The component list I have used is:

* XL430-W250-T Dynamixel actuator [(link)](https://emanual.robotis.com/docs/en/dxl/x/xl430-w250/)
* U2D2 USB communication converter [(link)](https://emanual.robotis.com/docs/en/parts/interface/u2d2/)
* U2D2 Power Hub [(link)](https://emanual.robotis.com/docs/en/parts/interface/u2d2_power_hub/) or an 
SMPS2Dynamixel
* USB to USB micro cable
* External power supply or battery for the U2D2 Power Hub or SMPS2Dynamixel

## Download and make the packages

Once we have all the necessary components, we can continue to install the ROS packages. The process to install these packages can be found on [(link)](https://emanual.robotis.com/docs/en/software/dynamixel/dynamixel_workbench/). Basically, you need to navigate to your src folder on your catkin workspace and clone the following repositories:

    git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench.git
    git clone https://github.com/ROBOTIS-GIT/dynamixel-workbench-msgs.git
    git clone https://github.com/ROBOTIS-GIT/DynamixelSDK.git

Once you have cloned these packages you should build them using:

    catkin_make

Now you are ready to use the nodes, messages, and launch files developed by Robotis to control and receive information from the actuators!

## Connect the hardware

Then, we can connect the hardware. The XL430-W250-T has two connection sockets. The first one is linked to the U2D2 USB communication converter, using a 3pin TTL cable. The second one is connected to the U2D2 Power Hub or SMPS2Dynamixel, using another 3pin TTL cable. The U2D2 USB communication converter is then connected to the PC using a USB to USB micro cable and the SMPS2Dynamixel is connected to the power supply. An image of how the connections should look like is attached below:

![](/images/dynamixel1.jpg "Dynamixel connections")

To use the U2D2 you may also need to create a rules file, a format that stores udev rules to operate and identify devices on linux systems. To create this file just copy and paste the following lines on your terminal:

    wget https://raw.githubusercontent.com/ROBOTIS-GIT/dynamixel-workbench/master/99-dynamixel-workbench-cdc.rules
    sudo cp ./99-dynamixel-workbench-cdc.rules /etc/udev/rules.d/
    sudo udevadm control --reload-rules
    sudo udevadm trigger

## Find dynamixels

Once this is done, you are ready to work with your Dynamixel actuator. First you may want to check that you can successfully find your actuator. To do so, open two terminal windows and run the following commands:

    roscore
    rosrun dynamixel_workbench_controllers find_dynamixel /dev/ttyUSB0

The first command will start the necessary nodes and programs that allow ROS nodes to communicate. The second one scans all ID with each Baudrate (9600, 57600, 115200, 1000000, 2000000, 3000000, 4000000) and shows if there are any Dynamixels connected. If you have connected everything correctly, you should find an actuator, like shown in the image below:

![](/images/findynamixel.png "After scanning all IDs you should find the connected dynamixel motors")


## Modify basic.yaml

Once the actuator has been found and the baudrate is known, we can use one of the launch files in the dynamixel-workbench package to control it. The launch file that we are going to use is dynamixel_controllers.launch on the launch folder. However, before using it, we need to modify the basic.yaml file in the config folder. If you are using a single actuator you should modify the file to remove the second actuator, for example commenting the lines like so:

    # You can find control table of Dynamixel on emanual (http://emanual.robotis.com/#control-table)
    # Control table item has to be set Camel_Case and not included whitespace
    # You are supposed to set at least Dynamixel ID
    pan:
      ID: 1
      Return_Delay_Time: 0
    #tilt:
    #  ID: 2
    #  Return_Delay_Time: 0

## Use the motors

Finally, we can control the actuator. Open a new terminal and type:

    roslaunch dynamixel_workbench_controllers dynamixel_controllers.launch

The colour of your U2D2 USB communication converter should change to red and blue. Now you can call control your actuator. Using rosservice, you can change the position of the actuator from 0 to 4095. For example, to move the actuator to a 90 degree position type the following lines to a new terminal:

    rosservice call /dynamixel_workbench/dynamixel_command "command: ''
    id: 1
    addr_name: 'Goal_Position'
    value: 1024"

Or:

    rosservice call /dynamixel_workbench/dynamixel_command '' 1 'Goal_Position' 1024

If you want to see the actuator working, take a look at this [Youtube video](https://youtu.be/l8pu72J_fR8). Now you can use this actuators to develop your own systems!
