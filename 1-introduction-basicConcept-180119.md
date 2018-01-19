# Introduction

## 1.4 Some basic concepts in ML

### 1.4.1 Parametric vs non-parametric model

- Parametric model : parameter의 갯수가 정해져 있는 모델
  - 빠르지만 data distribution에 강한 가정이 있어야 한다.
- Non-parametric model : data의 갯수에 따라 파라미터의 갯수가 변화하는 모델
  - 유연하지만 큰 데이터를 이용할 시 처리가 복잡해 진다.

### 1.4.2 Non-parametric classifier : K-nearest neighbors 

#### K-Nearest Neighbors 

입력값 x와 가까운 데이터 셋 K개를 이용해 category를 결정하는 방법

`수식`

>  $p(y=c|\mathbf{x}, D, K)= {1 \over K} \sum_{i\in K_k(\mathbf{x},D)} \mathbb{I}(y_i=c)  $

>  indicator function : $\mathbb{I}(e)$

>  $\mathbb{I}(e)=\begin{cases} 1 & \mbox{if e is  true} \\ 0 & \mbox{if e is false} \end{cases}$



- Supervised 이며 non-parametric model
- memory-based learning, instance-based learning
- K=1 일 때는 제일 가까은 점의 label로 선택되기 때문에 다각형안에 하나의 특징점을 포함하고 있는 Voronoi tessellation의 모습을 띈다.



### 1.4.3 curse of dimensionality

차원이 커질수록 데이터의 밀도는 배로 줄어들어 문제를 해결하기 위해 필요한 데이터 량이 급속하게 증가하는 문제.

#### 예 

다차원 단위 큐브의 일정 부분을 차지하는 더 작은 큐브의 길이를 구할 때, 

> $e_D(f)=f^{1/D}$

이란 수식이 사용 된다. 

D=10이고 f가 0.1이라고 할 때

> $e_{10}(0.1)=0.8$ 

이는 ??? 잘모르겠다. (이해 필요)



### 1.4.4 Parametric models : classification, regression

차원의 저주를 풀기 위해서는 data가 특정 data distribution을 따른 다고 가정한다. ($p(y|\mathbf{x})$ : supervised, $p(\mathbf{x})$ : unsupervised)

- 위와 같은 가정을 inductive bias혹은 parametric model이라 부른다. 

#### Linear regression

> $y(\mathbf{x})=\mathbf{w}^T\mathbf{x}+\epsilon = \sum_{j=1}^{D}w_jx_j+\epsilon$
>
> $\mathbf{w}$ : weight vector 
>
> $\epsilon$ : residual error

- residual error $\epsilon$

$\epsilon$은 주로 Gaussian 혹은 normal distribution을 띈다. 

$w_0$: bias, intercept

- linear regression + residual error 

> $p(y|\mathbf{x}, \mathbf{\theta})=N(y|\mu(\mathbf{x}), \sigma^2(\mathbf{x}))$
>
> $\mu(\mathbf{x})=w_0+w_1x=\mathbf{w}^T\mathbf{x}$
>
> $\sigma^2(\mathbf{x})=\sigma^2$

- linear regression을 non-linear regression으로 확장 (basis function expansion)

> $p(y|\mathbf{x}, \mathbf{\theta})=N(y|\mathbf{w}_T\Phi(\mathbf{x})), \sigma^2)$

 - polynomial regression : $\Phi(x)$가 다항의 조합으로 되어 있는 경우

> $\Phi(x)=[1,x,x^2,\dots, x^d]$



#### Logistic regression

linear regression을 binary classification으로 변환하는 방법

- 변환 방법

  1. Guassian 대신에 Bernoulli 분포를 사용한다.

     > $p(y|\mathbf{x},\mathbf{w})=Ber(y|\mu(\mathbf{x}))$
     >
     > $\mu(\mathbf{x})=Ber(y|\mu(\mathbf{x}))$
     >
     > $\mu(\mathbf{x})=\mathbb{E}[y|\mathbf{x}=p(y=1|\mathbf{x})]$

     ​	

  2. linear combination을 특정 함수에 넣어준다.

     > $\mu(\mathbf{x})=sigm(\mathbf{w}^T\mathbf{x})$

     $sigm(\eta)$ : sigmoid function, logistic function, logit function, squashing function

     > $sigm(\eta)={1 \over 1+exp(-\eta)}={e^\eta \over e^\eta+1}$

- Bernoulli + sigmoid function

> $p(y|\mathbf{x},\mathbf{w})=Ber(y|sigm(\mathbf{w}^T\mathbf{x}))$

- decision rule :  실제로 0, 1를 판단을 결정하는 규칙

  > $\hat{y}(x)=1 \iff p(y=1|\mathbf{x})>0.5$

트레이닝 셋에 대한 에러율이 0이 아니다. 그 이유는 데이터 자체가 이미 linearly separable하지 않기 때문이다. 이 문제를 해결하지 위해서는 basis function expansion을 이용해 non-linear decision boundaries를 만들어 주어야 한다.