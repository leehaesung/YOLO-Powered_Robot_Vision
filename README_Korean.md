# 라즈베리파이기반 YOLO 사물인식 로봇

***

* [English version](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/README.md)

## 소개

 이 로봇은 라즈베리파이 기반 YOLO 사물인식 로봇은 사람, 자동차, 버스, 과일 등과 같은 많은 물건을 인식 할 수 있습니다.


* 하드웨어 : Raspberry-Pi2, Sony PS3 Eye Camera
 
   (소니 PS3 Eye 카메라대신에 로직텍 C270 USB 카메라와 라즈베리파이와 함께 사용할 수 있습니다.)

* 소프트웨어 : YOLO (v2), 주피터노트북

![Structure.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/Structure_YOLO.png)


## 나의 동기
저는 라즈베리파이의 YOLO 이미지 인식 성능에 관심이 많았습니다. 또한 주피터노트북은 빠른 프로토타입으로 즉석으로 코드를 작성하는 것이 편리합니다. 라즈베리파이의 처리 속도는 내 랩톱에 비해 매우 느립니다.

([시스템 구조: 논문에서 발췌](https://pjreddie.com/media/files/papers/yolo_1.pdf))

![Architecture_CNN.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/Architecture_CNN.png)


## 요구 사항 및 설치

* 주피터 노트북: [라즈베리파이에 주피터 노트북 설치하기](https://www.instructables.com/id/Jupyter-Notebook-on-Raspberry-Pi/)


## 시작하기

이 포스트는 사전 훈련 된 모델을 사용하여 YOLO 시스템으로 물체를 감지하는 방법을 안내합니다. 아직 다크 넷을 설치하지 않았다면, 전에 OpenCV2를 라즈베리 파이에 설치해야합니다.

* 라즈베리파이에 OpenCV2를 위해 기초 드라이버 설치
```
sudo apt-get update

sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev python-dev python-numpy libjpeg-dev libpng-dev libtiff-dev libjasper-dev

sudo apt-get install python-opencv
```

* Python에서 가지고있는 OpenCV의 버전을 확인하십시오.
```
python
import cv2
cv2.__version__
```


* YOLO용 다크 넷 설치하기
```
git clone https://github.com/pjreddie/darknet
cd darknet
make
```
설치가 매우 쉽네요!

이미 cfg / 하위 디렉토리에 YOLO에 대한 설정 파일이 있습니다. 사전 훈련 된 가중치파일 (258 MB)을 다운로드해야합니다. 또는 다음을 실행하십시오.
```
wget http://pjreddie.com/media/files/yolo.weights
```

그런 다음 테스트 할 디텍터를 실행하십시오.
```
./darknet detect cfg/yolo.cfg yolo.weights data/dog.jpg
```

다음과 같은 출력이 표시됩니다.
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


* 'darknet'에서 'YOLO-Powered_Robot_Vision'으로 이름을 변경하십시오.

```
mv /home/pi/Documents/darknet /home/pi/Documents/YOLO-Powered_Robot_Vision
cd /home/pi/Documents/YOLO-Powered_Robot_Vision
```

* 'YOLO-Powered_Robot_Vision.ipynb' 다운로드하세요.
```
wget https://github.com/leehaesung/YOLO-Powered_Robot_Vision/raw/master/YOLO-Powered_Robot_Vision.ipynb

jupyter-notebook
```



## 소스코드

* [YOLO-Powered_Robot_Vision.ipynb](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/YOLO-Powered_Robot_Vision.ipynb)


## 객체인식 결과
(주의!: 저는 교육용으로 이미지 소스를 사용했으므로 저작권이있는 사진을 사용하지 마십시오. 저는 사용하는 이미지에 대해 책임을지지 않습니다.)

![predictions06.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions06.png)

* Another examples
![predictions07.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions07.png)

![predictions08.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions08.png)

![predictions09.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions09.png)

![predictions11.png](https://github.com/leehaesung/YOLO-Powered_Robot_Vision/blob/master/ImageFiles/predictions11.png)


* 감사합니다.
