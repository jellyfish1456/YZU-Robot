# Biped humanoid robot combined with computer vision technology - for real-time object detection based on YOLO

<div align=center><img width="450" height="450" src="https://github.com/christw16/Biped-Humanoid-Robot-Battle/blob/master/img/logo1.jpg"/></div>

This YZUEI Robot is our graduate capstone. The group members are Li-Yuan Liu and Ching-Hsien Hsu.



Generally, a defined biped humanoid robot has a torso, a head, two arms, as well as two legs. The robot requires a combination of hardware and software knowledge, integrating the expertise of the electrical, mechanical, and software knowledge. It is the best learning element for interdisciplinary learning. In this capstone, we use deep learning approach to combine with the robot. We use state of the art object detection method - YOLO to detect our custom trained object......to be continue



We can design the robot with our need. This robot is bought from Robosmart Technology. It provides us an opportunity to build our own robot!

# Content

  * [Robot](#Robot)
  * [Installation](#Installation)
  * [Praogram_syntax](#Praogram_syntax)
  * [Robot_Action_Programming](#Robot_Action_Programming)
  * [Preliminary_prepare](#Preliminary_prepare)
  * [Check_and_start](#Check_and_start)
  * [Code](#Code)
  * [Reference](#Reference)
  * [Members](#Members)
  * [Honor](#Honor)
  * [Gratitude](#Gratitude)

# Robot

The robot we use in our capstone is Siegfried robot.
Here is the link of [Siegfried robot](http://robosmart.com.tw/zh-tw/product_con.php?id=NTA=)

# Train_data
The following method is our traing data concept

first step (10/08):
1. we took images from far to middle to near as the training datas. Because in the process of the robot's movement, the object we want to detect will become bigger when the robot close to the object. 

Also, we set the far images, middle images and near images as  traing data in one class. The reason why we set different range views of the same class is because they are belongs to the same object, no matter the range of the images.

Moreover, if we set the training data as three classes, the detection cannot easily be classified. Since the edge between far and middle, middle and near is difficult to define.

...
far range images

middle range images

near range images

Experiment result

55 cm
The accuracy is 


42 cm
The accuracy is

26 cm
The accuracy is

12 cm
The accuracy is

### Feature 

to be continue

# Installation

For the installation process, we use ....................

### Jetson Nano
Please check out [Jetson_nano/vnc.md](Jetson_nano/vnc.md)
  
 # Gratitude

We appreciate Prof. Po-Chiang Lin as our capstone instructor.

We also appreciate those who helped us along the way
