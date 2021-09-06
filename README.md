
<img src="https://user-images.githubusercontent.com/77844152/132121864-7c089282-a781-49b7-a51c-256f6b8a1542.jpeg" width="900" height="200">

# 모션 키포인트 검출 AI 경진대회🏃‍♀️
(2021.03.10~2021.04.14)<br/>
Dacon 모션 키포인트 검출 AI경진대회는 사람이 어떤 운동을 수행할 때, 각각의 동작마다 신체 부위에서 keypoint를 검출하는 대회이다.


## 데이터구성

```bash
1.open
├── data
│   ├── test_imgs.zip
│   ├── train_imgs.zip
│   ├── test_imgs
│   └── train_imgs
├── train_df.csv
└── sample_submission
``` 
대회측에서 제공하는 데이터는 train 이미지 4195장,test 이미지 1600장, train이미지의 이름과 keypoint 24 지점의 x,y 좌표가 적혀있는 .csv파일,정답지로 구성되어있다.

## About the model


* ### EDA
 주어진 이미지와 keypoint지점을 사진위에 표현하며 제공된 데이터가 정확한 좌표를 포함하는 지 확인

* ### Preprocessing
train dataset에서 keypoint matching이 제대로 되지 않은 데이터 총 101개를 제거

* ### Augmentation
albumentation library를 이용. HorizontalFlip, RandomRotate90, VerticalFlip , MotionBlur, GaussNoise, Normalize

* ### Resnet
ResNet은 깊은 layer 구조를 가지면서도 layer의 input을 layer의 output에 바로 연결시키는 'skip connection' 기법을 통해 vanishing gradient 현상을 방지한 모델이다.
참가자 공유코드를 베이스라인으로 삼아 resnet18,resnet34,wide resnet 등 모델의 깊이를 변경해보았고 batch size,lr,epoch을 조정하며 train했다.


* ### Result
-parameters
	
| model| learning rate       | batch size        |  epoch |
|:---: | :---: | :---: |  :---: | 
| Wide ResNet50             | 	0.01     | 128 | 50|  

-scores	
|       train RMSE           |     dev RMSE                   | test RMSE         |  
|:---: | :---: | :---: | 
|    30.5407       | 	83.84183      | 78.944  |  


* ### 다양한 시도
	- densenet
	- detectron2
	- mask r-cnn

## Reference

*   [haerulmuttaqin/FoodsApp-starting-code](https://github.com/haerulmuttaqin/FoodsApp-starting-code)<br/>

## Project Report

Click [Here](https://drive.google.com/file/d/1Lpa7W7CeAKZmVW951RScrL2dIgGH7Ls3/view?usp=sharing)


## Contributors

* [박근아](https://github.com/guen-a-park)
* [서민지](https://github.com/Minjee-Seo)
* [이서인](https://github.com/seoin-lee)

