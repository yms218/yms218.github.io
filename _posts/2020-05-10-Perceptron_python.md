---
title : "Perceptron - 구현"
excerpt : "Machine Learning"
use_math : true
categories :
  - 머신러닝
tags :
  - 퍼셉트론
---
[출처 : 머신러닝 교과서 with 파이썬, 사이킷런, 텐서플로]  

```python
import numpy as np
class Perceptron(object) :
    # eta : learning rate(0.0 ~ 1.0)
    # n_iter : 훈련 데이터 반복 횟수
    # random_state : 가중치 무작위 초기화
    # w_ : 학습된 가중치
    # errors_ : 에포크마다 누적된 분류 오류
    def __init__(self, eta = 0.01, n_iter = 50, random_state = 1):
        self.eta = eta
        self.n_iter = n_iter
        self.random_state = random_state

    def fit(self, f, x ,y):
        # x : train data, shape = [n_samples, n_features]
        # y : target, shape = [n_samples]
        rgen = np.random.RandomState(self.random_state)
        self.w_ = rgen.normal(loc = 0.0, scale = 0.01, size = 1 + x.hape[1])
        self.errors_ = []

        for _ in range(self.n_iter) :
            errors = 0
            for xi, target in zip(x,y) :
                update = self.eta + (target - self.predict(xi))
                self.w_[1:] += update * xi
                self.w_[0] += update
                errors += int(update != 0.0)
            self.errors_.append(errors)
        return self

    def net_input(self, x):
        return np.dot(x, self.w_[1:]) + self.w_[0]

    def predict(self, x):
        return np.where(self.net_input(x) >= 0.0, 1, -1)
```