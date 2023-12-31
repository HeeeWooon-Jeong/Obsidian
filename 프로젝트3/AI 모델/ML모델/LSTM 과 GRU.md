

## LSTM 

> [!NOTE] LSTM
> LSTM(LSTM: Long Short-Term Memory)는 순환 신경망(RNN)의 한 유형으로, 시퀀스 데이터 및 시계열 데이터를 모델링하는 데 사용되는 강력한 구조입니다. 
> LSTM은 RNN의 변형 중 하나로, 과거 정보를 장기 및 단기 메모리 상태로 관리하며 장기 의존성 문제를 효과적으로 해결하는 데 도움이 됩니다.

LSTM은 다음과 같은 주요 특징을 갖습니다:

1. **셀(Cell)**: LSTM은 셀이라고 불리는 단위로 구성되어 있습니다. 각 셀은 현재 입력, 이전 시간 스텝의 은닉 상태, 이전 셀의 상태를 입력으로 받아 새로운 은닉 상태와 현재 셀의 상태를 출력합니다.

2. **장기 메모리(Long-Term Memory)**: LSTM은 장기 메모리 상태를 유지합니다. 이 상태는 데이터의 장기 의존성을 캡처하는 데 사용됩니다. 정보를 추가, 삭제 또는 유지할 수 있는 덧셈 게이트와 삭제 게이트가 있습니다.

3. **단기 메모리(Short-Term Memory)**: LSTM는 단기 메모리 상태도 유지합니다. 이 상태는 현재 시간 스텝에서 중요한 정보를 저장하는 데 사용됩니다.

4. **게이트(Gates)**: LSTM은 게이트 메커니즘을 사용하여 정보의 흐름을 제어합니다. 게이트는 정보를 얼마나 통과시킬지를 결정하고 이전 정보를 유지 또는 삭제합니다. LSTM에는 입력 게이트, 삭제 게이트, 출력 게이트가 있습니다.

5. **그라디언트 소실 문제 해결**: RNN의 주요 문제 중 하나는 장기 의존성을 모델링할 때 그라디언트 소실 문제가 발생하는 것입니다. LSTM은 이러한 문제를 일부 해결하며 더 긴 시퀀스를 처리할 수 있습니다.

LSTM은 자연어 처리, 음성 처리, 시계열 예측 및 다양한 시퀀스 데이터 처리 작업에서 효과적으로 사용됩니다. LSTM은 이전 시간 스텝의 정보를 기억하고 다음 시간 스텝에서 현재 입력과 결합하여 출력을 생성하므로 시간에 따른 의존성을 모델링하는 데 적합합니다.

---

## GRU


> [!NOTE] GRU
> GRU (Gated Recurrent Unit)는 LSTM (Long Short-Term Memory)과 마찬가지로 순환 신경망 (RNN)의 한 유형입니다. 
> LSTM의 변형 중 하나로, 장기 의존성 문제를 해결하면서도 더 간단한 구조를 가지고 있습니다.
> GRU는 다음과 같은 주요 특징을 가지고 있습니다:

1. **셀과 게이트**: GRU는 LSTM과 마찬가지로 셀을 사용하지만, LSTM보다 더 간단한 게이트 메커니즘을 사용합니다. GRU에는 업데이트 게이트와 재설정 게이트가 있으며, 이 게이트들은 정보의 흐름을 제어합니다.

2. **업데이트 게이트**: 업데이트 게이트는 현재 입력과 이전 상태가 셀 상태를 얼마나 업데이트할지를 제어합니다. 이것은 LSTM의 입력 게이트와 유사한 역할을 합니다.

3. **재설정 게이트**: 재설정 게이트는 이전 상태를 얼마나 재설정할지를 결정합니다. 이것은 LSTM의 삭제 게이트와 유사한 역할을 합니다.

4. **장기 및 단기 메모리**: GRU는 LSTM과 달리 명시적인 장기 및 단기 메모리 상태를 유지하지 않습니다. 대신, 하나의 은닉 상태만을 사용하여 정보를 유지하고 전달합니다.

5. **매개변수의 수 감소**: GRU는 LSTM보다 매개변수의 수가 적습니다. 이로 인해 학습 및 예측 속도가 빨라질 수 있습니다.

GRU는 LSTM과 마찬가지로 순환 신경망을 사용하여 시퀀스 데이터 및 시계열 데이터를 처리하며, 그라디언트 소실 문제를 일부 해결합니다. 또한 모델의 복잡성이 낮아 LSTM보다 간단한 모델을 만들 수 있어 학습 및 예측이 더 빠릅니다.

GRU와 LSTM 중 어떤 모델을 선택할지는 데이터와 작업의 특성에 따라 다를 수 있으며, 어떤 모델이 더 잘 수행되는지를 비교하기 위해 실험을 수행하는 것이 중요합니다.
