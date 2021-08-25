# 덕트 공동 탐지를 위한 LSTM Auto-Encoder (LSTM Auto-Encoder for Duct Void Detection)

## 요약(abstract)
PSC 박스 거더교는 박스 형태의 거더에 미리 응력을 가한 교량으로 가장 많이 이용되는 방식이다. 그러나 콘크리트를 타설 할 때, 덕트의 내부 직경이 작기 때문에 작은 실수로도 공동이 발생할 수 있다. 또한 거더교의 장기간 유지 시에는 결함이 나타날 수 있다. 이러한 결함을 감지하기 위해 비파괴 검사인 Impact-Echo (IE)방식으로 데이터를 수집한다. 본 연구에서는 PSC 박스 거더교 내부 덕트의 정상과 공동 여부를 탐지하기 위한 방법을 제시한다. 이는 비지도 학습인 Auto-Encoder (AE)를 바탕으로 시계열 데이터 처리에 좋은 LSTM을 적용한다. 정상 IE 신호로 LSTM AE를 훈련시킨 후, 각 평가 데이터로 AE 모델의 Encoder에서 나온 Latent Vector를 통해 데이터의 분포를 비교 분석한다. 이때 사전 학습된 LSTM AE는 정상 데이터로 학습되었기 때문에, Encoder에 공동 데이터를 넣어서 나온 Latent Vector는 정상 데이터 Latent Vector와 낮은 유사도를 갖는다. 그러므로 구해진 평균 유사도를 통해 모델의 성능을 평가할 수 있고, PSC 박스 거더교 내부에 있는 덕트의 정상과 공동 여부를 예측 가능하다.

## 목차
1. 서론
2. 데이터
    1.PSC 시험체 
    2.Impact-Echo 신호
3. 방법론
    1. LSTM Auto-Encoder
    2. Latent Vector
    3. Cosine Similarity
4. 실험 결과
5. 결론

------
### 1. 서론
![image](https://user-images.githubusercontent.com/57992071/130766849-744a4621-044e-4612-ac48-d35f33307266.png)

[그림1] PSC (Prestressed Concrete) 개요도

### 2.1 데이터-PSC 시험체
![image](https://user-images.githubusercontent.com/57992071/130766983-4385a132-4196-4c22-adfa-a469caf5da56.png)

[그림 2] 제작된 7가지의 PSC 시험체

-----
### 3.1 방법론-LSTM Auto-Encoder
![image](https://user-images.githubusercontent.com/57992071/130767042-aeb334a2-42f1-49e0-a460-4e7652bf2398.png)

[그림 3] Filtering된 IE 신호와 LSTM AE 모델 구조

### 3.3 방법론-Latent Vector
![image](https://user-images.githubusercontent.com/57992071/130767114-95ba6507-5f47-48ad-b504-d6da70fc63b6.png)

[그림 4] Pretrained LSTM Encoder의 Latent Vector 생성

------
### 4. 실험 결과
![image](https://user-images.githubusercontent.com/57992071/130767171-a6d5605e-5e4c-4221-8bbb-2251505cd382.png)

[그림 5] AE의 입력 및 출력 IE 신호

![image](https://user-images.githubusercontent.com/57992071/130767240-103f2ef4-e8b9-45bb-875a-55c1d8d26af1.png)

[표 1] 시험체 두께에 따른 Cosine Similarity 평균

------

## 5. 결론
본 연구는 LSTM Auto-Encoder의 성질을 이용한 Latent Vector을 통해 평균 Cosine Similarity로 데이터를 비교 분석한다. 모델의 훈련 데이터는 정상 IE신호로만 이루어지며, 정상 IE신호를 평가한 결과와 결함이 있는 공동 IE신호를 포함하여 평가한 결과를 비교한다. 모두 어느 정도의 차이로 평균 Cosine Similarity가 낮아지며, 눈에 띄는 유사도 차이를 보이는 두께는 7가지의 PSC 시험체 중 45, 70, 90cm이다. 결론적으로, 정상 데이터로 훈련된 AE에 비정상 데이터가 입력되면 정상 Latent Vector와의 차이가 나타남을 알 수 있고 이를 통한 PSC 덕트 공동 탐지가 가능하다.
