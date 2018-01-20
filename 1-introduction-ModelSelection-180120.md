# Introduction

## 1.4 Some basic concepts in ML

### 1.4.7 Overfitting

minor variation에 까지 적용되는 것을 피해야 한다.

- K-nearest neighbor 경우 
  - k=1일 경우, training set error가 없다. but wiggle (overfitiing)

### 1.4.8 Model selction

적합한 모델을 선택하는 방법

- misclassification error : training set에 대한 error

  $error(f,D)={1 \over N} \sum\mathbb{I}(f(x_i)\ne y_i)$

- generalization error : test 값에 대한 error

  - 보통 U-fit : parameter가 너무 적으면 overfit, 너무 많으면  underfit

- 적합한 모델을 찾기 위해서는  generalization error가  적은 값을 모델로 선택한다.

- 하지만 보통은 test set이 없기 때문에 train set으로 training해야 한다.



#### train set으로 test하는 법

1.  traning set을 train set과 validation set으로 나누어 훈련시키는 방법



2. Cross Validation
   - data를 k-fold로 나눈 뒤, $k_{th}$ 번째를 제외한 fold로 훈련시키고 $k_{th}$의 fold로 검증하여 error를 계산한다. 그리고 이름 k번 반복하여 평균 error를 구한다.
   - fold = 5, 5-fold CV
   - fold = N, Leave One Out Cross Validation

### 1.4.9 No free lunch teorem

모든 문제에 모두 적합한 모데은 존재하지 않는다.

- 그러므로 우리는 실제 문제에 발생하는 다양한 모델을 실험하여 구해야 한다.