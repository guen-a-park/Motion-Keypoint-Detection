
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


* ___EDA___ :주어진 이미지와 keypoint지점을 사진위에 표현하며 제공된 데이터가 정확한 좌표를 포함하는 지 확인


<img src="https://user-images.githubusercontent.com/77844152/132149470-0a64cd9b-af0e-477b-aa9b-3e7c065ebcf3.png" width="500" height="300">

 
* ___Preprocessing___ :  keypoint matching이 제대로 되지 않은 데이터 총 101개를 제거

* ___Augmentation___ : albumentation library를 이용. HorizontalFlip, RandomRotate90, VerticalFlip , MotionBlur, GaussNoise, Normalize

* ___Resnet___ : 참가자 공유코드를 베이스라인으로 삼아 resnet18,resnet34,wide resnet 등 모델의 깊이를 변경하고 batch size,lr,epoch을 조정하며 train

* ___Result___ <br/>

	
|parameters| model| learning rate       | batch size        |  epoch |
|:---:|:---: | :---: | :---: |  :---: | 
| -| Wide ResNet50             | 	0.01     | 128 | 50|  

	
|scores|       train RMSE           |     dev RMSE                   | test RMSE         |  
|:---:|:---: | :---: | :---: | 
|-|    30.5407       | 	83.84183      | 78.944  |  


* ___다양한 시도___
	- densenet
	- detectron2
	- mask r-cnn

## Reference

*   [dacon-data](https://dacon.io/competitions/official/235701/data)<br/>
*   [dacon-codeshare](https://dacon.io/competitions/official/235701/codeshare)
*   [albumentations-team/albumentations](https://github.com/albumentations-team/albumentations)
*   [liuzhuang13/DenseNet](https://github.com/liuzhuang13/DenseNet)
*   [facebookresearch/detectron2](https://github.com/facebookresearch/detectron2)

## Project Report

Click [Here](https://drive.google.com/file/d/1Lpa7W7CeAKZmVW951RScrL2dIgGH7Ls3/view?usp=sharing)


## Contributors

* [박근아](https://github.com/guen-a-park)
* [서민지](https://github.com/Minjee-Seo)
* [이서인](https://github.com/seoin-lee)

