## 선형 회귀 모델

### Line Fitting 관점에서의 선형 회귀 모델

직선의 기울기(a)와 y절편(b)을 조절해 데이터(점들)와의 **오차**가 가장 작아지도록 만들기

$$  
f\_{a,b}: \\mathbb{R} \\to \\mathbb{R} \\  
x \\mapsto ax + b  
$$

### MSE 손실함수

여기서 **오차**는 목표값과 출력값 간 **차이의 제곱**으로 정의되는, **MSE(Mean Squared Error) 손실함수**를 사용

$$  
Loss\_{MSE} : \\mathbb{R}, \\mathbb{R} \\to \\mathbb{R} \\  
\\phantom{Loss\_{MSE}} \\quad \\quad \\quad\\ y, \\hat{y} \\mapsto (y - \\hat{y})^2  
$$

### 최적화 문제로서의 선형회귀

고정된 X, Y 데이터셋에서 a, b에 따라 손실함수의 값을 그려보면, 아래와 같은 **convex함수**가 된다.

![](https://miro.medium.com/v2/resize:fit:1180/format:webp/0*hk3v9ZcPjToCfGIg.png)

source: [https://codatalicious.medium.com/what-makes-convex-functions-so-special-for-machine-learning-4365d7e90c85](https://codatalicious.medium.com/what-makes-convex-functions-so-special-for-machine-learning-4365d7e90c85)

이 관점에서 linear regression은 오른쪽과 같은 손실함수의 **argmin**(최소값이 되는 a, b)값을 찾는 **컨벡스 최적화(Convex Optimization) 문제**로 볼 수 있다.

최적화 문제의 **해를 구하는 방법**은 어떤 것들이 있을까?

### 최적화의 해석적 해법과 수치적 해법

해석적 해법 (Analytical Solution): 직접적으로, 데이터의 값을 입력하는 것만으로 빠르고 간편하게 **정확한** 값을 구할 수 있지만, **미리 해법이 알려진 경우**에만 사용할 수 있어 사용 조건이 까다롭거나, 아예 쓸수 없는 경우도 많음

수치적 해법(Numerical Solution): 결과가 **근사값**으로 나오고, 여러 단계를 거쳐야해 **시간**이 많이 필요한 경우가 많다. 대신 좀 더 일반적으로, 많은 경우에 사용이 가능하다.

### 최소제곱 선형회귀분석의 해석적 해법

**데이터 X, y**가 다음과 같이 정의되고, **MSE 손실함수를 사용**하는 다중 선형회귀 분석의 경우,

$$  
X = \\begin{bmatrix}  
x\_1^T \\  
x\_2^T \\  
\\vdots \\  
x\_n^T  
\\end{bmatrix}, \\quad (\\text{where } x\_i \\in \\mathbb{R}^m)  
\\qquad  
y = \\begin{bmatrix}  
y\_1 \\  
y\_2 \\  
\\vdots \\  
y\_n  
\\end{bmatrix}  
$$

다음과 같은 해석적 해법(Analytical Solution)을 사용해 파라미터 (\\theta)를 구할 수 있다.

$$  
\\theta = (X^T X)^{-1} X^T y  
$$

하지만 사실, 중간에 들어가는 **역행렬**을 구하는 것이 어려워서 이 부분만 **수치적**으로 풀기도 한다.
