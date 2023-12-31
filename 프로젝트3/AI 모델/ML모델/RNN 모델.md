
> [!NOTE] RNN
> RNN(Recurrent Neural Network)은 순환 신경망의 한 유형으로, 
> 시퀀스 데이터와 시간에 따른 의존성을 모델링하는 데 사용됩니다.
> RNN은 다양한 자연어 처리 및 시계열 데이터 분석 작업에 적합한 강력한 모델입니다. 
> 아래에서 RNN의 기본 개념과 작동 방식을 설명하겠습니다:


1. **순환성(Recurrence)**:
   - RNN은 입력과 이전 단계(이전 타임 스텝)의 출력을 고려하여 현재의 출력을 계산합니다. 이것은 순환성을 의미합니다. RNN은 과거 정보를 현재 계산에 활용하며, 이전 타임 스텝의 상태를 기억하고 갱신합니다.

2. **시간 스텝(Time Step)**:
   - 시퀀스 데이터는 시간에 따른 연속적인 데이터입니다. 각 데이터 포인트 또는 단골은 시간 스텝에 해당합니다. RNN은 시간 스텝마다 입력을 받아 처리하며, 각 시간 스텝에서의 출력은 다음 시간 스텝의 입력으로 사용됩니다.

3. **은닉 상태(Hidden State)**:
   - RNN은 시간 스텝 간에 은닉 상태를 유지합니다. 현재 시간 스텝의 입력과 이전 시간 스텝의 은닉 상태를 결합하여 현재 시간 스텝의 은닉 상태를 계산합니다. 은닉 상태는 모델이 과거 정보를 기억하고 다음 출력을 예측하는 데 사용됩니다.

4. **역전파(Backpropagation Through Time, BPTT)**:
   - RNN은 역전파 알고리즘을 사용하여 가중치를 학습합니다. BPTT는 RNN의 모든 시간 스텝을 거쳐 역전파를 수행하여 모델을 훈련합니다.

RNN은 다양한 종류의 레이어를 가질 수 있으며, 일반적으로 LSTM(Long Short-Term Memory) 및 GRU(Gated Recurrent Unit)와 같은 변형이 사용됩니다. 이러한 변형은 장기 의존성을 모델링하고 그라디언트 소실 문제를 해결하는 데 도움이 됩니다.

RNN은 다음과 같은 응용 분야에서 사용됩니다:
- 자연어 처리: 문장 구문 분석, 기계 번역, 감정 분석 등.
- 시계열 데이터 분석: 주식 가격 예측, 날씨 예보, 센서 데이터 분석 등.
- 음성 인식: 음성 명령 처리, 음성 텍스트 변환 등.

RNN은 시간에 따른 의존성을 모델링하는 데 강력한 도구이지만, 장기 의존성을 처리하는 데 어려움이 있을 수 있으며, 그라디언트 소실 문제와 폭발 문제가 발생할 수 있습니다. 이러한 문제를 해결하기 위해 LSTM 및 GRU와 같은 변형이 개발되었고, 더 발전된 모델인 트랜스포머(Transformer)도 등장했습니다.


시계열 데이터
- 시간에 따라 변경되는 데이터
 과거의 데이터와 현재 데이터가 같은 가중치를 공유한다.

 First Order System
 현재 시간의 상태가 이전 시간의 상태와 관련이 있다고 가정함
 X0 -> X1 -> X2 일때
 X1에 대한 결과에 X0의 영향이 미치고
 X2에대한 결과에 X1만 영향을 미침  (이전의 상태만 영향을 미친다)

