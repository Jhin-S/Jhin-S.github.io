---
title: "2-2 What is Probability"
date: 2026-06-01 20:30:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, axioms, frequentist, sample_space, disjoint_events]
---

## 1. 확률의 직관적 의미와 빈도주의 관점 (Intuitive & Frequentist View)

**[KR]** 표본 공간 S에 속하는 어떤 사건 A가 발생할 확률을 P(A)라고 표기합니다.

* **직관적 확률:** 공정한 동전을 던지는 실험(S = {H, T})에서 앞면(H)이 나올 확률은 직관적으로 P({H}) = P(H) = 1/2 입니다.
* **빈도주의 관점 (Frequentist view):** 이 실험을 아주 여러 번(n번) 반복했을 때, 전체 던진 횟수(n) 중 앞면(H)이 관측된 횟수의 비율이 대략 1/2에 근접한다는 것을 의미합니다. 즉, (총 H가 나온 횟수) / n ≈ 1/2 이 성립합니다.
* **주사위 예시:** 공정한 주사위를 던지는 실험(S = {1, 2, 3, 4, 5, 6})에서는 각 개별 결과의 확률이 1/6입니다. 따라서 1 또는 2가 나올 확률 P(1 or 2)는 1/3이 됩니다.

---

## 2. 확률의 형식적 정의와 4가지 공리 (Axioms of Probability)

**[KR]** 보다 엄밀한 수학적 정의에 따르면, 일반적인 사건 A (A ⊆ S)의 확률은 다음의 4가지 공리(Axioms)를 반드시 만족하는 함수여야 합니다.

* **공리 1:** 0 ≤ P(A) ≤ 1 (확률은 항상 0과 1 사이의 값을 가집니다.)
* **공리 2:** P(S) = 1 (표본 공간 전체의 확률, 즉 어떤 결과든 하나가 발생할 확률은 항상 1입니다. 예: 주사위에서 P(1, 2, 3, 4, 5, 6) = 1)
* **공리 3:** A와 B가 서로소인 사건(Disjoint events, 즉 A ∩ B = ∅)일 때, **P(A ∪ B) = P(A) + P(B)** 가 성립합니다. (예: P(1 or 2) = P(1) + P(2) = 1/6 + 1/6 = 1/3)
* **공리 4:** A₁, A₂, ... 가 서로소인 사건들의 무한 수열(Sequence of disjoint events, 즉 서로 다른 i, j에 대해 Aᵢ ∩ Aⱼ = ∅)이라고 가정할 때, 이들의 무한 합집합의 확률은 각각의 확률을 무한대까지 더한 것과 같습니다. 즉, **P( ∪(i=1 부터 ∞) Aᵢ ) = Σ(i=1 부터 ∞) P(Aᵢ)**

---

## 3. 무한 표본 공간에서의 공리 적용 (Application to Infinite Sample Space)

**[KR]** 첫 번째 앞면(H)이 나올 때까지 동전을 계속 던지는 실험을 생각해 봅시다.

* 표본 공간은 **S = {H, TH, TTH, TTTH, ...}** 로 무한하게 이어집니다.
* 각 결과를 서로소인 사건들로 분리하여 정의합니다 (A₁ = {H}, A₂ = {TH}, A₃ = {TTH} ...).
* 앞서 배운 공리 2와 공리 4를 적용하여 이를 수식으로 전개하면, 전체 표본 공간의 확률이 1이 됨을 수학적으로 증명할 수 있습니다. (**1 = P(S) = P( ∪(i=1 부터 ∞) Aᵢ ) = Σ(i=1 부터 ∞) P(Aᵢ) = Σ(i=1 부터 ∞) 1 / 2ⁱ**)

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-2 What is Probability-1" src="https://github.com/user-attachments/assets/2b380a65-12de-4f33-9179-a4484bbe4c3c" />
    <img width="1264" height="1635" alt="2-2 What is Probability-2" src="https://github.com/user-attachments/assets/c9536ed5-930b-4580-92bf-f91723ac237f" />
    <img width="1264" height="1635" alt="2-2 What is Probability-3" src="https://github.com/user-attachments/assets/69b2d3b7-0b4e-4b1b-a497-13f5f7f7f364" />
  </div>
</details>
