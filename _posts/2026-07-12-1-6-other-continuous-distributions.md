---
title: "1-6 Other Continuous Distributions"
date: 2026-07-12 14:45:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, triangular-distribution, beta-distribution, weibull-distribution, cauchy-distribution]
math: true
---

## 1. 삼각형 분포 (Triangular Distribution)

**[KR]** 삼각형 분포는 제한된 데이터나 최소한의 정보만으로 무작위 변수의 성질을 모델링해야 할 때 유용하게 쓰이는 연속 확률 분포입니다. 최솟값($a$), 최빈값($c$), 최댓값($b$)의 세 가지 파라미터로 정의되며, 확률 밀도 함수(pdf)가 삼각형 모양의 직선 구간들로 구성됩니다.

**[EN]** The triangular distribution is a continuous probability distribution useful for modeling random variables based on limited data and minimal information, defined by three parameters: minimum ($a$), mode ($c$), and maximum ($b$).

* **기댓값 (Mean):** $E[X] = \frac{a+b+c}{3}$

---

## 2. 베타 분포 (Beta Distribution)

**[KR]** 베타 분포는 확률이나 비율처럼 특정 구간(대개 $0$과 $1$ 사이)으로 값이 엄격하게 제한되는 데이터를 모델링하는 데 특화된 유연한 연속 확률 분포입니다. 감마 함수를 활용한 베타 함수를 통해 정의되며, 파라미터 $a$와 $b$의 조절에 따라 형태가 매우 다양하게 변합니다. 특수한 경우에 균등 분포나 삼각형 분포의 형태를 포함하기도 합니다.

**[EN]** The Beta distribution is a flexible continuous probability distribution tailored for modeling variables restricted to a specific finite interval, typically between $0$ and $1$. It is defined via the beta function and offers diverse shapes controlled by parameters $a$ and $b$.

* **확률 밀도 함수 (pdf):**
  $$f(x) = \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)} x^{a-1} (1-x)^{b-1} \quad (0 < x < 1)$$
* **기댓값 (Mean):** $E[X] = \frac{a}{a+b}$

---

## 3. 와이블 분포 (Weibull Distribution)

**[KR]** 와이블 분포는 신뢰성 공학이나 제품의 수명 및 고장 시간 분석에 탁월한 성능을 보이는 확률 분포입니다. 척도 파라미터 $a$와 형상 파라미터 $b$를 가지며, 우리가 잘 알고 있는 지수 분포(Exponential Distribution)는 와이블 분포의 특수한 한 형태(Special case)에 해당합니다.

**[EN]** The Weibull distribution is exceptionally well-suited for reliability models and time-to-failure analysis. Characterized by a scale parameter $a$ and a shape parameter $b$, the exponential distribution is a special case of the Weibull.

* **누적 분포 함수 (CDF):** $F(x) = 1 - \exp[-(ax)^b] \quad (x > 0)$
* **기댓값 (Mean):** $E[X] = \frac{1}{a} \Gamma\left(1 + \frac{1}{b}\right)$

---

## 4. 코시 분포 (Cauchy Distribution)

**[KR]** 코시 분포는 양쪽 꼬리가 매우 두껍고 무거운(Fat-tailed) 독특한 분포로, 통계학에서 기존의 직관을 깨거나 반례를 증명하는 용도로 종종 활용됩니다. 매우 흥미로운 성질로, **평균(Mean)이 정의되지 않으며 분산이 무한대**입니다. 또한 여러 개의 코시 분포 변수들을 더해서 개수로 나누어도 평균이 수렴하지 않고 다시 코시 분포가 되는 독특한 성질을 가집니다.

**[EN]** The Cauchy distribution is a symmetric, fat-tailed distribution often used in statistics to disprove assumptions and test boundaries. Fascinatingly, it has an undefined mean and an infinite variance. Taking the sample average of independent Cauchy random variables results right back in the Cauchy distribution itself.

* **확률 밀도 함수 (pdf):** $f(x) = \frac{1}{\pi(1+x^2)}$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-6 Other Continuous Distributions-1" src="https://github.com/user-attachments/assets/3dfda879-9ede-43e5-acaa-9a5c24b380db" />
    <img width="1264" height="1635" alt="1-6 Other Continuous Distributions-2" src="https://github.com/user-attachments/assets/d077b3fa-abbe-4bd8-a395-fd758a909f75" />
  </div>
</details>
