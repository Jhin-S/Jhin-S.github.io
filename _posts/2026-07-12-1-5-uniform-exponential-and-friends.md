---
title: "1-5 Uniform, Exponential, and Friends"
date: 2026-07-12 14:30:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, uniform-distribution, exponential-distribution, erlang-distribution, gamma-distribution, memoryless-property]
math: true
---

## 1. 연속 균등 분포 (Continuous Uniform Distribution)

**[KR]** 연속 균등 분포는 특정 구간 $[a, b]$ 내에서 모든 값이 나타날 확률(정확히는 확률 밀도)이 완벽하게 동일한 가장 단순한 형태의 연속 확률 분포입니다. 직사각형 모양의 확률 밀도 함수(pdf)를 가집니다.

**[EN]** The Continuous Uniform distribution is the simplest continuous probability distribution, where all values within a specific interval $[a, b]$ have the exact same probability density. It features a rectangular-shaped probability density function (pdf).

* **확률 밀도 함수 (pdf):** 구간 $[a, b]$에서 $f(x) = \frac{1}{b-a}$ (그 외 구간은 $0$)
* **통계량 요약:** * 평균 (Mean): $E[X] = \frac{a+b}{2}$
  * 분산 (Variance): $Var(X) = \frac{(a-b)^2}{12}$
  * 적률 생성 함수 (MGF): $M_X(t) = \frac{e^{tb} - e^{ta}}{t(b-a)}$

---

## 2. 지수 분포와 무기억성 (Exponential Distribution & Memoryless Property)

**[KR]** 지수 분포는 어떤 사건이 발생할 때까지 기다려야 하는 '대기 시간'이나 기계의 '수명' 등을 모델링할 때 널리 쓰이는 분포입니다. 
지수 분포가 가지는 가장 위대한 특징은 연속 확률 분포 중 유일하게 **'무기억성(Memoryless Property)'**을 가진다는 점입니다. 예를 들어, 평균 수명이 10개월인 전구가 이미 20개월을 살아남았다고 하더라도, 앞으로 10개월을 더 살아남을 확률은 새 전구가 10개월을 살아남을 확률과 완벽하게 동일합니다. 즉, 기계가 닳거나 노후화되지 않는다고 가정하는 "항상 새것과 같은(Always good as new)" 상태를 수학적으로 표현한 것입니다.

**[EN]** The Exponential distribution is widely used to model 'waiting times' until an event occurs or the 'lifespan' of a machine. 
Its greatest feature is that it is the only continuous probability distribution possessing the **'Memoryless Property'**. For instance, if a lightbulb with an average lifespan of 10 months has already survived for 20 months, the probability of it surviving another 10 months is exactly the same as a brand-new bulb surviving its first 10 months. It mathematically represents an "always good as new" state, assuming no wear and tear.

* **수학적 정의:** $X \sim Exp(\lambda)$ 일 때, $f(x) = \lambda e^{-\lambda x} \quad (x > 0)$
* **무기억성 증명:** 조건부 확률 공식을 통해 아주 우아하게 증명됩니다.
  
$$
P(X > s+t \mid X > s) = \frac{P(X > s+t \text{ and } X > s)}{P(X > s)} = \frac{P(X > s+t)}{P(X > s)} = \frac{e^{-\lambda(s+t)}}{e^{-\lambda s}} = e^{-\lambda t} = P(X > t)
$$

### 고장률 함수 (Failure Rate / Hazard Function)
어떤 시점 $t$까지 생존해 있을 때, 바로 그 다음 순간에 고장 날(사망할) 순간적인 비율을 고장률 함수 $S(t)$라고 합니다.
$$S(t) = \frac{f(t)}{1 - F(t)}$$
지수 분포를 여기에 대입해보면 $S(t) = \frac{\lambda e^{-\lambda t}}{e^{-\lambda t}} = \lambda$ 가 됩니다. 즉, 시간에 상관없이 고장 날 위험(비율)이 항상 일정한 상수 $\lambda$로 고정되어 있다는 뜻이며, 이는 무기억성의 또 다른 강력한 증거입니다.

---

## 3. 지수 분포의 친구들: 얼랑 분포와 감마 분포 (Erlang & Gamma Distributions)

**[KR]** 지수 분포가 '첫 번째' 사건이 발생할 때까지의 시간이라면, 이를 확장하여 **'$k$번째' 사건이 발생할 때까지 걸린 총 대기 시간**을 모델링한 것이 바로 **얼랑 분포(Erlang Distribution)**입니다. 수학적으로는 서로 독립이고 동일한 지수 분포를 따르는 확률 변수들을 $k$개 더한 것($S = \sum_{i=1}^k X_i$)과 같습니다.
여기서 횟수를 의미하는 정수 $k$를, 감마 함수($\Gamma$)를 이용하여 양의 실수 $\alpha$의 영역으로 부드럽게 확장(Generalization)한 것이 바로 **감마 분포(Gamma Distribution)**입니다.

**[EN]** While the Exponential distribution models the time until the 'first' event, extending this to model the **total waiting time until the '$k$-th' event** gives us the **Erlang Distribution**. Mathematically, it is the sum of $k$ independent and identically distributed (i.i.d.) exponential random variables ($S = \sum_{i=1}^k X_i$).
When we smoothly generalize the integer parameter $k$ (representing the number of events) into any positive real number $\alpha$ using the Gamma function ($\Gamma$), it becomes the **Gamma Distribution**.

* **얼랑 분포 통계량 (Erlang Statistics):**
  지수 분포 $k$개의 합이므로 기댓값의 선형성에 의해 평균은 $\frac{k}{\lambda}$, 분산은 $\frac{k}{\lambda^2}$ 가 됩니다. 적률 생성 함수(MGF) 역시 지수 분포의 MGF를 $k$제곱한 형태를 띱니다.
  
$$
M_S(t) = \left(\frac{\lambda}{\lambda - t}\right)^k
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-5 Uniform, Exponential, and Friends-1" src="https://github.com/user-attachments/assets/bb706ce3-6aaf-4803-bc3d-21a881f13676" />
    <img width="1264" height="1635" alt="1-5 Uniform, Exponential, and Friends-2" src="https://github.com/user-attachments/assets/81d67e92-2f4d-4b7a-a8b0-eb99fec1cef5" />
    <img width="1264" height="1635" alt="1-5 Uniform, Exponential, and Friends-3" src="https://github.com/user-attachments/assets/bd6e5455-55a4-42c8-927b-157134ab0b96" />
    <img width="1264" height="1635" alt="1-5 Uniform, Exponential, and Friends-4" src="https://github.com/user-attachments/assets/ae7de08e-60eb-41e1-aaa3-e9859f33403b" />
    <img width="1264" height="1635" alt="1-5 Uniform, Exponential, and Friends-5" src="https://github.com/user-attachments/assets/c586d41a-ab97-405b-8240-a5ffc38062f2" />
  </div>
</details>
