---
title : "Perceptron - (1)"
excerpt : "Machine Learning"
use_math : true
categories :
  - 머신러닝
tags :
  - 퍼셉트론
---
* **Perceptron : 수학적 정의**    
- 출처 : 머신러닝 교과서 with 파이썬, 사이킷런, 텐서플로  

$$w=\left[ \begin{matrix} { w }_{ 1 } \\ \vdots  \\ { w }_{ m } \end{matrix} \right] ,\quad x=\left[ \begin{matrix} { x }_{ 1 } \\ \vdots  \\ { x }_{ m } \end{matrix} \right]$$   

$$z={ w }_{ 1 }{ x }_{ 1 }+\dots +{ w }_{ m }{ x }_{ m }={ w }^{ T }x$$  
z : 가중치 벡터 w의 전치행렬(transpose)과 입력 벡터 x의 dot product

$$\phi (z)=\begin{cases} 1,\quad z\ge 0\quad  \\ -1,\quad else \end{cases}$$  

$$\phi (z)$$ : 결정함수, 단위 계단 함수(unit step function) 사용  

* **Perceptron Algorithm : 두 개의 클래스(-1,1)가 있는 이진 분류**
![](/assets/images/weight.png){: .align-center}
샘플 x를 입력으로 받아 가중치 w를 연결하여 최종 입력을 계산하게 되는데 결정 함수를 거쳐 최종적으로 샘플의 예측 클래스인 $$\hat { y } ^{ (i) }$$이 -1 또는 1로 이진 분류가 진행되게 됩니다. 그 이후에 $$\hat { y } ^{ (i) }$$을 이용하여 가중치를 업데이트를 하면서 학습이 이루어지게 됩니다.  

$${ \Delta w }_{ j }=\eta ({ y }^{ (i) }-\hat { y } ^{ (i) }){ x }_{ j }^{ (i) }$$  
$$\eta$$ : 학습률(Learning Rate : 0.0 ~ 1.0)   
$${ y }^{ (i) }$$ : true class label  
$$\hat { y } ^{ (i) }$$ : predicted class label  
