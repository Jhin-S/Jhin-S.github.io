---
title: "2-2 Overview of ML Pipeline with PyTorch Part 2: Models"
date: 2026-08-12 05:11:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, nn-module, training-loop, evaluation]
math: true
---

## 1. Building Models with `nn.Module` (`nn.Module` 기반 모델 구축)

**[KR]**
* **커스텀 PyTorch 모델 구조 (Structure of Custom PyTorch Models):**

```python
import torch.nn as nn #

class CustomModel(nn.Module): 
    def __init__(self): 
        super().__init__() # 필수: 파라미터 추적 및 등록 시스템 초기화
        self.fc1 = nn.Linear(784, 128) 
        self.relu = nn.ReLU() 
        self.fc2 = nn.Linear(128, 10) 

    def forward(self, x): 
        # 데이터가 통과하는 연산 흐름 정의
        x = self.relu(self.fc1(x)) 
        x = self.fc2(x) 
        return x 
```

* **치명적인 실행 규칙 (Critical Execute Rule):**
  * 항상 모델 인스턴스를 직접 호출할 것 (`outputs = model(inputs)`).
  * 절대 `model.forward(inputs)`를 수동으로 직접 호출하지 말 것. 직접 호출 시 내부 훅(Hook) 및 파라미터 등록 로직이 누락됩니다.

**[EN]**
* **Structure of Custom PyTorch Models:**
  *(See the Python code above)*
* **Critical Execute Rule:**
  * Always invoke the model instance directly (`outputs = model(inputs)`).
  * Never call `model.forward(inputs)` manually. Direct call bypasses internal hooks and parameter registration routines.

---

## 2. Training Loop Sequence & Silent Failures (학습 루프 순서와 소리 없는 실패)

**[KR]**
* **표준 학습 순서 (Standard Training Order):**
  1) `optimizer.zero_grad()`
  2) `outputs = model(inputs)`
  3) `loss = loss_fn(outputs, targets)`
  4) `loss.backward()`
  5) `optimizer.step()`
* **순서 오류 시 발생하는 위험 - 소리 없는 실패 (Risks of Misordering - Silent Failures):**
  * `backward()`와 `step()` 순서 바꿈: 현재 배치가 아닌 이전 배치 기울기로 파라미터를 업데이트합니다.
  * `zero_grad()`를 `backward()` 뒤에 배치: `step()` 실행 전 계산된 기울기가 파기됩니다 (Instantly erases calculated gradients before `step()`).
  * `zero_grad()`를 루프 바깥에 배치: 기울기가 무한 누적되어 미친 듯이 불안정한 파라미터 폭주가 발생합니다 (Gradients accumulate boundlessly, causing massive unstable updates).

**[EN]**
* **Standard Training Order:**
  1) `optimizer.zero_grad()`
  2) `outputs = model(inputs)`
  3) `loss = loss_fn(outputs, targets)`
  4) `loss.backward()`
  5) `optimizer.step()`
* **Risks of Misordering (Silent Failures):**
  * Swapping `backward()` & `step()`: Updates parameters using previous batch gradients.
  * Placing `zero_grad()` after `backward()`: Instantly erases calculated gradients before `step()`.
  * Placing `zero_grad()` outside loop: Gradients accumulate boundlessly, causing massive unstable updates.

---

## 3. Proper Model Evaluation Workflow (올바른 모델 평가 워크플로우)

**[KR]**
* **평가 파이프라인 설정 코드 (Evaluation Pipeline Setup):**

```python
model.eval() # 평가 모드로 전환

with torch.no_grad(): # 기울기 연산 그래프 생성을 차단하여 RAM/VRAM 메모리 절약
    for inputs, targets in test_loader: 
        outputs = model(inputs) 
        # 정확도(Accuracy) 및 평가지표 계산

model.train() # 학습을 계속 진행할 경우 다시 학습 모드로 원복
```

* **평가 지표 - 정확도 (Evaluation Metric - Accuracy):**
  $$ \text{Accuracy} = \frac{\text{Correct Predictions (맞춘 예측수)}}{\text{Total Samples (전체 평가 샘플수)}} $$
  * (예: 10000개 중 9500개 맞춤 = $95\%$ 정확도 / e.g., $9500 / 10000 = 95\%$ accuracy).

**[EN]**
* **Evaluation Pipeline Setup:**
  *(See the Python code above)*
* **Evaluation Metric - Accuracy:**
  $$ \text{Accuracy} = \frac{\text{Correct Predictions}}{\text{Total Samples}} $$
  * (e.g., $9500 / 10000 = 95\%$ accuracy).

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-2 Overview of ML Pipeline with PyTorch Part 2_ Models-1" src="https://github.com/user-attachments/assets/0cd241d7-9028-4d1c-bd31-9ffef4b7957f" />
    <img width="1264" height="1635" alt="2-2 Overview of ML Pipeline with PyTorch Part 2_ Models-2" src="https://github.com/user-attachments/assets/b297f228-723b-4142-bf91-9144a2b7e1a1" />
  </div>
</details>
