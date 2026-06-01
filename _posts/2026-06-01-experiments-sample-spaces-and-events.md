---
title: "2-1 Experiments, Sample Spaces, and Events"
date: 2026-06-01 20:00:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, sample_space, events, experiment, discrete_math]
---

## 1. 실험과 표본 공간 (Experiments & Sample Spaces)

**[KR]** 확률론에서 실험(Experiment)과 그로 인해 발생할 수 있는 모든 결과의 집합인 표본 공간(Sample Space)에 대한 정의입니다.

* **정의:** 특정 실험(E)과 관련된 표본 공간은 해당 실험에서 발생할 수 있는 모든 가능한 결과(Outcomes)들의 집합입니다. 기호로는 주로 S 또는 Ω(오메가)로 표기합니다.
* **표본 공간의 예시:**
  * **동전 1개 던지기:** S = {H, T}
  * **동전 3개 던지기:** S = {HHH, HHT, HTH, HTT, THH, THT, TTH, TTT} 로 나열할 수도 있지만, '앞면(H)의 개수'에 관심이 있다면 S' = {0, 1, 2, 3} 으로 정의할 수도 있습니다. 즉, 하나의 실험에 대한 표본 공간이 반드시 유일(Unique)해야 하는 것은 아닙니다!
  * **10명에게 선호하는 음료(콜라/펩시) 묻기:** S = {0, 1, ..., 10}
  * **전구의 수명 (연속형 데이터):** S = {t &#124; t ≥ 0}

---

## 2. 사건의 정의 (Definition of Events)

**[KR]** 사건(Event)은 표본 공간 내에서 우리가 관심을 가지는 특정한 결과들의 모임입니다.

* **정의:** 사건은 가능한 결과들의 집합이며, 표본 공간 S의 어떠한 부분집합(Subset)도 모두 사건이 될 수 있습니다.
* **예시:** 8면체 주사위(Dungeon and Dragons die)를 던지는 실험을 가정해 봅시다. 표본 공간은 S = {1, 2, ..., 8} 입니다. 만약 사건 A를 "홀수가 나오는 경우"라고 정의한다면, A = {1, 3, 5, 7} 이 됩니다.
* **특이한 사건들:** * 공집합(∅) 또한 사건입니다. 이는 "실험에서 가능한 결과 중 아무것도 관측되지 않음"을 의미합니다.
  * 전체 집합 S 역시 사건입니다. 이는 "표본 공간 내의 무언가가 어쨌든 발생함"을 의미합니다.

---

## 3. 사건의 연산 (Operations on Events)

**[KR]** 이전 챕터에서 배운 집합의 연산 법칙(교집합, 합집합, 여집합 등)을 사건에 동일하게 적용할 수 있습니다.

* **여사건 (Complementary Event):** 사건 A에 대하여, 반대되는 사건을 여사건이라 부르며 Aᶜ (또는 A 윗줄)로 표기합니다. 예를 들어 동전 2개를 던질 때 A = {HH} 라면, 여사건은 Aᶜ = {HT, TH, TT} 가 됩니다.
* **합사건과 곱사건:** 두 사건 A와 B에 대하여 합사건(A ∪ B)과 곱사건(A ∩ B) 역시 유효한 사건이 됩니다.
* **동전 3개 던지기 종합 예시:**
  * A = "뒷면(T)이 정확히 1번 관측됨" = {HHT, HTH, THH}
  * B = "뒷면(T)이 한 번도 관측되지 않음" = {HHH}
  * C = "첫 번째 동전이 앞면(H)임" = {HHH, HHT, HTH, HTT}
  * **A ∪ B** = "뒷면(T)이 많아야 1번 관측됨 (At most one T)" = {HHT, HTH, THH, HHH}
  * **A ∩ C** = "첫 번째가 H이면서 뒷면(T)이 정확히 1번 관측됨" = {HHT, HTH}

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-1 Experiments, Sample Spaces, and Events-1" src="https://github.com/user-attachments/assets/c5883e26-cbaf-42c9-84f9-75f052cd3329" />
    <img width="1264" height="1635" alt="2-1 Experiments, Sample Spaces, and Events-2" src="https://github.com/user-attachments/assets/7307004d-ca4e-4dee-8e88-39489ae4ef7f" />
  </div>
</details>
