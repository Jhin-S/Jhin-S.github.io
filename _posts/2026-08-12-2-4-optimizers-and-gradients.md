---
title: "2-4 Optimizers and Gradients"
date: 2026-08-12 05:21:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, optimizer, gradient-descent, adam, sgd, backward]
math: true
---

## 1. The Diagnostic Role of `loss.backward()` (`loss.backward()`의 진단 역할)

**[KR]**
* **흔한 오해와 실제 작동 (Misconception vs Reality):**
  * **오해 (Misconception):** `backward()`가 모델의 가중치를 직접 업데이트한다고 생각합니다.
  * **실제 (Reality):** `backward()`는 오직 기울기(Gradient, 진단 점수)만 계산/진단하며, 실제 가중치 업데이트는 `optimizer.step()`이 수행합니다.
* **파라미터 규모 예시 (Parameter Scale Example):**
  * 입력(784) $\rightarrow$ 은닉(128) $\rightarrow$ 출력(10) 구조의 소형 신경망도 101,770개의 학습 가능 파라미터(trainable parameters)를 가집니다.
  * `loss.backward()`는 미분(자동 미분 엔진, Auto-Differentiation)을 통해 이 10만여 개 파라미터의 오차 기여도를 동시에 계산합니다.

**[EN]**
* **Misconception vs Reality:**
  * **Misconception:** `backward()` updates the model's weight.
  * **Reality:** `backward()` only calculates gradients (diagnostic scores). Actual weight updates are performed by `optimizer.step()`.
* **Parameter Scale Example:**
  * Input (784) $\rightarrow$ Hidden (128) $\rightarrow$ Output (10) network has 101,770 trainable parameters.
  * `loss.backward()` evaluates all 101,770 parameters simultaneously using Calculus (Auto-Differentiation).

---

## 2. Gradient Descent & Optimizers: SGD vs Adam (경사하강법 및 최적화 알고리즘)

**[KR]**
* **비유 (Analogy):** 언덕(손실 값) 위에서 계곡 바닥(손실 최소화 지점)을 향해 내려가는 과정과 같습니다.
* **SGD (Stochastic Gradient Descent, 확률적 경사하강법):**
  * **규칙 (Rule):** $\text{Weight}_{\text{new}} = \text{Weight}_{\text{old}} - (\text{Learning Rate} \times \text{Gradient})$
* **학습률(Learning Rate, $lr$)의 영향 (Impact of Learning Rate):**
  * **너무 작을 때 (Small $lr$):** 수렴하는 데 시간이 매우 오래 걸립니다 (Takes too long to converge).
  * **너무 클 때 (Large $lr$):** 최저점을 지나쳐 왔다 갔다 하며 발산합니다 (Bounces back and forth, overshooting the minimum).
* **Adam 최적화 알고리즘 (Adam Optimizer):**
  * 각 파라미터별로 학습률을 개별 적용/조정합니다 (Adaptive learning rates for each parameter individually).
  * 신뢰성이 높고 빨라 현대 딥러닝에서 가장 선호되는 기본 알고리즘입니다.
  * **경고 (Warning):** SGD에서 쓰던 학습률을 Adam에 그대로 복사해서 쓰지 말 것 (손실 폭발 원인이 됩니다 / can cause loss explosion).

**[EN]**
* **Analogy:** Standing on a hillside trying to reach the bottom of a valley (minimizing loss).
* **SGD (Stochastic Gradient Descent):**
  * **Rule:** $\text{Weight}_{\text{new}} = \text{Weight}_{\text{old}} - (\text{Learning Rate} \times \text{Gradient})$
* **Impact of Learning Rate ($lr$):**
  * **Small $lr$:** Takes too long to converge.
  * **Large $lr$:** Bounces back and forth, overshooting the minimum.
* **Adam Optimizer:**
  * Adaptive learning rates for each parameter individually.
  * Reliable, fast, and default first choice in modern deep learning.
  * **Warning:** Do not use SGD learning rate values for Adam directly (can cause loss explosion).

---

## 3. Why `optimizer.zero_grad()` is Critical (`zero_grad()`가 필수인 이유)

**[KR]**
* **PyTorch의 기본 작동 방식 (PyTorch Default Behavior):**
  * 파이토치는 `backward()`가 호출될 때마다 기존 기울기 값에 새 기울기 값을 누적(합산)합니다.
* **기울기를 초기화해야 하는 이유 (Why Clear Gradients):**
  * `zero_grad()`가 없으면 이전 배치의 기울기가 현재 배치에 합쳐져 가중치 업데이트가 비정상적으로 커지고 불안정해집니다 (massive, unstable updates).
* **기본적으로 누적되도록 설계된 이유 (Why does PyTorch accumulate by default?):**
  * GPU 메모리가 부족할 때 가상으로 큰 배치 크기를 구현하는 '기울기 누적(Gradient Accumulation)' 같은 고급 기법에 활용하기 위함입니다.

**[EN]**
* **PyTorch Default Behavior:**
  * PyTorch accumulates (adds) gradients across multiple `backward()` calls by default.
* **Why Clear Gradients:**
  * Without `zero_grad()`, gradients from previous batches stack onto current batches, leading to massive, unstable updates.
* **Why does PyTorch accumulate by default?:**
  * Advanced techniques like Gradient Accumulation (simulating larger batch sizes when GPU memory is limited) rely on this behavior.

---

## 4. Summary of the Complete Training Loop (학습 루프 전체 요약)

**[KR]**
* **흐름:** 손실 함수 (측정) $\rightarrow$ 역전파 (진단) $\rightarrow$ 최적화 단계 (수정)
  1. `optimizer.zero_grad()`: 기존 진단 점수(기울기)를 초기화합니다 (Clears accumulated diagnostic scores).
  2. `outputs = model(inputs)`: 순전파 예측을 수행합니다 (Computes forward pass predictions).
  3. `loss = loss_fn(outputs, targets)`: 예측 오차를 측정합니다 (Measures overall prediction error).
  4. `loss.backward()`: 파라미터 기울기를 진단합니다 (Diagnoses parameter gradients).
  5. `optimizer.step()`: 계산된 기울기를 바탕으로 가중치를 수정합니다 (Updates model weights based on computed gradients).

**[EN]**
* **Flow:** Loss Function (Measure) $\rightarrow$ Backward (Diagnose) $\rightarrow$ Optimizer Step (Update)
  1. `optimizer.zero_grad()`: Clears accumulated diagnostic scores.
  2. `outputs = model(inputs)`: Computes forward pass predictions.
  3. `loss = loss_fn(outputs, targets)`: Measures overall prediction error.
  4. `loss.backward()`: Diagnoses parameter gradients.
  5. `optimizer.step()`: Updates model weights based on computed gradients.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-4 Optimizers and Gradients-1" src="https://github.com/user-attachments/assets/833737b5-1b61-4628-9c8e-b969b39b0f7b" />
    <img width="1264" height="1635" alt="2-4 Optimizers and Gradients-2" src="https://github.com/user-attachments/assets/0d9506a2-aaba-4c12-aec6-9bd8cb07d456" />
  </div>
</details>
