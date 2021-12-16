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

#### (1) LeNet
### 
|LeNet-5 구조|
| --- |
|![LeNet-5 구조](https://media.vlpt.us/images/5050/post/b184f9ee-5898-417b-96cc-41d8c2316c9f/image.png)|
<img src="https://miro.medium.com/max/743/0*N12IeN008JYr-7YC" width="40px" height="5px"></img>

###### LeNet은 손글씨를 인식하는 네트워크로서, 최초 모델인 LeNet-1이 1990년에 제안, 최종적으로 LeNet-5가 1998년에 제안됩니다. 구조를 간단히 살펴보면, 인풋, 3개의 컨볼루션 레이어, 2개의 서브샘플링 레이어, 한 층의 fully-connected 레이어, 아웃풋 레이어로 구성되어 있고, 활성함수로는 tanh함수를 사용합니다. 모델마다 다르긴 하지만, 수십, 수백개의 레이어를 가지고, 주로 RELU 활성함수를 사용하는 최근의 모델들(RESNET 등)과 비교했을때 확실히 간소해 보이긴 합니다. 

####  (2) Alexnet
###### 이렇게 1990년대~ 2000년대를 거쳐 CNN은 지속적으로 발전해 오다, 2012년에 열린 이미지 인식 경진대회에서 AlexNet이 우수한 정확도로(오차 15%) 우승하면서 CNN모델들이 큰 인기를 얻게 됩니다. AlexNet에서 Alex는 네트워크 제안자중 한명인 *Alex Krizhevsky*의 이름을 딴 것인데요, 이분이 쓴  **"ImageNet Classification with Deep Convolutional Neural Networks"** 이라는 논문이 바로 오늘 알아볼 논문입니다.

#### (3) Imagenet
###
|Imagenet 데이터셋|
| --- |
|![Imagenet](https://cs.stanford.edu/people/karpathy/cnnembed/cnn_embed_1k.jpg)|
<img src="https://cs.stanford.edu/people/karpathy/cnnembed/cnn_embed_1k.jpg" width="8" height="5">

###### CNN모델이 발전하고 있는데, 언제까지 조그마한 손글씨 데이터만 분류하고 있진 않겠죠. 네, MNIST와 유사하게 데이터셋과 상응하는 정답 라벨이 오픈되어 제공되지만, 이제 손글씨 뿐만이 아닌 보다 복잡하고 *자연적인*  이미지 데이터셋을 쌓아놓은 것이 바로 ImageNet 입니다. "가구", "사람"등의 라벨이 붙어진 수많은 데이터가 여기에 해당됩니다. 

######  사실, LeNet과 Alexnet 모두 주어진 imagedataset을 어떻게 더 정확하게 분류해 낼 수 있을까에서 발전했다고 볼 수 있을것 같습니다. 이러한 관점에서 보았을 때, 역시 어떤 모델을 쓰는가 보다는 *어떤 데이터를 분류할 것인가에 더욱 더 방점을 두어야 하는것 같습니다. 
 그러면, 이제 본격적으로 논문을 요약, 정리해보겠습니다.
##
### 3. About Alexnet
###
###### 먼저, 이 논문은 
###### Abstract 
###### 1. Introduction 
###### 2. Dataset 
###### 3. Architecture 
###### 4. Reducing overfitting
###### 5. Details of learning
###### 6. Results
###### 7. Discussion
###### 순으로 구성되어 있습니다. 오늘은 "architecture"를 중점적으로 다뤄보겠습니다.
### 
#### (1)  Background
###### architecture로 들어가기 전, Alexnet에 대한 개괄적인 설명부터 시작하겠습니다.
###
###### Alexnet은 Imagenet 내 120만여개의 고해상도 이미지를 1000개의 라벨로 분류하기 위해 학습된 모델입니다. 학습 결과, test data 상위 5개의 에러가 17~37.5%내에 있는 등 기존 모델보다 훨씬 뛰어난 성능을 보여주게 됩니다. Alexnet은 5개의 convolution layers와 그에 대응하는 max-pooling layers, 3개의 fully-connected layers와 1000개 라벨 다중분류를 위한 softmax 활성함수로 구성되어있습니다. 또한, 이미지 연산에 GPU 사용, dropout regularization 사용등 최근 개발된 대부분의 CNN의 기본이 되는 기법들이 이 모델에 사용됩니다. Alex Krizhevsky(이하 Alex로 편하게 부르겠습니다.)와 그의 동료들은 이 모델을 약간 변형해, 2012년 이미지 인식 경진대회에서 상위 5개 에러 확률 15.3%를 달성해 우승하게됩니다.
###
###### 그 당시 까지만 해도, MNIST 이미지 수준의 간단한 데이터를 수만개 규모로 사용해 학습할 경우, 적절히 augmented된 데이터라면 최고 오류율 0.3% 이내로 인간의 분류 수준에 근접해 있었습니다. 하지만, Imagenet정도 수준의  사실적이고 자연적인 이미지를 적절한 오류율 내에서 분류하기 위해선 훨씬 더 큰 규모(1500만개 규모)의 데이터셋이 필요했고 사실 이것도 충분하진 않았습니다.
###
###### CNN은 이미지의 특성을 잘 반영해 학습한다는 장점에도 불구하고, Imagenet 정도의 규모와 수준의 데이터를 학습하고 처리하기에는 자원이 너무나 많이 소모된다는 단점이 있습니다. 이 문제를 해결하기 위해, Alex는 학습에 GPU를 사용했습니다. 또한, 이미지를 학습하고 처리할 수 있을 만한 네트워크의 폭과 깊이 내에 모델의 성능을 향상, 학습시간 감소를 위해 여러 새롭고 특이한 특징들(a number of new and unusual features), Overfitting 방지를 위해 여러 효과적인 기술(several effective techniques)을 도입합니다. 거칠게 말하면, 앞서 말한 layer 개수와 GPU성능 사이에서 정확도와 시간을 최적화하는데, 여러 기법들을 도입해 그 최적점을 기존보다 훨씬 높은 위치에서 찾았다고 할 수 있습니다. 
###
###### 이번 포스트에서는 **여러 새롭고 특이한 특징들(a number of new and unusual features)** 이 무엇이었는지 좀 더 자세히 알아보도록 하겠습니다. 데이터셋은 Imagenet의 데이터를 사용했는데, 앞서 여러번 언급했으니 자세한 설명은 피하고, 다만 Alexnet은 256*256 해상도의 데이터만 input으로 받아들일 수 있기 때문에 다양한 해상도의 imagenet 내 데이터를  down-sampling을 진행해 학습에 이용했다는 것만 알아두시면 될 것 같습니다.
###
### (2) Architecture
###### 다음은 Alexnet의 구조에서  중요한 특징들을 중요도 순으로 설명한 것을 요약한 것입니다.
###
### (2-1) Relu Nonlinearity
###### LesNet에서도 봤듯이, 그동안 convolution layers에서 주로 쓰던 활성함수는 tanh(x) 함수 였습니다. 하지만 이 함수는 경사 하강의 관점에서 보면 Relu 함수에 비해 기울기가 너무 완만해 학습 시간에 악영향을 주었습니다. (Relu 함수는 *f(x)= max(0,x)* 함수로, 입력값이 0이하면 0을, 0 이상에선 입력값 그대로 출력하는 함수 입니다.) 
###
###### 실례로, 동일한 모델에서 학습 오류를 줄이는데 필요한 시간이 Relu 함수를 쓸때가 tanh(x)함수를 사용할 때 보다 6배 가량 차이가 났다고 합니다.
###
|Relu와 tanh(x) 학습시간 비교|
| --- |
|![Relu nonlinearity](https://seongkyun.github.io/assets/post_img/study/2019-05-01-activations/relu_alexplot.jpg)|

### (2-3) Local Response Normalization
###### Relu 함수는 출력 범위가 0이상이고, 입력 받는 범위는 모든 실수영역이므로 입력값에 대해 정규화가 따로 필요하지 않다는 장점이 있습니다.( 만약 반대라면, 입력값에 음수가 들어가지 않도록 결과값에 대해 적절한 정규화가 필요했을지도 모릅니다.) 하지만, 만약 입력 데이터의 일부 영역의 특징이 너무 강하다면(한 예로, 한 부분의 픽셀 화솟값이 주변 지역에 비해 급격히 크다면), 그 지역에 대한 fillter 가중치가 너무 높게 책정되어 주변 지역을 제대로 인식하는 것이 어려울 수 있습니다. 
###### 이를 막기위해, Alexnet에서는 Relu 결과값에 local response normalization을 이용합니다. 우리말로 그대로 옮기면 '국소 반응 정규화'입니다. 말 그대로, 모델이 국소 반응에 과도하게 반응하는 것을 막기위해, 동일 지역에 대해 서로 다른 layer 필터를 적용한 값들을 이용해 Relu 결과값을 정규화 하는 것 입니다. 이렇게 하면, 국소 지역의 특징으로 인해 하나의 필터에 과도한 가중치가 매겨졌다 하더라도, 동일 지역의 다른 layer 필터 값들도 큰 값을 가지게 되므로 국소 지역 특징을 과도평가 하는 것을 막는 효과가 있는것입니다. 
|LRN(local response normalization|
| --- |
|![LRN](https://t1.daumcdn.net/cfile/tistory/9925CB3E5A9A560604)|

## 참고사이트
https://towardsdatascience.com/a-short-history-of-convolutional-neural-networks-7032e241c483

https://bskyvision.com/418

https://proceedings.neurips.cc/paper/2012/file/c399862d3b9d6b76c8436e924a68c45b-Paper.pdf

