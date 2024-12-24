## 데이터 전처리 Data Preprocessing

- 머신러닝, 데이터 분석, 데이터 과학에서 원본(raw) 데이터를 모델에 적합한 형태로 변환하는 과정

- 모델 성능 향상, 분석 정확성 증대, 노이증 감소 등을 위해 필수적

### 주요 목적

- 데이터 품질 향상: 결측값, 이상치 처리 등을 통해 데이터의 정확성과 신뢰성을 높임

- 모델 성능 최적화: 모델이 데이터를 효과적으로 학습할 수 있도록 변환

- 데이터의 일관성 유지: 서로 다른 소스의 데이터를 통합하여 일관성을 유지

- 특징(feature) 추출 및 변환: 모델 학습에 유용한 데이터를 강조하거나 불필요한 데이터를 제거

### 1. 데이터 분석 (Exploratory Data Analysis, EDA)

- EDA는 데이터의 패턴, 분포, 특성 등을 이해하기 위한 초기 분석 단계

- 주요 작업

    - 데이터 구조 확인: 데이터 크기, 열의 데이터 타입, 결측값 여부 확인

    - 데이터 시각화

        - 분포 확인: 히스토그램, 상자 그림(Boxplot)

        - 상관관계 분석: sns.heatmap(), df.corr()

        - 예시

        ```python
        import seabron as sns
        sns.boxplot(data=df['variable])
        ```

        - 값의 분포
            - 데이터의 최솟값, 최댓값, 평균, 표준편차 확인

### 2. 결측치 처리

- 결측값(Missing Values)은 데이터가 비어있는 경우로, 처리하지 않으면 모델 성능에 영향을 미칠 수 있음

- 처리 방법

    - 삭제

        - 결측값이 많거나 해당 값이 분석에 큰 영향을 미치지 않을 경우

        ```python
        df.dropna(inplace=True)
        ```
    
    - 대체(Imputation)

        - 결측값을 다른 값으로 채움

            - 수치형 변수: 평균, 중앙값, 최빈값

            ```python
            df['column'].fillna(df['column'].mean(), implace=True)
            ```

            - 범주형 변수: 최빈값(mode)로 채움

            ```python
            df['category'].fillna(df['category'].mode()[0], inplace=True)
            ```
        - 예측 기반 대체

            - 결측값을 다른 변수로 예측하여 채움 (회귀, KNN 등)
    
### 이상치 처리

- 이상치(Outliers)는 데이터 분포에서 비정상적으로 벗어난 값을 의미

- 탐지 방법

    - 시각적 탐지: Boxplot, Scatter Plot
    
    ```python
    sns.boxplot(data=df['variable'])
    ```

    - 수치적 탐지

        - IQR (Interquartile Range)

        ```python
        Q1 = df['variable'].quantile(0.25)
        Q3 = df['variable'].quantile(0.75)
        IQE = Q3 - Q1
        lower_bound = Q1 - 1.5 * IQR
        upper_bound = Q3 + 1.5 * IQR
        outliers = df[(df['variable'] < lower_bound) | (df['variable'] > upper_bound)]
        ```
- 처리 방법

    1. 제거

        - 이상치를 제거하여 분석
        
        ```python
        df = df[(df['variable'] >= lower_bound & df['variable'] <= upper_bound>)]
        ```
    
    2. 변환

        - 로그 변환, 클리핑 등으로 이상치를 조정
        
        ```python
        df['variable'] = df['variable'].clip(lower_bound, upper_bound)
        ```
    3. 대체

        - 평균값, 중앙값 등으로 대체




