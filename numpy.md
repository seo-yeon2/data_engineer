# Numpy 정리

## Numpy 개요

### 특징
- **다차원 배열(ndarray)**을 효과적으로 처리할 수 있도록 도와주는 라이브러리
```
다차원 배열?
- 1차원 : 벡터 []
- 2차원 : 행렬 [[]]
- 3차원 이상 : 텐서 [[[...]]]
```
- python의 기본 list 보다 빠르고 강력한 기능 제공
- **벡터화 연산(Vetorized operaiton)** 가능

## 1차원 배열

### 벡터 속성

1. 벡터의 차원(dimension, axis) 개수

    문법: vector.ndim
    
    결과: 1

2. 벡터의 각 차원의 크기(shape) 

    문법: vector.shape
    
    결과: 벡터 내 요소 수를 tuple로 반환

3. 벡터의 총 요소 갯수(size)

    문법: vector.size

4. 벡터의 저장 데이터

    문법: vector.dtype
    
    결과: 벡터의 데이터 타입 알려줌 

### 생성 방법

1. 지정값으로 생성

    문법 : 변수 = np.array(리스트|튜플)
    ```
    <class 'numpy.ndarray'>
    ```
    --------------
    - upcasting

        데이터가 정수와 실수가 섞여있으면.. 자동으로 큰 데이터 타입(실수)으로 변경되는 것
        ```
        list_value = [10., 20, 30]
        vector1 = np.array(list_value)
        print(vector1, type(vector1), vector1.dtype)

        결과
        [10. 20. 30.]
        ```
        데이터 타입 변경하기
        
            dtype=np.데이터타입
            
            예시)
            list_value = [10., 20., 30.]
            vector1 = np.array(list_value, dtype=np.int32)
            print(vector1, type(vector1), vector1.dtype)

            결과
            [10 20 30]

2. 랜덤함수

    1. 랜덤값 고정

        문법: np.random.seed(1234)

    2. [0.0, 1.0) 사이의 임의의 float 값

        문법: np.random.random(개수)

        * 개수 생략하면 1개의 랜덤값 반환

        ```
        예시)
        arr = np.random.random(5)
        print(arr)
        
        => [0.62210877 0.43772774 0.78535858 0.77997581 0.27259261]
        ```

    3. 균등분포에서 표본 추출

        ; 0~1의 균등분포에서 표본 추출

        문법: np.random.rand(개수)

        * 개수 생략하면 1개의 랜덤값 반환
        ```
        예시)
        arr = np.random.rand(5)
        print(arr)
        
        => [0.80187218 0.95813935 0.87593263 0.35781727 0.50099513]
        ```

    4. 정규분포에서 표본 추출

        ; 표준편차가 1이고 평균값이 0인 정규분포에서 표본 추출

        문법: np.random.randn(개수)

        * 개수 생략하면 1개의 랜덤값 반환
        ```
        예시)
        arr = np.random.randn(5)
        print(arr)
        
        => [ 0.99194602  0.95332413 -2.02125482 -0.33407737  0.00211836]
        ```
    
    5. 최대, 최소 범위 내에서 임의의 난수 추출

        문법: np.random.randint(low, high, n)

        * n개의 난수 추출
        * [최소, 최대)
        * 최소 생략 가능 (0부터 시작)
        * 복원 추출
        ```
        예시)
        arr = np.random.randint(1,10,3)
        print(arr)
        
        => [3 7 4]

        arr = np.random.randint(5, size=4)
        print(arr)
        
        => [3 0 1 3]
        ```

    6. 주어진 리스트에서 임의의 값 1개 반환

        문법: np.random.choice(리스트)

        ```
        예시)
        arr = np.random.choice(['a', 'b', 'ac'])
        print(arr)
        
        => a
        ```