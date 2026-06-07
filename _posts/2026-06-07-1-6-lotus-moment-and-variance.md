---
title: "1-6 LOTUS, Moment,, and Variance"
date: 2026-06-07 14:20:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, lotus, variance, moment, gamma-function]
math: true
---

## 1. 무의식적인 통계학자의 법칙 (LOTUS)

**[KR]** 확률 변수 $X$에 대한 새로운 함수 $h(X)$의 기댓값을 구하고 싶을 때, $h(X)$ 자체의 확률 분포를 새롭게 구하지 않고도 원래 $X$의 확률 분포 $f(x)$를 그대로 이용하여 기댓값을 계산할 수 있게 해주는 아주 유용한 정리입니다. 이를 **무의식적인 통계학자의 법칙(Law of the Unconscious Statistician, LOTUS)**이라고 부릅니다.

**[EN]** The Law of the Unconscious Statistician (LOTUS) is a powerful theorem that allows us to calculate the expected value of a function of a random variable, $h(X)$, without needing to know the probability distribution of $h(X)$ itself. We simply use the original distribution $f(x)$ of $X$.

* **이산 확률 변수 (Discrete):** $$E[h(X)] = \sum_x h(x)f(x)$$
* **연속 확률 변수 (Continuous):** $$E[h(X)] = \int_{-\infty}^{\infty} h(x)f(x) \,dx$$

---

## 2. 적률과 감마 함수 (Moments & Gamma Function)

**[KR]** 통계학에서 확률 분포의 형태(기울어짐, 뾰족함 등)를 설명하기 위해 $X$의 거듭제곱에 대한 기댓값을 계산하며, 이를 **적률(Moment)**이라고 합니다. 제 $k$차 적률은 $E[X^k]$ 로 정의됩니다.

**[EN]** In statistics, to describe the shape characteristics of a probability distribution (like skewness or kurtosis), we calculate the expected values of the powers of $X$. These are called **Moments**. The $k$-th moment is defined as $E[X^k]$.

### 지수 분포의 적률과 감마 함수
지수 분포 $X \sim Exp(\lambda)$ 의 $k$차 적률을 계산하다 보면 자연스럽게 **감마 함수(Gamma Function)**가 등장합니다. 감마 함수 $\Gamma(x)$는 자연수의 팩토리얼($!$) 개념을 실수와 복소수 영역으로 확장한 특수 함수입니다.

$$
\Gamma(n) = \int_0^\infty t^{n-1} e^{-t} \,dt
$$

* **감마 함수의 핵심 성질:** $\Gamma(n+1) = n\Gamma(n)$ (자연수일 경우 $n!$ 과 같습니다.)
* **지수 분포의 $k$차 적률:** 위 적분 성질을 활용하면 지수 분포의 적률은 다음과 같이 깔끔하게 도출됩니다.
  
$$
E[X^k] = \int_0^\infty x^k \lambda e^{-\lambda x} \,dx = \frac{\Gamma(k+1)}{\lambda^k}
$$

---

## 3. 중심 적률과 분산 (Central Moments & Variance)

**[KR]** 값들이 평균 $\mu$ 로부터 얼마나 떨어져 있는지를 평가하기 위해 기준점을 평균으로 잡은 적률을 **중심 적률(Central Moment)**이라고 합니다. 제 $k$차 중심 적률은 $E[(X - \mu)^k]$ 입니다.
이 중에서 **제 2차 중심 적률을 우리는 '분산(Variance)'**이라고 부르며, 데이터가 평균을 중심으로 얼마나 넓게 퍼져있는지(산포도)를 나타냅니다.

**[EN]** To evaluate how far values deviate from the mean $\mu$, we use moments centered around the mean, known as **Central Moments**. The $k$-th central moment is $E[(X - \mu)^k]$. 
The **second central moment is what we call 'Variance'**, which measures the spread or dispersion of the data around its mean.

* **분산 (Variance):** $Var(X) = E[(X - \mu)^2]$
* **표준편차 (Standard Deviation):** $\sigma = \sqrt{Var(X)}$

### 분산의 실용적인 계산 공식 (Easier Formula for Variance)
정의에 따라 $(X - \mu)^2$ 을 직접 전개하여 기댓값을 취하면, 분산을 계산하는 훨씬 더 실용적인 공식을 얻을 수 있습니다. **(분산 = 제곱의 평균 - 평균의 제곱)**

$$
Var(X) = E[X^2 - 2\mu X + \mu^2] = E[X^2] - 2\mu E[X] + \mu^2 = E[X^2] - \mu^2
$$

$$
Var(X) = E[X^2] - (E[X])^2
$$

---

## 4. 기댓값과 분산의 선형성 (Linearity Properties)

**[KR]** 변수 $X$에 어떤 상수 $a$를 곱하고 $b$를 더하는 선형 변환($Y = aX + b$)을 했을 때, 기댓값과 분산이 어떻게 변하는지 나타내는 공식입니다.

**[EN]** These formulas describe how the expected value and variance change when we apply a linear transformation ($Y = aX + b$) to a random variable $X$.

1. **기댓값의 선형성 (Linearity of Expectation):** 기댓값은 덧셈과 실수배에 대해 완전히 밖으로 빠져나올 수 있습니다.
   $$E[aX + b] = aE[X] + b$$

2. **분산의 특성 (Properties of Variance):** 분산은 '퍼짐의 정도'이므로, 단순히 모든 값에 상수 $b$를 더해 위치만 이동시키는 것은 퍼짐 정도에 아무런 영향을 주지 않습니다(상수 무시). 반면, 값의 간격을 $a$배 늘리면 분산은 제곱인 $a^2$배로 증폭됩니다.
   $$Var(aX + b) = a^2 Var(X)$$

### 간단한 응용 예제
확률 변수 $X$가 베르누이 분포 $Bern(0.3)$ 을 따른다고 가정합시다.
* 평균: $E[X] = p = 0.3$
* 분산: $Var(X) = p(1-p) = 0.3 \times 0.7 = 0.21$

새로운 변수 $Y = 4X + 5$ 가 주어졌을 때, $Y$의 기댓값과 분산은 선형성 성질을 통해 아주 쉽게 구할 수 있습니다.
* $E[Y] = 4E[X] + 5 = 4(0.3) + 5 = 6.2$
* $Var(Y) = 4^2 Var(X) = 16(0.21) = 3.36$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-6 LOTUS, Moment,, and Variance-1" src="https://github.com/user-attachments/assets/7af5db09-76e2-4bf2-b8ea-8bed9121d907" />
    <img width="1264" height="1635" alt="1-6 LOTUS, Moment,, and Variance-2" src="https://github.com/user-attachments/assets/d47dd629-f4b8-4ac8-a008-8e483157da26" />
    <img width="1264" height="1635" alt="1-6 LOTUS, Moment,, and Variance-3" src="https://github.com/user-attachments/assets/a9349b66-1f86-4079-ae8b-1cc8cec1d132" />
    <img width="1264" height="1635" alt="1-6 LOTUS, Moment,, and Variance-4" src="https://github.com/user-attachments/assets/d8379601-8088-417f-8852-1aef2d963b6c" />
    <img width="1264" height="1635" alt="1-6 LOTUS, Moment,, and Variance-5" src="https://github.com/user-attachments/assets/f289c75c-ff18-4fec-8c02-9f1bb42e8d8d" />
    <img width="1264" height="1635" alt="1-6 LOTUS, Moment,, and Variance-6" src="https://github.com/user-attachments/assets/f12c9a75-7b69-416e-8ad5-a1b64c54e09b" />
  </div>
</details>
