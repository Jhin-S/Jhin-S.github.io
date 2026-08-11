---
title: "1-3 Building a Simple Neural Network"
date: 2026-08-12 04:17:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, neural-network, training-loop]
math: true
---

## 1. Import & Data Representation (임포트 및 데이터 표현)

**[KR]**
* **핵심 모듈 (Core Modules):**
  * `torch`: PyTorch 기본 라이브러리
  * `torch.nn`: 신경망 레이어 및 손실 함수 제공
  * `torch.optim`: 최적화 알고리즘 제공 (예: SGD, Adam)
* **텐서 형태의 데이터 (Data as Tensors):**
  * 텐서(Tensors)는 GPU/CPU 연산에 최적화된 다차원 배열 데이터 구조입니다.
  * **배치 구조 (Batch Structure):** 바깥쪽 대괄호는 전체 배치(샘플들의 집합)를 의미하며, 안쪽 대괄호는 개별 샘플을 의미합니다.
  * **특성 (Features):** 안쪽 대괄호 내부 값의 개수는 입력 특성의 개수를 나타냅니다 (예: 1개 = 배달 거리 1개).
  * `dtype=torch.float32`: 32비트 부동소수점 형으로, 정밀한 실수 연산에 표준으로 사용됩니다.

**[EN]**
* **Core Modules:**
  * `torch`: Core PyTorch library.
  * `torch.nn`: Neural network layers & loss functions.
  * `torch.optim`: Optimization algorithms (e.g., SGD, Adam).
* **Data as Tensors:**
  * Tensors are multi-dimensional arrays optimized for GPU/CPU mathematical operations.
  * **Batch Structure:** Outer brackets represent the Batch (Collection of samples); inner brackets represent individual Samples.
  * **Features:** Number of values inside each inner bracket corresponds to input features (e.g., 1 feature = distance).
  * `dtype=torch.float32`: 32-bit floating point, standard for precise real number computations.

### 예시 코드 (Example Code)
```python
import torch

data = torch.tensor(
    [
        [1.5, 0.8], # 1번 배달건 (Batch 1)
        [3.2, 1.2], # 2번 배달건 (Batch 2)
        [0.8, 0.4], # 3번 배달건 (Batch 3)
    ],
    dtype=torch.float32 # 3개의 배달 건(Batch=3)에 대해 각각 [배달거리, 음식무게] (Feature=2) 데이터를 가짐
)
```
## 2. Model Architecture & Setup (모델 아키텍처 및 설정)
**[KR]**
* **모델 정의 (Model Definition - nn.Sequential)**
  * 순차적 컨테이너로, 입력값을 레이어 순서대로 전달합니다.
  * `nn.Linear(in_features=1, out_features=1)`: $y = Wx + B$ 연산을 수행하는 단일 뉴런 레이어입니다.
* **손실 함수 및 최적화 도구 (Loss Function & Optimizer):**
  * 손실 함수 (`nn.MSELoss`): 예측값과 실제값 차이의 제곱 평균(MSE)을 측정합니다.
  * 최적화 도구 (`optim.SGD`): 확률적 경사하강법(SGD)을 사용하여 모델의 파라미터($W, B$)를 수정합니다.
  * 학습률 (`lr, Learning Rate`): 파라미터 업데이트 시 이동하는 보폭(Step size)을 조절합니다.
**[EN]**
* **Model Definition (`nn.Sequential`):**
  * Sequential container passes inputs through layers in strict order.
  * `nn.Linear(in_features=1, out_features=1)`: Single neuron performing $y = Wx + B$.
* **Loss Function & Optimizer:**
  * Loss Function (`nn.MSELoss`): Measures average squared difference between predictions and targets.
  * Optimizer (`optim.SGD`): Adjusts model parameters() ($W, B$) using Stochastic Gradient Descent.
  * Learning Rate (`lr`): Controls the step size during parameter updates.

## 3. The Training Loop Step-by-Step (학습 루프 5단계)
**[KR]**
* **에포크 (Epoch): 전체 학습 데이터셋을 한 번 모두 통과하는 단위입니다.**
* **학습 루프 내부 5단계 핵심 동작 (5 Key Operations inside the Loop):**
  * 1) `optimizer.zero_grad()`: 누적된 이전 에포크의 기울기(Gradient) 값을 초기화합니다.
  * 2) `outputs = model(inputs)`: 순전파(Forward Pass) - 모델 예측값을 계산합니다.
  * 3) `loss = loss_fn(outputs, targets)`: 예측 오차를 측정합니다.
  * 4) `loss.backward()`: 역전파(Back propagation) - 미분을 이용해 $W, B$의 기울기를 계산합니다.
  * 5) `optimizer.step()`: 계산된 기울기와 학습률을 바탕으로 $W, B$ 파라미터를 업데이트합니다.

**[EN]**
* **Epoch: One complete pass through the entire training dataset.**
* **5 Key Operations inside the Loop:**
  * 1) `optimizer.zero_grad()`: Clears old gradients to prevent accumulation across epochs.
  * 2) `outputs = model(inputs)`: Forward Pass - Computes predictions.
  * 3) `loss = loss_fn(outputs, targets)`: Calculates prediction error.
  * 4) `loss.backward()`: Back propagation - Computes gradients of $W$ and $B$ using calculus.
  * 5) `optimizer.step()`: Updates weights and bias based on computed gradients.

## 4. Inference Mode (추론 모드)
**[KR]**
* **컨텍스트 매니저 (Context Manager - `with torch.no_grad():`):**
  * 추론 단계에서 기울기 계산 기능을 비활성화합니다.
  * 파라미터 업데이트가 필요 없으므로 연산 속도가 빨라지고 메모리 사용량이 절감됩니다.
* **목표 (Goal): 학습된 모델이 새로운 배달 거리에 대해 정확한 시간을 예측하는지 테스트합니다.**
**[EN]**
* **Context Manager (`with torch.no_grad():`):**
  * Disable gradient calculation during inference.
  * Reduces memory consumption and speeds up computation since parameter updates are not needed.
* **Goal: Test if the trained model accurately predicts delivery times for new distances.**

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-3 Building a Simple Neural Network-1" src="https://github.com/user-attachments/assets/6fe49353-52c9-42b6-abbd-9d2d6dab65d4" />
    <img width="1264" height="1635" alt="1-3 Building a Simple Neural Network-2" src="https://github.com/user-attachments/assets/306fdf10-65dc-471a-8199-4eccea9206c6" />
    <img width="1264" height="1635" alt="1-3 Building a Simple Neural Network-3" src="https://github.com/user-attachments/assets/3a55067c-edc8-49c2-be74-118812d3b29e" />
  </div>
</details>
