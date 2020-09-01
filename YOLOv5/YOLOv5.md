# YOLOv5

# Installation

```sh
$ conda create -n yolov5 python=3.8 -y
$ conda activate yolov5

$ git clone https://github.com/ultralytics/yolov5  
$ curl -L -o tmp.zip https://github.com/ultralytics/yolov5/releases/download/v1.0/coco128.zip && unzip -q tmp.zip && rm tmp.zip 
$ cd yolov5
$ pip install -qr requirements.txt
```

# How to put your data
   ```
   #image is to put image data, label is to put the corresponding txt file.(The detail of generating txt file can refers to "Yolov3 official")
   
   ${yolov5}
    `-- data
        `-- image
            |-- train
            |-- val
        `-- label
            |-- train
            |-- val
   ```
#  Train Custom Data
```sh
# Input data is your custom data
$ cd yolov5/data/
$ gedit coco128.yaml
```

# Step 1. Create Dataset.yaml
### You can directly use coco128.yaml file change to your data form
```sh
# train and val data as 1) directory: path/images/, 2) file: path/images.txt, or 3) list: [path1/images/, path2/images/]
train: ../data/images/train/
val: ../data/images/val/

# number of classes
nc: 2

# class names
names: ['person', 'bicycle']
```
# For how to label the image, please refers to yolov3 method

# Step 2. Select a Model
```sh
$ cd yolov5/models/
$ gedit yolo5s.yaml
```

## choose one model, here I use yolov5s.yaml as example
## In yolov5s.yaml, it only change nc: _  to your class number 
```sh
# parameters
nc: 2  # number of classes
depth_multiple: 0.33  # model depth multiple
width_multiple: 0.50  # layer channel multiple

# anchors
anchors:
  - [10,13, 16,30, 33,23]  # P3/8
  - [30,61, 62,45, 59,119]  # P4/16
  - [116,90, 156,198, 373,326]  # P5/32

# YOLOv5 backbone
backbone:
  # [from, number, module, args]
  [[-1, 1, Focus, [64, 3]],  # 0-P1/2
   [-1, 1, Conv, [128, 3, 2]],  # 1-P2/4
   [-1, 3, BottleneckCSP, [128]],
   [-1, 1, Conv, [256, 3, 2]],  # 3-P3/8
   [-1, 9, BottleneckCSP, [256]],
   [-1, 1, Conv, [512, 3, 2]],  # 5-P4/16
   [-1, 9, BottleneckCSP, [512]],
   [-1, 1, Conv, [1024, 3, 2]],  # 7-P5/32
   [-1, 1, SPP, [1024, [5, 9, 13]]],
   [-1, 3, BottleneckCSP, [1024, False]],  # 9
  ]

# YOLOv5 head
head:
  [[-1, 1, Conv, [512, 1, 1]],
   [-1, 1, nn.Upsample, [None, 2, 'nearest']],
   [[-1, 6], 1, Concat, [1]],  # cat backbone P4
   [-1, 3, BottleneckCSP, [512, False]],  # 13

   [-1, 1, Conv, [256, 1, 1]],
   [-1, 1, nn.Upsample, [None, 2, 'nearest']],
   [[-1, 4], 1, Concat, [1]],  # cat backbone P3
   [-1, 3, BottleneckCSP, [256, False]],  # 17 (P3/8-small)

   [-1, 1, Conv, [256, 3, 2]],
   [[-1, 14], 1, Concat, [1]],  # cat head P4
   [-1, 3, BottleneckCSP, [512, False]],  # 20  (P4/16-medium)

   [-1, 1, Conv, [512, 3, 2]],
   [[-1, 10], 1, Concat, [1]],  # cat head P5
   [-1, 3, BottleneckCSP, [1024, False]],  # 23  (P5/32-large)

   [[17, 20, 23], 1, Detect, [nc, anchors]],  # Detect(P3, P4, P5)
  ]
```
# Step 3. Train
### If you face "CUDA out of memory" problem when you do training, please change your batch size smaller
```sh
# Back to root directory 

# Train YOLOv5s on coco128 for 5 epochs
$ python train.py --img 640 --batch 16 --epochs 100 --data ./data/coco128.yaml --cfg ./models/yolov5s.yaml --weights ''
```

# Step 4.  Detection
```sh
# save 
$ python detect.py --weights runs/exp15/weights/best.pt --source data/(to your image location) --save-txt
```









