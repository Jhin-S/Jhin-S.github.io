---
title: "1-3 Geometric and Negative Binomial Distributions"
date: 2026-07-12 14:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, geometric-distribution, negative-binomial, memoryless-property]
math: true
---

## 1. 기하 분포 (Geometric Distribution)

**[KR]** 기하 분포(Geometric Distribution)는 무한히 반복되는 베르누이 시행 속에서 '처음으로 성공'할 때까지 걸린 총 시도 횟수를 나타내는 이산 확률 분포입니다. 매번 성공할 확률을 $p$, 실패할 확률을 $q = 1-p$로 정의해 봅시다. 만약 $k$번째 시도에서 비로소 첫 성공을 거두었다면, 앞선 $k-1$번은 연달아 실패했다는 뜻이 됩니다. 따라서 확률 질량 함수(pmf)는 다음과 같은 형태를 띠게 됩니다.

**[EN]** The geometric distribution is a discrete probability distribution representing the total number of trials needed to achieve the 'first success' in an infinite sequence of independent Bernoulli trials. Let $p$ be the success probability and $q = 1-p$ be the failure probability. If the first success occurs exactly on the $k$-th trial, it inherently means that the preceding $k-1$ trials were consecutive failures. Thus, the probability mass function is formulated as follows.

$$
P(X = k) = q^{k-1}p \quad (k = 1, 2, 3, \dots)
$$

* **기댓값 (Mean):** $E[X] = \frac{1}{p}$
* **분산 (Variance):** $Var(X) = \frac{q}{p^2}$
* **적률 생성 함수 (MGF):** $M_X(t) = \frac{pe^t}{1 - qe^t}$

---

## 2. 기하 분포의 무기억성 (Memoryless Property)

**[KR]** 기하 분포가 가지는 가장 독특하고 강력한 특징은 바로 **'무기억성(Memoryless Property)'**입니다. 이는 과거에 얼마나 많은 실패를 겪었는지가 미래의 성공 확률에 단 1%의 영향도 주지 않는다는 것을 의미합니다. 이미 $s$번을 실패했다는 전제하에 추가로 $t$번을 더 시도해야 할 확률은, 아무런 배경 지식 없이 처음부터 $t$번을 시도해야 할 확률과 완벽히 동일합니다.

**[EN]** The most unique and powerful characteristic of the geometric distribution is its **'Memoryless Property'**. This implies that the history of past failures has absolutely zero impact on the probability of future success. The conditional probability of needing $t$ additional trials, given that $s$ trials have already failed, is perfectly identical to the baseline probability of needing $t$ trials from the very beginning.

$$
P(X > s + t \mid X > s) = P(X > t)
$$

---

## 3. 음이항 분포 (Negative Binomial Distribution)

**[KR]** 기하 분포의 개념을 한 단계 확장하여, 첫 번째가 아닌 **'$r$번째 성공'을 달성하기 위해 필요한 총 시도 횟수**를 모델링한 것이 바로 음이항 분포(Negative Binomial Distribution)입니다. 총 $k$번의 시도 끝에 $r$번째 성공을 이뤄냈다면, 마지막 $k$번째는 무조건 성공이어야만 하고, 그 이전의 $k-1$번의 시도 중에서는 정확히 $r-1$번의 성공이 흩어져 있어야 합니다. 이를 조합을 활용해 나타내면 아래와 같습니다.

**[EN]** Generalizing the concept of the geometric distribution, the Negative Binomial Distribution models the total number of trials required to achieve the **'$r$-th success'** rather than just the first. If the $r$-th success is achieved exactly on the $k$-th trial, the $k$-th trial must definitively be a success, and there must have been exactly $r-1$ successes interspersed among the preceding $k-1$ trials. Using combinations, this is expressed as:

$$
P(X = k) = \binom{k-1}{r-1} p^r q^{k-r}
$$

* **통계적 특성:** 음이항 분포는 근본적으로 $r$개의 서로 독립적인 기하 분포를 하나로 합친 것과 같습니다.
* **기댓값 (Mean):** $E[X] = \frac{r}{p}$
* **분산 (Variance):** $Var(X) = \frac{rq}{p^2}$

---

## 4. 이항 분포와의 직관적 비교 (Comparison with Binomial)

**[KR]** 이항 분포(Binomial)와 음이항 분포(Negative Binomial)는 현상을 바라보는 관점에서 완벽한 대칭을 이룹니다. 이항 분포는 **"정해진 횟수만큼 시도했을 때 도대체 몇 번을 성공할 것인가?"**를 묻는다면, 음이항 분포는 **"정해진 목표 성공 횟수를 채우려면 도대체 몇 번을 시도해야 하는가?"**를 묻는 통계적 모델입니다.

**[EN]** The Binomial and Negative Binomial distributions exhibit a perfect symmetry in their perspectives. While the Binomial distribution asks, **"How many successes will occur within a fixed number of trials?"**, the Negative Binomial distribution asks the inverse question: **"How many trials are necessary to achieve a fixed target number of successes?"**

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-3 Geometric and Negative Binomial Distributions-1" src="https://github.com/user-attachments/assets/ce84e6c4-cf5e-4df1-bc84-805e377845e5" />
    <img width="1264" height="1635" alt="1-3 Geometric and Negative Binomial Distributions-2" src="https://github.com/user-attachments/assets/8bdbeadd-dfe0-496e-9574-4ee8fc371701" />
    <img width="1264" height="1635" alt="1-3 Geometric and Negative Binomial Distributions-3" src="https://github.com/user-attachments/assets/be213d35-3bd0-468a-a2fe-e7d81bb0b804" />
    <img width="1264" height="1635" alt="1-3 Geometric and Negative Binomial Distributions-4" src="https://github.com/user-attachments/assets/7b16224c-1ec0-4ff1-8432-cc1507818bb6" />
  </div>
</details>
