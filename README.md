# Biped humanoid robot combined with computer vision technology - for real-time object detection based on YOLO

<div align=center><img width="450" height="450" src="https://github.com/christw16/Biped-Humanoid-Robot-Battle/blob/master/img/logo1.jpg"/></div>

This YZUEI Robot is our graduate capstone. The group members are Li-Yuan Liu (1063706) and Ching-Hsien Hsu (1063740).



Generally, a defined biped humanoid robot has a torso, a head, two arms, as well as two legs. The robot requires a combination of hardware and software knowledge, integrating the expertise of the electrical, mechanical, and software knowledge. It is the best learning element for interdisciplinary learning. In this capstone, we use deep learning approach to combine with the robot. We use state of the art object detection method - YOLO to detect our custom trained object.


# Content

  * [Robot](#Robot)
  * [JetsonNano](#JetsonNano)
  * [Tools](#Tools)
  * [Train_data](#Train_data)
  * [Algorithm](#Algorithm)
  * [Gratitude](#Gratitude)

# Robot

The robot we use in our capstone is Siegfried robot.
Here is the link of [Siegfried robot](http://robosmart.com.tw/zh-tw/product_con.php?id=NTA=)
<div align=center><img width="450" height="470" src="https://github.com/christw16/YZU-Robot/blob/master/images/S__29704212.jpg"/></div>

# JetsonNano
Please check out [Install](Jetson_nano/Installation_of_Jetson_Nano.md) to see how to install Jetson Nano.

Please check out [Install](Jetson_nano/Equipment.md) to see the equipment.

Please check out [VNC](Jetson_nano/vnc.md) to see how we control Jetson Nano without using screen and keyboards.

# Tools
In the process of training our custom data, there are three main tools that we often use.

(1) Video-to-image

If we want to train data with a lot of data, we have to take thousands of images.
Therefore, we come up with the idea that we can take videos, and convert the video into images.

Please check out [Video-to-image](Tools/videotoimage.md)

(2) Batch Rename the file name

After converting the video to the images, the file name might be random weird name. Also, we have a great number of file to be handle.
Therefore, we have to use a better and easier way to change the file name. When we label the data, if the file name has weird character, it will get error.


Please check out [Batch Rename the file name](Tools/BatchRenaming.md)

(3) YOLO Label
It is very important to label the images with the format of text file or xml file. Since the process of "Object detection training" needs the information of the bounding box. Using YOLOLabel can easily get the bounding box information.

Please check out [YOLO Label](Tools/yololabel.md)

# Train_data
The following method is our traing data concept, all the process is using YOLOv3-tiny

We took images from far to middle to near as the training datas. Because in the process of the robot's movement, the object we want to detect will become bigger when the robot close to the object. 

Also, we set the far images, middle images and near images as  traing data in one class. The reason why we set different range views of the same class is because they are belongs to the same object, no matter the range of the images.

Moreover, if we set the training data as three different classes, the detection cannot easily be classified. Since the edge between far and middle, middle and near is difficult to define.

For the detailed information of YOLOv3, please visit its official website.

# Algorithm
  
  <div align=center><img width="450" height="450" src="https://github.com/christw16/YZU-Robot/blob/master/images/algorithm.jpg"/></div>
  
  
 # Gratitude

We appreciate Prof. Po-Chiang Lin as our capstone instructor.

We also appreciate those who helped us along the way
