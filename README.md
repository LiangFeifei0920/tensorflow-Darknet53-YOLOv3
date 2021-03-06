# Object Detection
This is the implementation of YOLOv3 for object detection in Tensorflow. It contains complete code for preprocessing, training and test. Besides, this repository is easy-to-use and can be developed on Linux and Windows.  

[YOLOv3 : Redmon, Joseph, and Ali Farhadi. "Yolov3: An incremental improvement." arXiv preprint arXiv:1804.02767 (2018).](https://arxiv.org/abs/1804.02767)

## Getting Started
### 1 Prerequisites  
* Python 3.x  
* Tensorflow 1.x  
* Opencv-python  
* Pandas  

### 2 Define your class names  
Download  and unzip this repository.  
`cd ../YOLOv3/label`  
Open the `label.txt` and revise its class names as yours.  

### 3 Prepare images  
Copy your images and annotation files to directories `../YOLOv3/data/annotation/images` and `../YOLOv3/data/annotation/images/xml` respectively, where the annotations should be obtained by [a graphical image annotation tool](https://github.com/tzutalin/labelImg) and  saved as XML files in PASCAL VOC format.  
`cd ../YOLOv3/code`  
run  
`python spilt.py`  
Then train and val images will be generated in  `../YOLOv3/data/annotation/train` and  `/YOLOv3/data/annotation/test` directories, respectively.  

### 4 Anchor clusters using K-means  
Run K-means clustering on the training set bounding boxes to automatically find good anchors.  
`cd ../YOLOv3/code`  
run  
`python anchor_cluster.py`  
Anchors generated by K-means are saved in the directory `../YOLOv3/anchor/anchor.txt`. Belows are same outputs when running K-means:

`Iter = 1/20, Average IoU = 0.719983, is current optimal anchors.`  
`Iter = 2/20, Average IoU = 0.733096, is current optimal anchors.`  
`Iter = 3/20, Average IoU = 0.73589, is current optimal anchors.`  
`Iter = 4/20, Average IoU = 0.736503, is current optimal anchors.`  
`Iter = 5/20, Average IoU = 0.736472`  
`Iter = 6/20, Average IoU = 0.736157`  
`Iter = 7/20, Average IoU = 0.735872`  
`Iter = 8/20, Average IoU = 0.735478`  
`...................................`  
`...................................`  
`...................................`  
`Iter = 19/20, Average IoU = 0.732432`  
`Iter = 20/20, Average IoU = 0.73226`  

### 5 Train model using Tensorflow  
The model parameters, training parameters and eval parameters are all defined by `parameters.py`.  
`cd ../YOLOv3/code`  
run  
`python train.py`  
The model will be saved in directory `../YOLOv3/model/checkpoint`, and some detection results are saved in `../YOLOv3/pic`. 
 
### 6 Visualize model using Tensorboard  
`cd ../YOLOv3`  
run  
`tensorboard --logdir=model/`   
Open the URL in browser to visualize model. Below  is the graph of my model:  
<div align=center><img width="900" height="700" src="https://github.com/xiaogangLi/tensorflow-Darknet53-YOLOv3/blob/master/YOLOv3/pic/graph.png"/></div>

## Examples  
Here are some detection examples in my dataset:   

![Image](https://github.com/xiaogangLi/tensorflow-Darknet53-YOLOv3/blob/master/YOLOv3/pic/example0.jpg)
![Image](https://github.com/xiaogangLi/tensorflow-Darknet53-YOLOv3/blob/master/YOLOv3/pic/example1.jpg)
![Image](https://github.com/xiaogangLi/tensorflow-Darknet53-YOLOv3/blob/master/YOLOv3/pic/example2.jpg)
![Image](https://github.com/xiaogangLi/tensorflow-Darknet53-YOLOv3/blob/master/YOLOv3/pic/example3.jpg)
