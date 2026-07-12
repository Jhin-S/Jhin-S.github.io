---
title: "1-1 Bernoulli and Binomial Distributions"
date: 2026-07-12 13:41:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, bernoulli, binomial, mgf, expected-value]
math: true
---

## 1. 베르누이 분포 (Bernoulli Distribution)

**[KR]** 통계학에서 가장 기초가 되는 확률 분포로, 어떤 시행의 결과가 오직 '성공(Success, 1)' 또는 '실패(Failure, 0)' 단 두 가지로만 나타나는 경우를 모델링합니다. 성공할 확률을 $p$, 실패할 확률을 $q = 1 - p$ 로 정의합니다.

**[EN]** The Bernoulli distribution is the most fundamental probability distribution in statistics, modeling an experiment that results in exactly two possible outcomes: 'Success' (1) or 'Failure' (0). The probability of success is denoted by $p$, and the probability of failure by $q = 1 - p$.

* **확률 변수 $X$의 정의:**
  $$X = \begin{cases} 1 & \text{with probability } p \\ 0 & \text{with probability } q \end{cases}$$
* **기본 통계량 요약:**
  평균(기댓값) $E[X] = p$, 분산 $Var(X) = pq$, 적률 생성 함수 $M_X(t) = pe^t + q$

---

## 2. 이항 분포 (Binomial Distribution)

**[KR]** 이항 분포는 동일한 성공 확률 $p$를 가진 베르누이 시행을 **독립적으로 $n$번 반복**했을 때, 총 성공한 횟수 $Y$가 따르는 확률 분포입니다. $n$번의 시도 중 $k$번 성공할 확률은 조합(Combination, $\binom{n}{k}$)을 사용하여 계산합니다.

**[EN]** The Binomial distribution describes the probability of having exactly $k$ successes in $n$ **independent** Bernoulli trials, each with the same success probability $p$. The probability is calculated using combinations ($\binom{n}{k}$).

$$
P(Y = k) = \binom{n}{k} p^k q^{n-k} \quad (k = 0, 1, \dots, n)
$$

### 실전 예제 (Practice Example)
두 개의 주사위를 동시에 던져서 두 눈의 합이 7이 나오는 사건을 관찰합니다. 이 시행을 5번 반복할 때, 합이 7이 나오는 횟수를 $Y$라고 합시다.
주사위 두 개의 합이 7이 될 확률은 $\frac{6}{36} = \frac{1}{6}$ 입니다. 따라서 $Y$는 이항 분포 $Bin(5, 1/6)$ 을 따릅니다.
합이 7인 경우가 정확히 4번 발생할 확률 $P(Y=4)$는 다음과 같이 계산할 수 있습니다.

$$
P(Y = 4) = \binom{5}{4} \left(\frac{1}{6}\right)^4 \left(\frac{5}{6}\right)^1
$$

---

## 3. 이항 분포의 통계적 성질과 MGF (Properties of Binomial RV)

**[KR]** 이항 분포 $Y \sim Bin(n, p)$ 는 논리적으로 $n$개의 독립적인 베르누이 확률 변수들의 합($Y = \sum_{i=1}^n X_i$)으로 완벽하게 분해할 수 있습니다. 기댓값의 선형성 덕분에 이항 분포의 통계량은 직관적으로 아주 쉽게 도출됩니다.

**[EN]** A Binomial random variable $Y \sim Bin(n, p)$ can be logically perfectly decomposed into the sum of $n$ independent Bernoulli random variables ($Y = \sum_{i=1}^n X_i$). Thanks to the linearity of expectations, deriving its statistical properties becomes incredibly intuitive.

* **평균 (Mean):** $n$번의 시행 각각에서 기대되는 성공 횟수 $p$를 더합니다.
  $$E[Y] = E\left[\sum_{i=1}^n X_i\right] = \sum_{i=1}^n E[X_i] = np$$
* **분산 (Variance):** 독립 시행이므로 각 분산을 단순히 더합니다.
  $$Var(Y) = npq$$
* **적률 생성 함수 (MGF):** 독립인 확률 변수들의 합의 MGF는 각 MGF의 곱과 같으므로 $n$제곱이 됩니다.
  $$M_Y(t) = (pe^t + q)^n$$

---

## 4. 이항 분포의 덧셈 정리 (Sum of Binomials)

**[KR]** 아주 유용한 정리 중 하나입니다. 만약 여러 개의 이항 분포 확률 변수 $Y_1, Y_2, \dots, Y_k$ 들이 서로 **독립**이고, 모두 **동일한 성공 확률 $p$**를 공유하고 있다면, 이 변수들을 모두 더한 새로운 확률 변수 역시 거대한 하나의 이항 분포를 따르게 됩니다. 시행 횟수만 모두 더해주면 됩니다.

**[EN]** This is a highly practical theorem. If multiple Binomial random variables $Y_1, Y_2, \dots, Y_k$ are **independent** and share the **exact same success probability $p$**, their sum will also follow a grand Binomial distribution. You simply add all the individual trial numbers together.

$$
\text{If } Y_i \sim Bin(n_i, p) \text{ and independent, then } \sum_{i=1}^k Y_i \sim Bin\left(\sum_{i=1}^k n_i, p\right)
$$

(이 정리는 적률 생성 함수(MGF)가 각 확률 분포를 유일하게 결정짓는다는 'MGF의 유일성 정리'를 통해 수학적으로 우아하게 증명될 수 있습니다.)

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1 Bernoulli and Binomial Distributions-1" src="https://github.com/user-attachments/assets/7f37222a-2d54-41ba-9038-947172369df9" />
  </div>
</details>
