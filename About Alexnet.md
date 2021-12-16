# [Alexnet이란 무엇인가?](https://mmistakes.github.io/minimal-mistakes/)
### 
###### Yeon Wook Park, M.E, zexkiss77@hanyang.ac.kr
##
### 1. Instruction
###### - AlexNet은 2012년 개최된 ILSVRC 대회의 우승을 차지한 컨볼루션 신경망(CNN) 구조입니다.  
###### - 한학기 동안 배운 CNN구조를 더욱 제대로 이해하고, 정리하고자 Alexnet을 주제로 포스팅을 했습니다. 
###### - Alexnet의 히스토리, 구조와 특징들을 알아보도록 하겠습니다.   
##
### 2. History of CNN
###### 현대적 의미의 CNN(convolutional neural network)은 1990년대 MNIST라는 손글씨 숫자 데이터와 함께 시작합니다. 
###### 이 데이터셋은 0~9까지의 라벨링된 손글씨 데이터로, CNN은 MNIST의 데이터로 학습 후, 주어진 이미지에 나타난 숫자가 무엇인지 예측하게 되는겁니다. 이 28*28 크기의 작은 데이터셋을 분류하면서 나온 CNN 모델이 바로 LeNet입니다.
###
|MNIST 데이터셋|
| --- |
|![MNIST](https://miro.medium.com/max/743/0*N12IeN008JYr-7YC)|
<img src="https://miro.medium.com/max/743/0*N12IeN008JYr-7YC" width="8" height="5">
###
### (1) LeNet
###
|LeNet-5 구조|
| --- |
|![LeNet-5](https://media.vlpt.us/images/5050/post/b184f9ee-5898-417b-96cc-41d8c2316c9f/image.png)|
###### LeNet은 손글씨를 인식하는 네트워크로서, 최초 모델인 LeNet-1이 1990년에 제안, 최종적으로 LeNet-5가 1998년에 제안됩니다. 구조를 간단히 살펴보면, 인풋, 3개의 컨볼루션 레이어, 2개의 서브샘플링 레이어, 한 층의 fully-connected 레이어, 아웃풋 레이어로 구성되어 있고, 활성함수로는 tanh함수를 사용합니다. 모델마다 다르긴 하지만, 수십, 수백개의 레이어를 가지고, 주로 RELU 활성함수를 사용하는 최근의 모델들(RESNET 등)과 비교했을때 확실히 간소해 보이긴 합니다. 
###
###  (2) Alexnet
###### 이렇게 1990년대~ 2000년대를 거쳐 CNN은 지속적으로 발전해 오다, 2012년에 열린 이미지 인식 경진대회에서 AlexNet이 우수한 정확도로(오차 15%) 우승하면서 CNN모델들이 큰 인기를 얻게 됩니다. AlexNet에서 Alex는 네트워크 제안자중 한명인 *Alex Krizhevsky*의 이름을 딴 것인데요, 이분이 쓴  **"ImageNet Classification with Deep Convolutional Neural Networks"** 이라는 논문이 바로 오늘 읽어볼 논문입니다.
###
### (3) Imagenet
###
|Imagenet 데이터셋|
| --- |
|![Imagenet](https://miro.medium.com/max/770/0*mkpvMkCbiSi8d_K4)|
###### CNN모델이 발전하고 있는데, 언제까지 조그마한 손글씨 데이터만 분류하고 있진 않겠죠. 네, MNIST와 유사하게 데이터셋과 상응하는 정답 라벨이 오픈되어 제공되지만, 이제 손글씨 뿐만이 아닌 보다 복잡하고 *자연적인*  이미지 데이터셋을 쌓아놓은 것이 바로 ImageNet 입니다. "가구", "사람"등의 라벨이 붙어진 수많은 데이터가 여기에 해당됩니다. 
######  사실, LeNet과 Alexnet 모두 주어진 imagedataset을 어떻게 더 정확하게 분류해 낼 수 있을까에서 발전했다고 볼 수 있을것 같습니다. 이러한 관점에서 보았을 때, 역시 어떤 모델을 쓰는가 보다는 *어떤 데이터를 분류할 것인가에 더욱 더 방점을 두어야 하는것 같습니다. 그러면, 이제 본격적으로 논문을 읽어보겠습니다.
### 3. About Alexnet
###


##
## 참고사이트
https://towardsdatascience.com/a-short-history-of-convolutional-neural-networks-7032e241c483   
https://bskyvision.com/418
