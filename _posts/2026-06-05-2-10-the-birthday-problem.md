---
title: "2-10 The Birthday Problem"
date: 2026-06-05 14:40:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, birthday-problem, paradox, combinations]
math: true
---

## 1. 문제 소개 (Problem Statement)

**[KR]** 방 안에 $n$명의 사람이 있다고 가정해 봅시다. 이 중 **적어도 두 명의 생일이 같을 확률**은 얼마일까요? (단, 2월 29일 윤달은 무시하며 1년 365일 모든 날짜에 생일이 태어날 확률은 동일하다고 가정합니다.)

**[EN]** There are $n$ people in a room. Find the probability that **at least two have the same birthday**. (Ignore Feb. 29, and assume that all 365 days have equal probability.)

---

## 2. 확률 계산 (Probability Calculation)

**[KR]** '적어도 두 명이 생일이 같을 확률'을 직접 구하는 것보다, **'모든 사람의 생일이 다를 확률'을 구한 뒤 전체 확률(1)에서 빼는 여사건(Complement) 방식**을 사용하는 것이 훨씬 쉽습니다.

**[EN]** Instead of calculating "at least two have the same birthday" directly, it is much easier to use the complement: calculate the probability that **"all birthdays are different"** and subtract it from 1.

### ① 표본 공간 (Sample Space, $S$)
각각의 사람($n$명)이 365일 중 하루를 생일로 가질 수 있으므로, 전체 경우의 수는 다음과 같습니다.

$$
|S| = 365^n
$$

### ② 사건 $A$: 모든 사람의 생일이 다른 경우 (All birthdays are different)
첫 번째 사람은 365일 중 아무 날이나 생일이 될 수 있고, 두 번째 사람은 첫 번째 사람의 생일을 제외한 364일, 세 번째 사람은 363일... 이런 식으로 계산되는 순열($P$)입니다.

$$
|A| = P_{365, n} = 365 \times 364 \times 363 \times \dots \times (365 - n + 1)
$$

### ③ 생일이 겹치지 않을 확률 $P(A)$
전체 경우의 수로 나누어 확률을 구하면 다음과 같습니다.

$$
P(A) = \frac{365 \times 364 \times \dots \times (365 - n + 1)}{365^n} = 1 \cdot \frac{364}{365} \cdot \frac{363}{365} \dots \frac{365 - n + 1}{365}
$$

### ④ 우리가 구하고자 하는 확률 $P(\bar{A})$ (적어도 두 명이 생일이 같을 확률)
전체에서 $A$가 일어날 확률을 뺍니다.

$$
P(\bar{A}) = 1 - P(A) = 1 - \left( 1 \cdot \frac{364}{365} \cdot \frac{363}{365} \dots \frac{365 - n + 1}{365} \right)
$$

---

## 3. 흥미로운 사실 (Interesting Facts & Notes)

이 문제는 우리의 직관과 실제 확률의 차이를 보여주기 때문에 종종 **'생일 역설(Birthday Paradox)'**이라고도 불립니다.

* **$n = 366$ 일 때:** 비둘기집 원리(Pigeonhole Principle)에 의해 최소한 두 명은 무조건 생일이 겹치게 됩니다. 따라서 $P(\bar{A}) = 1$ (100%)이 됩니다.
* **$n = 23$ 일 때:** 놀랍게도 방 안에 고작 23명만 있어도 생일이 겹칠 확률은 절반($P(\bar{A}) > 0.5$)을 넘습니다. (A bit surprising!)
* **$n = 50$ 일 때:** 사람이 50명이 모이면, 생일이 겹칠 확률은 약 $P(\bar{A}) \approx 0.97$ (97%)에 달하게 됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-10 The Birthday Problem-1" src="https://github.com/user-attachments/assets/82ef29a7-d7db-485c-86e5-26d37a01bb52" />
  </div>
</details>
