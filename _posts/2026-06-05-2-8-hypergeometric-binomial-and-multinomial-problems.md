---
title: "2-8 Hypergeometric, Binomial and Multinomial Problems"
date: 2026-06-05 14:06:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, hypergeometric, binomial, multinomial, combination]
---

## 1. 초기하 분포 (Hypergeometric Distribution)

**[KR]** 주머니 안에 두 가지 종류의 대상(예: 빨간 공 $a$개, 파란 공 $b$개)이 있을 때, **비복원 추출(Without Replacement)**로 $n$개를 뽑는 상황을 모델링합니다. 뽑은 공들 중에서 첫 번째 종류의 대상이 정확히 $k$개 포함될 확률을 구하는 것이며, 이때의 확률 분포를 초기하 분포라고 합니다.

**[EN]** Suppose you have two types of objects (e.g., $a$ red balls and $b$ blue balls) in a box. The hypergeometric distribution models the probability of selecting exactly $k$ objects of the first type when drawing $n$ objects **without replacement**.

$$P(X = k) = \frac{\binom{a}{k}\binom{b}{n-k}}{\binom{a+b}{n}}$$

* **Example:** 주머니에 빨간 공 15개, 파란 공 10개가 있을 때 비복원 추출로 7개를 뽑아 정확히 3개의 빨간 공이 나올 확률 (25 Sox in a box. 15 red, 10 blue. Pick 7 without replacement.)
  $$P(k=3) = \frac{\binom{15}{3}\binom{10}{4}}{\binom{25}{7}} \approx 0.1988$$

---

## 2. 이항 분포 (Binomial Distribution)

**[KR]** 초기하 분포와 유사하지만, 가장 큰 차이점은 **복원 추출(With Replacement)**을 한다는 것입니다. 매번 공을 뽑을 때마다 다시 집어넣으므로 각 시행이 독립적이며, 뽑힐 확률이 일정하게 유지됩니다.

**[EN]** This is similar to the hypergeometric distribution, but the key difference is that objects are drawn **with replacement**. This ensures that each draw is an independent event, and the probability of success remains constant across all trials.

$$P(X = k) = \binom{n}{k} \left(\frac{a}{a+b}\right)^k \left(\frac{b}{a+b}\right)^{n-k}$$

* **Example:** 주머니에 빨간 공 15개, 파란 공 10개가 있을 때 복원 추출로 7번을 뽑아 정확히 3번 빨간 공이 나올 확률 (25 Sox in a box. 15 red, 10 blue. Pick 7 with replacement.)
  $$P(k=3) = \binom{7}{3} \left(\frac{15}{25}\right)^3 \left(\frac{10}{25}\right)^{7-3} \approx 0.1936$$

---

## 3. 중복 조합 (Combinations with Replacement)

**[KR]** 서로 다른 $n$개의 종류 중에서 중복을 허용하여 $r$개를 선택하는 경우의 수입니다. 이를 직관적으로 이해하기 위해 **칸막이 모델(Stones and Bars)**을 주로 사용합니다. 예를 들어 3가지 맛의 아이스크림 중 4스쿱을 고르는 경우, 4개의 공(스쿱)과 2개의 칸막이를 나열하는 조합의 수와 완벽하게 일치합니다. (동차, Homogeneous의 앞 글자를 따서 $H$ 기호를 사용합니다.)

**[EN]** The number of ways to choose $r$ items from $n$ distinct categories, where repetition is allowed. This is often visualized using the **Stones and Bars (or Stars and Bars)** model. For instance, choosing 4 scoops of ice cream from 3 available flavors is mathematically equivalent to arranging 4 stones (scoops) and 2 bars (dividers). 

$$_n H_r = _{n+r-1} C_r$$

* **Formula Derivation:** 서로 다른 $n$종류를 구분하기 위해 필요한 칸막이의 수는 $n-1$개입니다. 선택할 개수 $r$개와 칸막이 수 $n-1$개를 합친 총 자릿수에서 칸막이(또는 대상)의 위치를 고르는 조합의 수로 계산됩니다.

---

## 4. 다항 계수 (Multinomial Coefficients)

**[KR]** 이항(Binomial)이 두 가지 선택지만 다루었다면, 다항(Multinomial)은 세 가지 이상의 선택지가 있는 상황으로 일반화한 것입니다. 같은 것이 포함된 대상을 일렬로 나열할 때 사용됩니다. 먼저 모든 대상을 다르다고 가정하고 나열한 뒤(분자), 중복되는 대상들끼리 자리를 바꾸는 경우의 수(분모)로 나누어 구합니다.

**[EN]** While binomial deals with two outcomes, multinomial generalizes this to $k$ different types of outcomes. It is used to calculate the number of unique permutations of a set containing duplicate items. You calculate the total permutations assuming all items are unique, and then divide by the permutations of the identical items.

$$\binom{n}{n_1, n_2, \dots, n_k} = \frac{n!}{n_1! n_2! \dots n_k!}$$

* **Example:** 3개의 사과, 2개의 바나나, 1개의 오렌지 총 6개의 과일을 일렬로 줄 세우는 방법의 수 (How many ways to arrange 3 apples, 2 bananas, and 1 orange?)
  $$\frac{6!}{3! 2! 1!} = 60$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-1" src="https://github.com/user-attachments/assets/642b70c0-c477-4f36-ab3f-614aa766e221" />
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-2" src="https://github.com/user-attachments/assets/fafc77fa-c0f2-4f27-ba92-ce19ea5906ca" />
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-3" src="https://github.com/user-attachments/assets/7cdf9b38-586f-4a3d-8801-5b39512c5f1d" />
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-4" src="https://github.com/user-attachments/assets/5699de80-4ede-4513-a916-595886172092" />
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-5" src="https://github.com/user-attachments/assets/0cd37e29-f87e-4ce8-9e27-68810c1ca9f2" />
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-6" src="https://github.com/user-attachments/assets/2e15197d-532e-4c9e-9e8c-a673cc155aeb" />
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-7" src="https://github.com/user-attachments/assets/58d511a5-1ca8-4309-ad7a-0b07947714a7" />
    <img width="1264" height="1635" alt="2-8 Hypergeometric, Binomial and Multinomial Problems-8" src="https://github.com/user-attachments/assets/f897417b-676c-49dc-935b-23de09cbb4ae" />
  </div>
</details>
