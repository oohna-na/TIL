## 연속형 변수 변환 Continuous Variable Transformation

### 함수 변환 

데이터의 분포를 조정하거나 비선형 관계를 선형으로 바꾸기 위해 수학적 변환을 적용

#### 1. 로그 변환

- 값의 범위를 축소하고, 데이터의 분포가 오른쪽으로 치우친 경우(왜도가 큰 경우) 정규분포에 가깝게 만든다.

- 예시: 소득 분포가 고소득층에 집중된 경우 로그 변환


#### 2. 제곱근 변환

- 데이터의 큰 값의 영향을 줄이고, 분포를 안정화한다.

- 예시: 특정 국가의 투자 금액이 다른 국가 대비 매울 클 때


#### 3. Box-Cox 변환

- 로그 변환, 제곱근 변환 등을 포함한 일반화된 변환 방법으로, 데이터 분포를 정규분포에 가깝게 만드는 데 사용된다.

- 조건: 데이터가 0보다 커야 함


### 스케일링

데이터의 스케일(크기)을 조정해 변수 간의 크기 차이를 줄이고, 모델 학습을 원활하게 만든다.

#### 1. Min-Max 스케일링

- 데이트럴 0과 1 사이로 변환

- 특징: 극단값(이상치)에 민감

- 예시: 상품 판매량 데이터를 0~1로 정규화


#### 2. 표준화(Standardization)

- 데이터를 평균 0, 표준편차 1로 변환

- 특징: 극단값 영향을 덜 받음

- 예시: 평균 타율을 중심으로 데이터 표준화

#### 3. 로버스트 스케일링(Robust Scaling)

- 중위수와 IQR(사분위수 범위)을 사용해 스케일 조정, 이상치 영향을 최소화

- 예시: 초고속 성장 국가 데이터를 포함한 소득 증가율


### 구간화(Binning)

연속형 데이터를 범주형 데이터로 변환하는 방법이다. 데이터를 구간으로 나누어 분석을 단순화하거나 해석력을 높이는 데 유용하다.

#### 구간화의 종류

- 등간 구간(Equal Width Binning): 데이터의 범위를 동일한 간격으로 나눔

- 등빈 구간(Equal Frequency Binning): 데이터를 동일한 개수로 나눔

- 도메인 기반 구간화: 비즈니스 요구에 따라 구간을 지정

- 예시: 선수의 나이를 "20대, "30대", "40대 이상"으로 구간화