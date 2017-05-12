# YOLO-Powered_Robot_Vision

***

* [Written by Korean version]()

## Introduction

This is a Pi-based robot to implement visual recognition([by YOLO](https://pjreddie.com/media/files/papers/yolo_1.pdf)). The YOLO-Powered vision can recognize many objects such as people, car, bus, fruits, and so on. 

* Hardware: Raspberry-Pi2, Sony PS3 Eye Camera
 
   (Available to use Logitech C270 USB camera with Raspberry Pi)

* Software: YOLO(v2), Jupyter-Notebook

![Structure.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/Structure_YOLO.png)


## My motivation
I was so interested in performance of the image recognition with YOLO-2 on Raspberry Pi. In addition, the Jupyter notebook is really convenient to instantly code as a quick prototype. The Raspberry pi's processing speed is very slow compare to my laptop.

([The Architecture: paper](https://pjreddie.com/media/files/papers/yolo_1.pdf))

![Architecture_CNN.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/Architecture_CNN.png)


## Requirements and Installation

* Jupyter-Notebook: [How To Install Jupyter-Notebook on Raspberry Pi](https://www.instructables.com/id/Jupyter-Notebook-on-Raspberry-Pi/)


## Quick Start

This post will guide you through detecting objects with the YOLO system using a pre-trained model. If you don't already have Darknet installed, you should install OpenCV2 before on your Raspberry Pi. 

* Install dependencies for OpenCV2
```
sudo apt-get update

sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev python-dev python-numpy libjpeg-dev libpng-dev libtiff-dev libjasper-dev

sudo apt-get install python-opencv
```

* Check which version of OpenCV you have in Python
```
python
import cv2
cv2.__version__
```


* Install the darknet for YOLO
```
git clone https://github.com/pjreddie/darknet
cd darknet
make
```
Easy!

You already have the config file for YOLO in the cfg/ subdirectory. You will have to download the pre-trained weight file here (258 MB). Or just run this:
```
wget http://pjreddie.com/media/files/yolo.weights
```

Then run the detector to test.
```
./darknet detect cfg/yolo.cfg yolo.weights data/dog.jpg
```

You will see some output like this:
```
layer     filters    size              input                output
    0 conv     32  3 x 3 / 1   416 x 416 x   3   ->   416 x 416 x  32
    1 max          2 x 2 / 2   416 x 416 x  32   ->   208 x 208 x  32
    .......
   29 conv    425  1 x 1 / 1    13 x  13 x1024   ->    13 x  13 x 425
   30 detection
Loading weights from yolo.weights...Done!
data/dog.jpg: Predicted in 0.016287 seconds.
car: 54%
bicycle: 51%
dog: 56%
```
![Output](https://pjreddie.com/media/image/Screen_Shot_2016-11-17_at_11.14.54_AM.png)


* Re-name from 'darknet' to 'YOLO-Powered_Robot_Vision'.

```
mv /home/pi/Documents/darknet /home/pi/Documents/YOLO-Powered_Robot_Vision
cd /home/pi/Documents/YOLO-Powered_Robot_Vision
```

* Download 'YOLO-Powered_Robot_Vision.ipynb' at /home/pi/Documents/YOLO-Powered_Robot_Vision
```
wget https://github.com/leehaesung/YOLO-Powered_Robot_Vision/raw/master/YOLO-Powered_Robot_Vision.ipynb

jupyter-notebook
```



## Source Codes

* [YOLO-Powered_Robot_Vision.ipynb](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/YOLO-Powered_Robot_Vision.ipynb)


## Result of Object Recognition
(Caution!!: I have used the image sources for an educational purpose. Please don't use any picture in copyright.)

![predictions06.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions06.png)

* Another examples
![predictions07.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions07.png)

![predictions08.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions08.png)

![predictions09.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions09.png)

![predictions11.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions11.png)



