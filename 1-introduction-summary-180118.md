# Introduction

## 1.1 머신러닝의 종류

### Predictive, Supervised learning

- 라벨 값이 있는 데이터를 활용한 학습 방식
- input 값을 특정 output에 매핑시키는 것이 목적



- input $x_i$: feature, attribute, covariates
- output $y_i$ : response variable
  - 종류 : 
    - categorical(finite set) : 푸는 방법 classfication, pattern recognition
    -  nominal(real-valued) : 푸는 방법 regression 
    - ordinal regression(라벨이 있는 서수)



### Descriptive, Unsupervised learning

- 관심있는 패턴을 찾아내는 것 (knowledge discovery)이 목적
- error metric 이 존재하지 않는다.



## Reinforcement learning

주어진 환경에서 행동에 대한 보상과 벌을 통해 학습하는 방법



## 1.2 Supervised learning

### 1.2.1 Classification

#### Classification의 종류

- binary classification (라벨이 두개인 경우)
- multiclass classification (라벨이 여러개인 경우)
- multi-label classification (하나에 라벨이 여러개 붙는 경우)
- multiple output model (하나에 여러개의 이진 라벨이 붙는 경우)



#### function approximation

라벨이 있는 training set을 가지고 function $\hat{f}$를 추정하는 방법

$\hat{y} = \hat{f}(x) $

- generalization : 새로운 데이터를 예측해 의미있는 것을 만드는 능력



#### The need for probabilistic predictions

$p(y|x, D, M)$

$x : input , D : train set, M : model$

- 실제 푸는 방법

$\hat{y}=\hat{f}(\mathbf{x})=\overset{C}{\underset{c=1}{argmax}} \ p(y=c|\mathbf{x},D)$

- mode : 가장 확률이 높은 라벨
- MAP estimate (maximum a posteriori) : 가장 확률이 높은 라벨을 추정하는 방법 



#### 실제 응용

- Document classification and email spam filtering
  - 문서를 걸러내거나 스팸 이메일을 찾아내는 기법
  - bag of word : 문서안 단어를 feature-vector화하는 방법
- Classifying flowers
  - feature extraction : 특징을 추출하는 작업
  - exploratory data analysis : 머신러닝을 적용하기 전에 데이터를 그림으로 표시에 미리 분석하는 방법
- Image classification and handwriting recognition
  - MNIST (modify national institute of standards) : train set : 60000, test set : 10000, 28x28 handwriting data
- Face detection and recognition
  - object detection, object localization
  - sliding window detector : 그림을 부분 부분 잘라내어 물체를 classification하는 방법
  - Face recongnition : 얼굴이 누구인지 판별하는 시스템

### 1.2.2 Regression

input과 output이 모두 실수의 값으로 이루어진 모델.



## 1.3 Unsupervised learning

- Knowledge discovery : 흥미로운 구조를 발견하는 것
- density estimation : $p(\mathbf{x}_i|\boldsymbol{\theta})$ 에서 $\boldsymbol{\theta}$ 를 추정하는 한다.
- input x는 multivatiate probability model이다.
- 인간과 동물의 학습방법과 유사한 기법으로 supervised learning보다 더 넓게 적용해 사용할 수 있다. 



#### 실제 응용

- Discovering clusters : 군집화의 갯수를 알려준다. 

  - 찾는 방법
    - 첫번째 군집 K를 찾는다.
      - $p(K|D)$가 최대가 되는 mode $K^* = \underset{K}{argmax} \ p(K|D) $ 를 찾는다.
    - 두번째 군집 K에 속하는 포인트를 찾는다.
      - hidden, latent variable : 알수없는 k의 값
  - model based clustering : 데이터를 확률 기반으로 클러스터링하는 방법
    - 장점 : 객관적인 방법으로 표현이 가능하다.

- Discovering latent factors

  - dimenstionality reduction : 차원을 줄이는 작업
  - 이 작업을 통해 빠른 Nearest Neighbor Search가 가능, Visualizing에도 좋아진다.
  - 대표적인 예 : PCA(principle component analysis) 

- Discovering graph structure

  - $\hat{G} \ = \ argmax \ p(G|D)$ 를 계산해 graph 구조를 알아내는 방법

- Matrix completion

  - 빈 부분을 채우는 기법
  - Image inpainting : 이미지의 빈부분을 채운다.
  - Collaborative filtering : 적은 데이터로 빈부분의 행렬을 채우는 방법

- Market basket analysis

  ​

  ​