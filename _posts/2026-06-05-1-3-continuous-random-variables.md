---
title: "1-3 Continuous Random Variables"
date: 2026-06-06 00:20:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, random-variable, continuous, pdf, exponential, normal-distribution]
math: true
---

## 1. 연속 확률 변수와 확률 밀도 함수 (Continuous RV & PDF)

**[KR]** 연속 확률 변수 $X$는 실수 구간 내의 무수히 많은 값을 가질 수 있습니다. 이러한 연속적인 세계에서는 특정한 정확한 점(예: 정확히 0.5000...)을 뽑을 확률은 0이 됩니다 ($P(X=x) = 0$). 따라서 연속 확률 변수에서는 이산 확률 변수의 '질량(Mass)' 대신, 면적을 통해 확률을 구하는 **확률 밀도 함수(Probability Density Function, PDF)** $f(x)$를 사용합니다. 

**[EN]** A continuous random variable $X$ can take any value within a range of real numbers. In this continuous space, the probability of $X$ taking one exact, specific point is zero ($P(X=x) = 0$). Therefore, instead of using a mass function, we use a **Probability Density Function (PDF)** $f(x)$, where probabilities are calculated by finding the area under the curve.

확률 밀도 함수 $f(x)$가 되기 위해서는 다음 세 가지 필수 조건을 만족해야 합니다.
1. **전체 면적은 1:** 함수를 실수 전체 구간에서 적분한 값은 1이어야 합니다. ($\int_{-\infty}^{\infty} f(x)dx = 1$)
2. **항상 양수:** 확률의 개념을 담고 있으므로 그래프가 $x$축 아래로 내려갈 수 없습니다. ($f(x) \ge 0$)
3. **면적이 곧 확률:** 특정 구간 $[a, b]$에 속할 확률은 그 구간에서 함수를 적분한 값과 같습니다.
   $$P(a < X < b) = \int_{a}^{b} f(x)dx$$

* **💡 핵심 포인트:** 특정 점에서의 확률이 0이므로, 연속 확률 변수에서는 부등호에 등호가 포함되든 안 되든 확률 값에는 전혀 영향을 주지 않습니다.
  $$P(a < X < b) = P(a \le X < b) = P(a \le X \le b)$$

---

## 2. 대표적인 연속 확률 분포 (Common Continuous Distributions)

### ① 균등 분포 (Uniform Distribution)
**[KR]** 어떤 구간 $(a, b)$ 내에서 모든 값이 나타날 가능성이 '동등하게(Equally likely)' 퍼져있는 분포입니다. 평평한 직사각형 모양의 그래프를 가집니다.
**[EN]** A distribution where all intervals of the same length are equally probable. It has a flat, rectangular-shaped PDF.

$$
f(x) = \frac{1}{b-a} \quad (\text{for } a \le x \le b)
$$
*(표기: $X \sim Unif(a,b)$)*

### ② 지수 분포 (Exponential Distribution)
**[KR]** 대기 시간이나 수명 등을 모델링할 때 자주 쓰이며, 파라미터 $\lambda > 0$를 가집니다. $x \ge 0$인 구간에서 급격히 감소하는 곡선 형태를 띱니다.
**[EN]** Often used to model waiting times or lifetimes, characterized by a parameter $\lambda > 0$. The curve decays exponentially for $x \ge 0$.

$$
f(x) = \lambda e^{-\lambda x} \quad (\text{for } x \ge 0)
$$
*(표기: $X \sim Exp(\lambda)$)*

---

## 3. PDF를 활용한 심화 계산 (Advanced Calculations with PDF)

**[KR]** 확률 밀도 함수를 다룰 때 가장 중요한 것은 **"전체 적분 값이 1이 되어야 한다"**는 성질입니다. 이를 이용하면 미지수 상수를 쉽게 구할 수 있습니다. 또한, 이산 확률 변수에서 배웠던 조건부 확률(Conditional Probability) 공식 역시 적분 기호만 씌우면 연속 확률 변수에 똑같이 적용할 수 있습니다.

**[EN]** The fundamental property of a PDF is that **its total integral must equal 1**. This is extremely useful for finding unknown constants in a given function. Furthermore, the conditional probability formula we learned for discrete variables applies perfectly to continuous variables—we simply use integrals to find the required probabilities.

**Example:** $f(x) = cx^2 \text{ (for } 0 < x < 2 \text{)}$ 일 때, 상수 $c$의 값과 조건부 확률 구하기.

1. **상수 $c$ 찾기:**
   전체 적분값이 1이 되어야 하므로, $\int_{0}^{2} cx^2 dx = \left[ \frac{c}{3}x^3 \right]_{0}^{2} = \frac{8c}{3} = 1 \implies c = \frac{3}{8}$

2. **조건부 확률 계산:** $P(0 < X < 1 \vert \frac{1}{2} < X < \frac{3}{2})$
   조건부 확률의 정의에 따라 교집합 영역을 분모의 영역으로 나눕니다.
   
$$
\frac{P(\frac{1}{2} < X < 1)}{P(\frac{1}{2} < X < \frac{3}{2})} = \frac{\int_{1/2}^{1} \frac{3}{8}x^2 dx}{\int_{1/2}^{3/2} \frac{3}{8}x^2 dx} = \frac{7}{26}
$$

---

## 4. 표준 정규 분포 (Standard Normal Distribution)

**[KR]** 통계학에서 가장 유명하고 중요한 '종 모양(Bell curve)'의 분포입니다. 모든 정규 분포의 기준이 되며, 평균이 0이고 표준편차가 1인 형태입니다.

**[EN]** The most famous and important distribution in statistics, known for its symmetrical "bell curve" shape. It serves as the baseline for all normal distributions, centered at a mean of 0 with a standard deviation of 1.

$$
\phi(x) = \frac{1}{\sqrt{2\pi}} e^{-x^2 / 2} \quad (\text{for all } x \in \mathbb{R})
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-3 Continuous Random Variables-1" src="https://github.com/user-attachments/assets/d981ebbd-3687-4009-8e89-599e4a5aba41" />
    <img width="1264" height="1635" alt="1-3 Continuous Random Variables-2" src="https://github.com/user-attachments/assets/d4a02c4c-ac6d-475d-9a70-c32abb042f51" />
    <img width="1264" height="1635" alt="1-3 Continuous Random Variables-3" src="https://github.com/user-attachments/assets/8c5fce6b-0b6c-4e1c-a4be-d809d40372e3" />
    <img width="1264" height="1635" alt="1-3 Continuous Random Variables-4" src="https://github.com/user-attachments/assets/b8d02d0e-832b-4366-afb1-0e1a89ff7c1a" />
    <img width="1264" height="1635" alt="1-3 Continuous Random Variables-5" src="https://github.com/user-attachments/assets/2bdf11ac-b4a5-43b7-bcbc-b5ff65ca2968" />
    <img width="1264" height="1635" alt="1-3 Continuous Random Variables-6" src="https://github.com/user-attachments/assets/fe1ffe8c-dc16-4b2f-a236-1857c6cc7f03" />
  </div>
</details>
