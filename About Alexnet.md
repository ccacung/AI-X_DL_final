# [Alexnet이란 무엇인가?](https://mmistakes.github.io/minimal-mistakes/)
### 
Yeon Wook Park, M.E, zexkiss77@hanyang.ac.kr
##
### 1. Instruction
###### - AlexNet은 2012년 개최된 ILSVRC 대회의 우승을 차지한 컨볼루션 신경망(CNN) 구조입니다.  
###### - 한학기 동안 배운 CNN구조를 더욱 제대로 이해하고, 정리하고자 Alexnet을 주제로 포스팅을 했습니다. 
###### - Alexnet의 구조와 특징들을 알아보도록 하겠습니다.   
##
### 2. History of CNN
###### 현대적의미의 CNN(convolutional neural network)은 1990년대 MNIST라는 손글씨 숫자 데이터와 시작합니다. 이 데이터셋은 0~9까지의 라벨링된 손글씨 데이터로, CNN은 MNIST의 데이터로 학습 후, 주어진 이미지에 나타난 숫자가 무엇인지 예측하게 되는겁니다. 이 28*28 크기의 작은 데이터를 분류하면서 나온 CNN 모델이 바로 Lenet입니다.
#
####  LeNet 
|MNIST 데이터셋|
| --- |
|![MNIST](https://miro.medium.com/max/743/0*N12IeN008JYr-7YC)|
<img src="https://miro.medium.com/max/743/0*N12IeN008JYr-7YC" width="8" height="5">

