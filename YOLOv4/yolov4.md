<h1>Use YOLOv4 to train you own data in Linux

Follow the instruction below, so you can easily understand how to use yolov4 to train you own data in linux.
<h2>Preparation

1. **Download YOLO4** 
 * In this part you can use the code below to download YOLO4 .
    git clone https://github.com/AlexeyAB/darknet.git 
 
 * You also can visit https://github.com/AlexeyAB/darknet to download the code.
 2. **Download pre-trained weights-file**
 * Use link below to down the pre-trained weights-file
 https://github.com/AlexeyAB/darknet/releases/download/darknet_yolo_v3_optimal/yolov4.conv.137

 3. **If you want use gpu to run the model please following the instruction below.(Need  cudnn and cuda)**
* Revise makefile (You can find in darknet file)
  
  ![enter image description here](https://imagizer.imageshack.com/img922/1439/QroxQG.png)
  ![enter image description here](https://imagizer.imageshack.com/img923/2103/L7zaNu.png)
* After you revise it , you need use code below.
cd darknet
make

![enter image description here](https://imagizer.imageshack.com/img922/6418/joHpS2.png)
4. **Create the file and data**
* Please follow the image below to create the file.
  
  ![enter image description here](https://img-blog.csdnimg.cn/20200430153948299.png)
  ![enter image description here](https://imagizer.imageshack.com/img922/2379/D6OtUg.png)
*  Annotations save label file. You can use labelImg to label your images.
   
   ![enter image description here](https://imagizer.imageshack.com/img922/5516/6ZS4Ik.png)
   
* Put all images in JPEGImages
* The txt in ImageSets use image's name line by line
  
  ![enter image description here](https://imagizer.imageshack.com/img922/5198/PRoHwu.png)
  ![enter image description here](https://imagizer.imageshack.com/img924/3333/JJknlt.png)
 
5.**Use voc_label.py to create label file. Please follow the instruction below.**
* First find voc_label.py
  
  ![enter image description here](https://imagizer.imageshack.com/img922/81/0ZQbrE.png)
* Revise the voc_label.py according to your data

   ![enter image description here](https://imagizer.imageshack.com/img923/2687/kSQcM3.png)
  Depend on your data choose the correct classes and class's name.
   
   ![enter image description here](https://imagizer.imageshack.com/img922/8861/DPp5Xu.png)
   
   ![enter image description here](https://imagizer.imageshack.com/img923/7893/3eqc3I.png)
 
* After you finish the all procedure. Please run voc_label.py, it will generate label file.
  
  ![enter image description here](https://imagizer.imageshack.com/img923/2007/Y3FmeP.png)

6.**Prepare obj.data, obj.names and yolov4-tiny-custom.cfg**
* Copy coco.data and rename it to obj.data
  
   ![enter image description here](https://imagizer.imageshack.com/img922/8615/oY3BeU.png)
   
   ![enter image description here](https://imagizer.imageshack.com/img924/7324/5ev8Lm.png)
   classes = depend on your data
   train = The path of  2007_train.txt 
   valid = The path of  2007_test.txt 
   names = The path of obj.names
   backup = The path you want to save your weights

* Copy coco.names and rename it to obj.names
    obj.names depend on your  classes name

  ![enter image description here](https://img-blog.csdnimg.cn/20200430162928516.png)
      
* Copy yolov4-tiny-custom.cfg and revise it
   
   ![enter image description here](https://imagizer.imageshack.com/img924/7669/8Wyquv.png)
      You need change classes depand on your classes
      ![enter image description here](https://imagizer.imageshack.com/img923/1414/XbHHDh.png)
      You also need change filters depend on your classes
      There is the formula [(class+5)*3] to calculate how many filters you need.
 <h2>Train your model
      
  * Now you can train your model by useing code below
  cd darknet
  ./darknet detector train ...../obj.data ....../yolov4-tiny-custom.cfg ......../yolov4.conv.137
  * You also can test the result of your model by using code below
  cd darknet
  ./darknet test ..../obj.data ...../yolov4-tiny-custom.cfg ...../yolov4.weights ....../test.jpg
<h3>This is how to use YOLOv4 to train your own data. Hoping everyone can success to train their own data. Thanks to your patient.
<h2> Reference
   
  [https://medium.com/@jennyTurtle/%E5%B0%8F%E7%99%BDtrain%E8%87%AA%E5%B7%B1%E7%9A%84yolo-v4-f23f48f85f9e](https://medium.com/@jennyTurtle/%E5%B0%8F%E7%99%BDtrain%E8%87%AA%E5%B7%B1%E7%9A%84yolo-v4-f23f48f85f9e)
      
