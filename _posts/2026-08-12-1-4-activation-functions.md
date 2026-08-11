---
title: "1-4 Activation Functions"
date: 2026-08-12 04:45:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, activation-function, relu, sigmoid, tanh]
math: true
---

## 1. The Problem of Linear Models & Need for Nonlinearity (선형 모델의 한계와 비선형성의 필요성)

**[KR]**
* **실제 데이터의 문제점 (Problem in Real-world Data):**
  * 단거리 (Short distance): 자전거 이동 $\rightarrow$ 선형적 관계 (Linear relation).
  * 중거리 (Medium distance): 도심 교통 체증 $\rightarrow$ 속도 저하 (Slowdown).
  * 장거리 (Long distance): 고속도로 진입 $\rightarrow$ 속도 증가 (Faster speed).
  * **결과 (Result):** 배달 시간 데이터는 직선이 아닌 곡선 형태의 관계를 형성합니다.
* **선형 계층만 쌓았을 때의 문제 (Why Stacking Linear Layers Fails):**
  * 활성화 함수 없이 선형 방정식 여러 개를 결합하면 결국 또 다른 하나의 선형 방정식이 될 뿐입니다.
    $$ y = W_2(W_1x + B_1) + B_2 \quad \Rightarrow \quad y = W'x + B' $$
  * 뉴런을 아무리 많이 더해도 직선만 표현 가능합니다.
* **해결책 (Solution):** 선형 변환 직후, 요소별(Element-wise)로 비선형 활성화 함수(Nonlinear Activation Functions)를 적용합니다.

**[EN]**
* **Problem in Real-world Data:**
  * Short distance: Bike range $\rightarrow$ Linear relation.
  * Medium distance: Dense city traffic $\rightarrow$ Slowdown.
  * Long distance: Highway $\rightarrow$ Faster speed.
  * **Result:** Delivery time forms a curved relationship, not a straight line.
* **Why Stacking Linear Layers Fails:**
  * Combining multiple linear equations always simplifies to another linear equation.
    $$ y = W_2(W_1x + B_1) + B_2 \quad \Rightarrow \quad y = W'x + B' $$
  * Multiple neurons without activation functions still produce a straight line.
* **Solution:** Introduce Nonlinear Activation Functions element-wise after linear transformations.

---

## 2. Understanding ReLU (ReLU 활성화 함수의 이해)

**[KR]**
* **ReLU(Rectified Linear Unit)의 정의 (Definition of ReLU):**
  $$ f(x) = \begin{cases} 0 & \text{if } x < 0 \\ x & \text{if } x \ge 0 \end{cases} $$
* **수학적 직관 (Mathematical Intuition):**
  * 일반적인 직선($Wx + B$)을 특정 지점에서 꺾인 선(bend/corner)으로 변환합니다.
  * **꺾임 위치 (Break Point Location):** $Wx + B = 0$이 되는 지점, 즉 $x = -\frac{B}{W}$에서 발생합니다.
* **복잡한 곡선 만들기 (Building Complex Curves):**
  * 단일 ReLU 뉴런 = 1개의 꺾임점 (1 bend).
  * 여러 개의 ReLU 뉴런 = 서로 다른 위치($x = -B_i/W_i$)에서 꺾이는 여러 선분.
  * 꺾인 선분들을 합치면(Summing) 어떠한 부드러운 연속 곡선도 근사(Approximate)할 수 있습니다.

**[EN]**
* **Definition of ReLU (Rectified Linear Unit):**
  $$ f(x) = \begin{cases} 0 & \text{if } x < 0 \\ x & \text{if } x \ge 0 \end{cases} $$
* **Mathematical Intuition:**
  * Converts a standard linear line ($Wx + B$) into a line with a bend/corner.
  * **Break Point Location:** The bend occurs where $Wx + B = 0$, which is $x = -\frac{B}{W}$.
* **Building Complex Curves:**
  * Single ReLU neuron = 1 bend.
  * Multiple ReLU neurons = Multiple bends at different locations ($x = -B_i/W_i$).
  * Summing multiple bent lines approximates any smooth continuous curve.

---

## 3. PyTorch Implementation & Architecture (PyTorch 코드 및 구조)

**[KR]**
* **PyTorch 코드 예시 (PyTorch Code Example):**

```python
import torch.nn as nn 

model = nn.Sequential( 
    nn.Linear(1, 3), # 1개 입력(거리) -> 은닉층 3개 뉴런
    nn.ReLU(),       # 비선형 활성화 함수 적용
    nn.Linear(3, 1)  # 은닉층 3개 출력 -> 최종 출력 1개(배달 시간)
) 
```

* **Layer 상세 분석 (Layer Breakdown):**
  * `nn.Linear(1, 3)`: 3개의 서로 다른 $Wx + B$ 선형 연산을 수행합니다.
  * `nn.ReLU()`: 3개의 연산 결과 각각에 $\max(0, x)$를 적용합니다.
  * `nn.Linear(3, 1)`: 비선형 변환된 3개의 값을 조합하여 1개의 최종 예측값을 생성합니다.
* **모델 표현력 향상 (Increasing Model Capacity):** 은닉층의 뉴런 수를 늘릴수록 네트워크는 훨씬 더 부드럽고 복잡한 곡선을 정교하게 모델링할 수 있습니다.

**[EN]**
* **PyTorch Code Example:**

```python
import torch.nn as nn 

model = nn.Sequential( 
    nn.Linear(1, 3), # 1 input feature (distance) -> 3 hidden neurons
    nn.ReLU(),       # Apply nonlinear activation function
    nn.Linear(3, 1)  # 3 hidden outputs -> 1 final output (delivery time)
) 
```

* **Layer Breakdown:**
  * `nn.Linear(1, 3)`: Computes 3 separate $Wx + B$ linear outputs.
  * `nn.ReLU()`: Applies $\max(0, x)$ to each of the 3 outputs.
  * `nn.Linear(3, 1)`: Combines the 3 transformed non-linear outputs into 1 final prediction.
* **Increasing Model Capacity:** Increasing hidden neurons allows the network to model smoother, more complex curves.

---

## 4. Alternative Activation Functions (기타 활성화 함수)

**[KR]**
* **기타 주요 활성화 함수 (Other Common Activation Functions):**
  * **Sigmoid (시그모이드):** 출력을 $(0, 1)$ 범위로 압축합니다. 확률 예측 및 이진 분류(Binary classification)에 유용합니다.
  * **Tanh (쌍곡선 탄젠트):** 출력을 $(-1, 1)$ 범위로 압축하며, 중심이 $0$에 위치(Zero-centered)합니다.
* **실무 팁 (Practical Advice):** 대부분의 현대 딥러닝 아키텍처에서는 ReLU를 기본(Default) 시작점이자 핵심(Workhorse) 함수로 사용합니다.

**[EN]**
* **Other Common Activation Functions:**
  * **Sigmoid:** Squashes values into range $(0, 1)$. Ideal for probability estimation/binary classification.
  * **Tanh (Hyperbolic Tangent):** Maps values into range $(-1, 1)$, zero-centered.
* **Practical Advice:** ReLU remains the default starting point (workhorse) for modern deep learning architectures.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-4 Activation Functions-1" src="https://github.com/user-attachments/assets/1824a26a-54a7-46a9-b233-768d906b25aa" />
    <img width="1264" height="1635" alt="1-4 Activation Functions-2" src="https://github.com/user-attachments/assets/f05d8208-cedb-4a42-b8b9-6c287389a10b" />
  </div>
</details>
