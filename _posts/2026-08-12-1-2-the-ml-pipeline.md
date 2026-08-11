---
title: "1-2 The ML Pipeline"
date: 2026-08-12 04:00:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, ml-pipeline, inference]
math: true
---

## 1. Introduction & Inference Concept (소개 및 추론의 개념)

**[KR]**
* **복습 (Recall):** 이전 강의에서 단일 뉴런이 선형 패턴($y = Wx + B$)을 학습하는 과정을 확인했습니다.
* **추론 개념 (Concept - Inference):**
  * **정의:** 학습된 모델을 활용하여, 학습 중 보지 못한 새로운 데이터(Unseen data)에 대해 예측을 수행하는 것입니다.
  * **실습 목표:** 새로운 고객 위치에 대한 배달 시간을 예측합니다.
  * **목표:** 단순 회귀 분석부터 복잡한 이미지 분류까지 모든 PyTorch 프로젝트에 공통으로 적용되는 **표준화된 6단계 ML 프레임워크**를 확립합니다.

**[EN]**
* **Recall:** Previous lesson showed how a single neuron learns linear patterns ($y = Wx + B$).
* **Concept - Inference:**
  * **Definition:** Making predictions on new, unseen data using a trained model.
  * **Goal in Lab:** Predict delivery times for new customer locations.
  * **Objective:** Establish a standardized 6-stage ML framework applicable to all PyTorch projects (from simple regression to complex image classification).

---

## 2. Stage 1 & Stage 2 (1단계 및 2단계)

**[KR]**
* **Stage 1: Data Ingestion (데이터 수집)**
  * PyTorch가 효율적으로 다룰 수 있는 형태로 원시 데이터(Raw information)를 수집 및 정리합니다.
  * 실제 데이터는 매우 무질서합니다(텍스트/숫자 혼용, 결측치, 자전거로 시속 200마일 주행과 같은 불가능한 기록 등).
* **Stage 2: Data Preparation (데이터 전처리)**
  * 모델이 잘 학습할 수 있도록 데이터를 정제, 변환, 구조화합니다.
  * **주요 작업 (Key Tasks):**
    * 중복 및 불가능한 이상치(Outliers) 제거
    * 누락된 결측치(Missing values) 처리
    * 특성 공학(Feature Engineering): 원시 데이터 변환 (예: 주소 $\rightarrow$ 거리(마일))
  * **참고:** 실무 프로젝트에서 가장 많은 시간과 코드가 소요됩니다. 모델의 실패는 수학적 오류보다 지저분한 데이터(Messy data) 때문인 경우가 많습니다.

**[EN]**
* **Stage 1: Data Ingestion**
  * Gather raw information into PyTorch-accessible formats.
  * Real-world data is messy: text vs. numeric formats, missing values, impossible records (e.g., biking at 200 mph).
* **Stage 2: Data Preparation**
  * Clean, transform, and format data for effective learning.
  * **Key Tasks:**
    * Removing duplicates/impossible outliers.
    * Handling missing values.
    * Feature Engineering: Converting raw features (e.g., Address $\rightarrow$ Distance in miles).
  * **Note:** Takes the most time and code in real projects. Models usually fail due to messy data, not bad math.

---

## 3. Stage 3 & Stage 4 (3단계 및 4단계)

**[KR]**
* **Stage 3: Model Building (모델 구축)**
  * 문제에 적합한 모델의 아키텍처(구조)를 설계합니다.
  * **주요 결정 요소:** 뉴런 수, 뉴런 간 연결 방식, 레이어(Layer) 종류.
  * **PyTorch 구현:** 단일 뉴런 모델의 경우 단 한 줄의 코드로 구현 가능합니다.
* **Stage 4: Training (학습)**
  * 입출력 쌍(Training pairs)을 모델에 입력합니다 (예: 8.2마일 $\rightarrow$ 22분).
  * **주요 구성 요소 (Core Components):**
    * 오차 측정 방식 (손실 함수, Loss Function)
    * 파라미터 업데이트 규칙 및 학습률 (Optimization Strategy & Learning Rate)
  * PyTorch가 복잡한 연산을 수행하는 **학습 루프(Training Loop)**를 실행하여 파라미터를 자동으로 최적화합니다.

**[EN]**
* **Stage 3: Model Building**
  * Define the architecture (structure) suitable for the domain.
  * **Key Decisions:** Number of neurons, connection patterns, layer types.
  * **PyTorch Implementation:** Single line of code for a simple single-neuron model.
* **Stage 4: Training**
  * Feed training pairs into the model (e.g., 8.2 miles $\rightarrow$ 22 mins).
  * **Core Components to Configure:**
    * Error measurement (Loss Function).
    * Optimization Strategy & Learning Rate.
  * Execute the training loop where PyTorch updates parameters automatically.

---

## 4. Stage 5 & Stage 6 (5단계 및 6단계)

**[KR]**
* **Stage 5: Evaluation and Debugging (평가 및 디버깅)**
  * 학습 과정에서 분리해 둔 평가 데이터(Test set)를 통해 성능을 검증합니다.
  * 예측 오차 차이(Prediction gap)를 확인합니다 (예: 예측 28분 vs 실제 32분).
  * **핵심 질문:** 모델이 실제 서비스에 신뢰하고 사용할 수 있을 만큼 충분히 정확한가?
* **Stage 6: Deployment (배포)**
  * 학습 완료된 모델을 실무/실제 사용 환경(Production)에 서빙하여 최종 사용자가 이용할 수 있도록 합니다.

**[EN]**
* **Stage 5: Evaluation and Debugging**
  * Assess model performance on unseen Test set (data held back during training).
  * Measure prediction gap (e.g., Predicted: 28 min vs. Actual: 32 min).
  * **Core Question:** Is the model accurate and reliable enough for deployment?
* **Stage 6: Deployment**
  * Serve the trained model in production for end-users.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-2 The ML Pipeline-1" src="https://github.com/user-attachments/assets/5a8835ff-a0b6-4746-aae7-80eb329dcf16" />
    <img width="1264" height="1635" alt="1-2 The ML Pipeline-2" src="https://github.com/user-attachments/assets/40c6bc0c-692e-468b-a6e1-0f597432123f" />
  </div>
</details>
