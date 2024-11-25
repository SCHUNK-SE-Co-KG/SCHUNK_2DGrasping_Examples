# KUKA KRC

## Quickstart
- Make sure EthernetKRL is installed on robot
- Connect SVC to XF5 Port of  robot controller and make sure IP adresses are in same subnet
- Copy 2DGK_plugin.src and 2DGK_plugin.dat to KRC/R1/Program
- Copy SCHUNK_2DGrasping.xml to Config/User/Common/EthernetKRL
- Add in .dat specified variables to $config.dat
- Edit program to fit your needs and use global functions where you need them

## Prerequisites 

This application was tested on a KR10 Robot using a KR C5 micro – 8.7.5 controller. The (paid) option package EthernetKRL is needed. We used V3.2.4 and cannot ensure to be compatible with other versions. Keep in mind that EthernetKRL is a paid option so if it is not present on your robot, contact your KUKA supplier. 

## Hardware Connection 

To connect the SCHUNK IPC and the KUKA controller plug an ethernet cable into the robot port of the SCHUNK IPC and port XF5 of the KUKA controller. This port uses the static IP address set in your robot settings. The usage of other ports is not recommended. To access this IP address, go to your startup setting and view your network config. Open the web frontend of the SCHUNK Device and make sure your robot port is in the same subnetwork as the robot. 

To accommodate for KUKAs default IP address you should use the IP address 172.31.1.76 for the SCHUNK device. If you use a different one you also need to change the IP address in SCHUNK_2DGrasping.xml. The SCHUNK_2DGrasping.xml has to be stored in Config/Common/EthernetKRL 

Keep in mind that the IP Addresses of the robot and SVC should under any circumstances NOT be identical. 

## Programming 

We do not deliver code that is moving your robot out of the box, because we cannot foresee every different robot setup out there, especially as there are many different KUKA controllers that do not work the same, depending also on their software version. 

So, the provided code should only be used as foundation for your task and get you faster to the point of a working TCP/IP connection and to utilize all commands available. All global functions can be used in the code of your robot program. A simple example without specific robot and gripper commands is included in the SCHUNK_GRASPINGKIT.src 

We recommend to still take a look at the protocol documentation given. 

To use the global variables returned from the SCHUNK device make sure to add them to your $config.dat as described in the SCHUNK_GRASPINGKIT.dat file. 

We highly recommend observing the replyCodeSCHUNK variable in your program to detect any errors and act accordingly. 
