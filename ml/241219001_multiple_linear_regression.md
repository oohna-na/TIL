## 다중선형회귀

-   여러 개의 독립변수(X들)을 이용해 하나의 종속변수(Y)를 예측하는 통계적 기법Y: 종속변수(예측하려는 값)b: 절편(intercept)
-   w₁, w₂, ...: 회귀 계수(coefficients)
-   X₁, X₂, ...: 독립변수들
-   **Y = b + w₁X₁ + w₂X₂ + ⋯ + wₙXₙ**

### 코드 구현

1.  모델 초기화

-   다중선형회귀 모델 객체 생성
-   `multi_regressor = LinearRegression()`

2.  모델 학습

-   train\_data: X₁, X₂, ... 같은 독립변수 데이터
-   train\_target: Y 예측값
-   모델이 데이터를 학습하여 w₁, w₂,... 와 절편 b값을 계산
-   `multi_regressor.fit(train_data, train_target)`

3.  결과 확인 (intercept와 coefficients)

-   절편 (intercept): 독립변수가 모두 0일 때 예상되는 결과값
-   계수 (coefficients): 각 독립변수가 결과값에 미치는 영향력
-   `print("intercept:", multi_regressor.intercept_) print("coefficients:", multi_regressor.coef_)`
