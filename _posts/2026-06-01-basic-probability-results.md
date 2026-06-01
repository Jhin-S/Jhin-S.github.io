---
title: "2-3 Basic Probability Results"
date: 2026-06-01 21:00:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, inclusion_exclusion, venn_diagram, basic_results]
---

## 1. 여사건과 공집합의 확률 (Complement and Empty Set)

**[KR]** 확률의 기본 공리를 바탕으로 도출되는 유용한 기본 정리들입니다.

* **여사건의 정리:** P(Aᶜ) = 1 - P(A)
  * 어떤 사건이 일어나지 않을 확률은 1에서 그 사건이 일어날 확률을 뺀 것과 같습니다. (예: 내일 비가 올 확률 = 1 - 내일 비가 오지 않을 확률)
* **공집합의 확률:** P(∅) = 0
  * 표본 공간에서 아무런 결과도 관측되지 않을 확률은 0입니다.
* **주의사항 (역은 성립하지 않음):** P(A) = 0이라고 해서 반드시 A = ∅ (불가능한 사건)인 것은 아닙니다. 예를 들어 0과 1 사이에서 무작위로 실수 하나를 뽑을 때, 정확히 특정한 숫자 하나가 뽑힐 확률은 0이지만 아예 불가능한 사건은 아닙니다.

---

## 2. 두 사건의 합집합 확률 (For Two Events)

**[KR]** 두 사건 A와 B에 대한 합집합의 확률을 구하는 공식입니다. 이전에 배운 공리 3(서로소 사건의 덧셈)은 A ∩ B = ∅ 인 경우에 해당하는 이 정리의 특수한 사례입니다.

* **공식:** P(A ∪ B) = P(A) + P(B) - P(A ∩ B)
* **예제 풀이:**
  * 더 추워질 확률 P(C) = 40% (0.4)
  * 비가 오고 더 추워질 확률 P(R ∩ C) = 10% (0.1)
  * 비가 오거나 더 추워질 확률 P(R ∪ C) = 80% (0.8)
  * **비가 올 확률 P(R) 구하기:** P(R) = P(R ∪ C) - P(C) + P(R ∩ C) = 0.8 - 0.4 + 0.1 = **0.5**

---

## 3. 세 사건의 합집합 확률 (For Three Events)

**[KR]** 사건이 세 개(A, B, C)로 늘어날 경우, 벤 다이어그램의 중복 영역을 고려하여 식을 확장할 수 있습니다.

* **공식:** P(A ∪ B ∪ C) = P(A) + P(B) + P(C) - P(A ∩ B) - P(B ∩ C) - P(C ∩ A) + P(A ∩ B ∩ C)
* **실생활 예제 (애틀랜타 주민들의 취미):**
  * 조깅(J): 75%, 아이스크림(I): 20%, 음악(M): 40%
  * 교집합: J ∩ I = 15%, J ∩ M = 30%, I ∩ M = 10%
  * 세 가지 모두: J ∩ I ∩ M = 5%
  * **적어도 하나의 활동을 할 확률 P(J ∪ I ∪ M):** 0.75 + 0.20 + 0.40 - 0.15 - 0.30 - 0.10 + 0.05 = **0.85**
* **정확히 한 가지 활동만 할 확률:** 벤 다이어그램을 그려 안쪽에서부터 바깥으로 채워나가면 쉽게 구할 수 있습니다.
  * P(오직 J만) + P(오직 I만) + P(오직 M만) = 0.35 + 0.00 + 0.05 = **0.40**

---

## 4. 포함-배제의 원리 (Principle of Inclusion-Exclusion)

**[KR]** 합집합의 확률을 구하는 일반적인 수학적 원리입니다.

사건이 n개로 늘어났을 때 합집합의 확률 P(A₁ ∪ A₂ ∪ ... ∪ Aₙ)은 다음의 규칙을 따릅니다.
1. 모든 **단일 사건**의 확률을 더합니다.
2. 모든 **이중 교집합**의 확률을 뺍니다.
3. 모든 **삼중 교집합**의 확률을 다시 더합니다.
4. 이 과정을 n중 교집합까지 더하기(+)와 빼기(-)를 번갈아가며(Alternating) 반복합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-3 Basic Probability Results-1" src="https://github.com/user-attachments/assets/755bb184-5a53-42a1-8d47-e4eb2ad3dade" />
    <img width="1264" height="1635" alt="2-3 Basic Probability Results-2" src="https://github.com/user-attachments/assets/425f6541-30cf-4db0-85af-d3170aa05496" />
    <img width="1264" height="1635" alt="2-3 Basic Probability Results-3" src="https://github.com/user-attachments/assets/740e434e-43e7-4110-9858-de07088edee0" />
    <img width="1264" height="1635" alt="2-3 Basic Probability Results-4" src="https://github.com/user-attachments/assets/f3beff9d-33da-43cf-994f-d3235fdcdb44" />
    <img width="1264" height="1635" alt="2-3 Basic Probability Results-5" src="https://github.com/user-attachments/assets/52d02a43-0592-416d-8f4a-5f36352c3363" />
  </div>
</details>
