---
title: "2-4 Finite Sample Spaces"
date: 2026-06-01 21:40:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, finite_sample_space, simple_sample_space, equally_likely]
---

## 1. 유한 표본 공간 (Finite Sample Spaces)

**[KR]** 표본 공간 내의 결과(Outcomes)가 유한한 개수로 이루어져 있을 때, 우리는 이를 유한 표본 공간이라고 부릅니다. 유한 표본 공간을 활용하면 특정 사건의 확률을 훨씬 효율적으로 계산할 수 있습니다.

* **기본 원리:** 유한 표본 공간 S = {s₁, s₂, ..., sₙ} 안의 어떤 사건 A가 발생할 확률 P(A)는, 사건 A에 포함된 각각의 개별 결과(sᵢ)들이 발생할 확률을 모두 더한 것과 같습니다.
  * **수식:** P(A) = Σ (sᵢ ∈ A) P(sᵢ)
* **예제:** 빨간색 카드 2장, 파란색 카드 1장, 노란색 카드 1장 중에서 무작위로 1장을 뽑는 실험을 생각해 봅시다. ("무작위"란 각 카드가 뽑힐 확률이 동일함을 의미합니다.)
  * 이 실험에서 "빨간색 카드 또는 노란색 카드를 뽑을 확률"을 구한다면, 해당 사건에 속하는 카드들의 확률을 더하여 2/4 + 1/4 = **3/4** 가 됩니다.

---

## 2. 단순 표본 공간 (Simple Sample Space, SSS)

**[KR]** 단순 표본 공간은 유한 표본 공간 중에서도 **"모든 결과(Outcomes)가 발생할 확률이 동일한(Equally likely)"** 특수한 경우를 의미합니다.

* **예제 (동전 2개 던지기):**
  * 표본 공간을 **S = {HH, HT, TH, TT}** 로 잡는다면, 각각의 결과가 나올 확률이 모두 1/4로 동일하므로 이는 **단순 표본 공간(SSS)**입니다.
  * 반면, 표본 공간을 앞면(H)의 개수를 기준으로 잡아 **S' = {0, 1, 2}** 로 정의한다면 어떻게 될까요? 앞면이 1개 나올 확률(HT, TH)은 2/4이고, 나머지는 각각 1/4이므로 모든 결과의 확률이 같지 않습니다. 따라서 이는 단순 표본 공간이 아닙니다.

---

## 3. 단순 표본 공간에서의 확률 계산 정리 (Theorem)

**[KR]** 단순 표본 공간(SSS)에서는 각각의 결과가 나올 확률이 모두 같기 때문에, 확률 계산이 단순한 '개수 세기' 문제로 바뀝니다.

* **공식:** 단순 표본 공간 S 내의 임의의 사건 A에 대하여, 확률은 다음과 같이 계산됩니다.
  * **P(A) = &#124;A&#124; / &#124;S&#124; = (사건 A에 포함된 원소의 수) / (전체 표본 공간 S의 원소의 수)**
* **예제 1 (주사위 1개):** 공정한 주사위 1개를 던질 때, 사건 A = {1, 2, 4, 6}이 발생할 확률은?
  * 전체 경우의 수는 6가지이고, 사건 A의 개수는 4개이므로 P(A) = **4/6** 입니다.
* **예제 2 (주사위 2개):** 공정한 주사위 2개를 굴릴 때, 나올 수 있는 모든 조합의 수는 36가지이며 각각의 확률은 1/36로 동일한 단순 표본 공간입니다.
  * 이때 두 눈의 합이 4가 되는 사건을 찾아보면 {(1, 3), (2, 2), (3, 1)} 으로 총 3가지입니다.
  * 따라서 두 주사위 눈의 합이 4일 확률은 **3/36** 이 됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-4 Finite Sample Spaces-1" src="https://github.com/user-attachments/assets/7d91b0b0-ab45-41cc-b9e3-1aa86efa8b7b" />
    <img width="1264" height="1635" alt="2-4 Finite Sample Spaces-2" src="https://github.com/user-attachments/assets/9bdd1c18-c19e-4cc6-af58-cba9a59b4361" />
  </div>
</details>
