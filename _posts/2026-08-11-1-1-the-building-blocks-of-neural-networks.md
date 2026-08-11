---
title: "1-1 The Building Blocks of Neural Networks"
date: 2026-08-11 20:10:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, neural-networks, linear-equation]
math: true
---

## 1. Problem Definition & Intuition (문제 정의 및 직관)

**[KR]** 
* **문제 상황 (Problem Scenario):** 30분 이내에 배달을 완료하는 것이 목표입니다. 현재 들어온 주문은 7마일 떨어진 지역에 있습니다.
* **질문:** 과연 30분 안에 도착할 수 있을까요?
* **핵심 통찰 (Core Insight):** 신경망(Neural Networks)은 과거 데이터를 활용하여 이러한 예측 문제를 해결합니다. 단일 뉴런(Single Neuron)은 딥러닝의 가장 기본적인 구성 요소입니다. 여기서 뉴런은 생물학적 개념이 아니라, 조정 가능한 파라미터를 가진 수학적 단위입니다.

**[EN]** 
* **Problem Scenario:** The goal is to deliver orders within 30 minutes. The current order is 7 miles away.
* **Question:** Can we deliver in under 30 minutes?
* **Core Insight:** Neural networks solve prediction problems using historical data. A single neuron is the foundational building block of deep learning. Neurons are not biology - they are mathematical units with adjustable parameters.

---

## 2. Single Neuron as a Linear Equation (선형방정식으로서의 뉴런)

**[KR]** 
* **데이터 패턴 (Data Pattern):** 
  * 5마일 $\rightarrow$ 22.2분 소요
  * 6마일 $\rightarrow$ 25.6분 소요
* 관측된 점들이 직선적인 형태를 따릅니다. 따라서 가장 적합한 예측 모델은 **선형방정식(Linear Equation)**입니다.
* **예측 수식:** 
  $$ \text{Prediction} = (\text{Weight} \times \text{Input}) + \text{Bias} $$
  $$ y = W \cdot x + B $$
* **머신러닝의 목표 (Goal of Machine Learning):** 데이터를 가장 잘 설명하는 최적의 가중치($W$, Weight)와 편향($B$, Bias) 값을 찾는 것입니다.

**[EN]** 
* **Data Pattern:** 
  * 5 miles $\rightarrow$ 22.2 min
  * 6 miles $\rightarrow$ 25.6 min
* The points follow a straight line. The best predictive model is a **Linear Equation**.
* **Prediction Formula:**
  $$ \text{Prediction} = (\text{Weight} \times \text{Input}) + \text{Bias} $$
  $$ y = W \cdot x + B $$
* **Goal of Machine Learning:** Find the optimal values for $W$ (Weight) and $B$ (Bias) to fit the data best.

---

## 3. How the Neuron Learns (뉴런의 학습 방식)

**[KR]** 
* **초기 추정 - 무작위 시작 (Initial Guess):** 
  $W = 1$, $B = 10$으로 설정해 봅니다.
  $$ (1 \times 5) + 10 = 15 \text{분} $$
  (실제 걸린 시간은 22.2분이므로, 오차는 $7.2$분 발생합니다.)
* **수정된 시도 (Refined Trial):** 
  $W = 3.4$, $B = 5$로 설정해 봅니다.
  $$ (3.4 \times 5) + 5 = 22 \text{분} $$
  (오차가 $0.2$분으로 줄어들어 훨씬 잘 맞습니다!)
* **PyTorch를 통한 자동화된 학습 (Automated Learning via PyTorch):**
  1. 무작위 파라미터($W$, $B$)로 시작합니다.
  2. 전체 예측 오차를 측정합니다.
  3. 미분(Calculus, Derivatives)을 사용하여 파라미터를 늘릴지 줄일지 조정 방향을 결정합니다.
  4. 보폭을 작게 이동 $\rightarrow$ 오차 재측정 $\rightarrow$ 미세 조정의 과정을 수백에서 수천 번 반복(Repeats)합니다.

**[EN]** 
* **Initial Guess (Random Start):** 
  Try $W = 1$, $B = 10$:
  $$ (1 \times 5) + 10 = 15 \text{ min} $$
  (Actual was 22.2 min $\rightarrow$ Error is $7.2$ min.)
* **Refined Trial:** 
  Try $W = 3.4$, $B = 5$:
  $$ (3.4 \times 5) + 5 = 22 \text{ min} $$
  (Error = $0.2$ min, much better!)
* **Automated Learning via PyTorch:**
  1. Starts with random parameters ($W$, $B$).
  2. Measures total prediction error.
  3. Uses calculus (derivatives) to determine adjustment direction.
  4. Takes small steps $\rightarrow$ Measures error $\rightarrow$ Adjusts $\rightarrow$ Repeats hundreds/thousands of times.

---

## 4. Expanding to Multiple Inputs & Deep Networks (다중 입력 및 심층 신경망으로의 확장)

**[KR]** 
* **다중 입력으로의 확장 (Multiple Inputs Extension):**
  * 단일 입력: 거리 ($x$)
  * 다중 입력: 거리 ($x_1$), 시간대 ($x_2$), 날씨 ($x_3$)
  * 입력이 늘어나도 선형 구조는 그대로 유지됩니다.
    $$ y = (W_1 \cdot x_1) + (W_2 \cdot x_2) + (W_3 \cdot x_3) + B $$
* **신경망 구조 (Network Architecture):**
  * **레이어 (Layer):** 동일한 입력을 동시에 처리하는 뉴런들의 집합입니다.
  * **입력층 (Input Layer):** 원시 데이터 특징(거리, 날씨 등)을 입력받습니다.
  * **은닉층 (Hidden Layers):** 입력층과 출력층 사이에 존재하며, 내부 값을 직접 설정하거나 직접 볼 수 없는 층입니다.
  * **출력층 (Output Layer):** 최종 예측값을 출력합니다 (예: 배달 소요 시간).

**[EN]** 
* **Multiple Inputs Extension:**
  * Single input: Distance ($x$)
  * Multiple Inputs: Distance ($x_1$), Time of day ($x_2$), Weather ($x_3$)
  * The formula remains linear even with multiple inputs:
    $$ y = (W_1 \cdot x_1) + (W_2 \cdot x_2) + (W_3 \cdot x_3) + B $$
* **Network Architecture:**
  * **Layer:** A group of neurons processing the same inputs simultaneously.
  * **Input Layer:** Receives raw features (distance, weather, etc.).
  * **Hidden Layers:** Layers between input and output whose values are not directly set/observed.
  * **Output Layer:** Returns the final prediction (e.g., delivery time).

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1 The Building Blocks of Neural Networks-1" src="https://github.com/user-attachments/assets/0c85870c-d0e9-4591-8354-ad2d5454c1a9" />
    <img width="1264" height="1635" alt="1-1 The Building Blocks of Neural Networks-2" src="https://github.com/user-attachments/assets/6c51a05d-c77e-4a71-a328-3cd939e0546a" />
  </div>
</details>
