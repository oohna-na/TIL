## KNN Imputer

- K-Nearest Neighbors (KNN) 알고리즘을 기반으로 결측채 채우는 방법

- 데이터의 결측치를 같은 데이터셋 내에서 가장 유사한 샘플(k개의 이웃)들의 값을 사용해 채움

- 이웃의 값을 평균, 중앙값 등으로 결합하여 결측치를 대체

- scikit-learn의 sklearn.impute.KNNImputer를 사용하여 쉽게 구현


### KNN Imputer 작동 방식

1. 결측치 탐지

    - 데이터에서 결측치(NaN)를 탐지

2. 유사도 계산

    - 결측치가 포함된 행과 다른 모든 행 간의 유사도를 계산

    - 유사도는 유클리디안 거리로 측정됨

3. 가까운 이웃 선택

    - 가장 가까운 k개의 이웃을 선택(n_neighbors)


4. 결측치 대제

    - 선택된 k개의 이웃의 값을 기반으로 결측치를 채움

    - 기본적으로 평균값이 사용되지만 다른 방식으로 대체 가능

### KNN Imputer 주요 파라미터터

- n_neighbors

    - KNN 알고리즘에서 사용할 이윳의 개수를 설정

    - 기본값은 5

    - n_neighbors가 클수록 결측치 대체값이 더 부드러워지지만 계산 시간 늘어남

- weights

    - 이웃 값의 가중치를 설정

    - uniform: 모든 이웃의 가중치를 동일하게 설정 (기본값)

    - distance: 가까운 이웃에게 더 큰 가중치를 부여

- metric

    - 거리 계산 방식을 설정

    - 기본값은 nan_euclidean으로 결측치를 무시하고 나머지 변수들로 유클리디안 거리를 계산


### 장점

1. 연속형 변수 처리를 다룰 때 유용

2. 데이터의 패턴을 유지

3. 다차원 데이터에서 변수 간 관계를 반영해 결측치 대체


### 단점

1. 데이터 크기와 변수 수가 많아질수록 계산 시간이 매우 길어짐

2. 차원이 높아지면 거리 계산이 덜 효과적일 수 있음

3. 결측치가 많은 경우, 거리 계산에 사용할 정보가 부족해 대체값이 부정확할 수 있음

### 사용법

```python
from sklearn.impute import KNNImputer

imputer = KNNImputer(n_neighbors=5)

imputed_data = imputer.fit_transform(data)
```