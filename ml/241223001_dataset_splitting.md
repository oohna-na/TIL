## 데이터셋 분할

### 2분할 방법 (Train-Test Split)

- 데이터를 훈련 데이터(Train Set)와 테스트 데이터(Test Set)로 나누는 가장 기본적인 방법

- 훈련 데이터(Train Set)

    - 모델을 학습시키는 데 사용

    - 데이터셋의 대다수를 차지(보통 70~80%)

- 테스트 데이터(Test Set)

    - 학습된 모델을 평가하는 데 사용

    - 데이터셋의 나머지 부분(보통 20~30%)

- 장점

    - 간단하고 빠름

    - 작은 데이터셋에서 빠르게 모델 성능 확인 가능

- 단점

    - 편향 문제: 데이터가 한 번만 나누어지기 때문에 특정 분할이 운 좋게 또는 나쁘게 설정되면 평가 결과가 왜곡될 수 있음

    - 데이터가 적은 경우, 테스트 데이터가 충분하지 않을 수 있음

- 예시

    ```python
    from sklearn.model_selection import train_test_split

    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=43)
    ```


### 3분할 방법 (Train-Validation-Test Split)

- 데이터를 훈련 데이터(Train Set), 검증 데이터(Validation Set), 테스트 데이터(Test Set)로 나누는 방법

- 모델 학습과 하이퍼파라미터 튜닝을 별도로 처리하기 위한 구조

- 훈련 데이터(Train Set)

    - 모델을 학습시키는 데 사용

    - 전체 데이터의 60~70%

- 검증 데이터(Validation Set)

    - 하이퍼파라미터 튜닝과 모델 성능을 확인하는 데 사용

    - 전체 데이터의 10~20%

- 테스트 데이터(Test Set)

    - 최종적으로 모델 성능을 평가하는 데 사용

    - 전체 데이터의 10~20%

- 장점

    - 모델 학습과 평가를 구분하여 테스트 데이터의 정보 누출을 방지

    - 하이퍼파라미터 튜닝에 적합

- 단점

    - 데이터가 작을 경우, 훈련 데이터가 부족해질 수 있음

    - 검증 데이터와 테스트 데이터가 작으면 평가 신뢰성이 떨어질 수 있음

- 예시

    ```python
    from sklearn.model_selection import train_test_split

    X_train, X_temp, y_train, y_temp = train_test_split(X, y, test_size=0.4, random_state=42)
    X_val, X_test, y_val, y_test = train_test_split(X_temp, y_temp, test_size=0.5, random_state=42)
    ```


### k-fold 교차검증 (k-fold Cross Validation)

- 데이터를 k개의 폴드(Folds)로 나눈 뒤, 각 폴드를 테스트 세트로 번갈아 가며 사용하는 방법

- 훈련과 테스트를 여러 번 반복하여 모델 성능을 안정적으로 평가

- 구성

    1. 데이터를 k개의 동일한 크기의 포드로 분할

    2. k번 반복
        
        - 한 폴드를 테스트 세트로 사용

        - 나머지 k-1개의 폴드를 훈련 세트로 사용  

    3. k번의 테스트 결과를 평균내어 최종 모델 성능을 평가

- 장점

    - 데이터를 한 번만 나누는 2분할/3분할보다 평가 결과가 더 안정적

    - 데이터가 적더라도 효율적으로 사용 가능

- 단점

    - 계산량이 많아 학습 시간이 오래 걸림

    - 결과를 종합하기 위해 추가적인 처리가 필요

- 예시

    ```python
    from sklearn.model_selection import KFold
    from sklearn.metrics import accuracy_score

    kf = KFold(n_splits=5, shuffle=True, random_state=42)
    for train_index, test_index in kf.split(X):
        X_train, X_test = X[train_index], X[test_index]
        y_train, y_test = y[train_index], y[test_index]
        model.fit(X_train, y_train)
        y_pred = model.predict(X_test)
        print("Accuracy: ", accuracy_score(y_test, y_pred))
    ```
