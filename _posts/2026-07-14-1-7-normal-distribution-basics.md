---
title: "1-7 Normal Distribution: Basics"
date: 2026-07-14 13:52:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, normal-distribution, gaussian-distribution, standardization, empirical-rule]
math: true
---

## 1. 정규 분포의 기초 (Introduction to the Normal Distribution)

**[KR]** 정규 분포(혹은 가우스 분포, Gaussian Distribution)는 자연계와 사회 현상에서 가장 빈번하게 발견되는 완벽한 대칭형의 '종 모양(Bell-curve)' 확률 분포입니다. 키, 몸무게, 시험 점수 등 수많은 데이터의 평균들이 이 분포를 따릅니다. 
데이터의 중심인 평균 $\mu$를 기준으로 양옆으로 대칭을 이루며, 분산 $\sigma^2$이 작을수록 중심에 데이터가 밀집되어 위로 솟은 뾰족한 형태가 되고, 분산이 클수록 낮고 넓게 퍼진 형태가 됩니다.

**[EN]** The Normal distribution (or Gaussian distribution) is a perfectly symmetric, bell-shaped probability distribution most frequently observed in nature and society. Variables like heights, weights, and test scores naturally follow this distribution. 
It is centered symmetrically around the mean $\mu$. A smaller variance $\sigma^2$ tightly clusters the data, resulting in a tall, narrow peak, while a larger variance spreads the data out into a shorter, wider curve.

* **확률 밀도 함수 (pdf):**
  
$$
f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left[-\frac{(x-\mu)^2}{2\sigma^2}\right] \quad (-\infty < x < \infty)
$$

---

## 2. 경험적 법칙과 적률 생성 함수 (Empirical Rule & MGF)

**[KR]** 정규 분포는 분포의 흩어짐에 대해 매우 명확한 수학적 성질을 가집니다. 평균을 중심으로 표준편차($\sigma$)의 1배, 2배, 3배 거리 안에 전체 데이터의 확률이 각각 약 68.3%, 95.5%, 99.7%가 포함됩니다. 제조업에서 불량률을 극도로 낮추기 위해 사용하는 '식스 시그마(6-Sigma)' 품질 관리 기법 역시 이 극한의 확률적 꼬리(Tail) 범위에서 유래한 것입니다.

**[EN]** The Normal distribution holds distinct mathematical properties regarding data dispersion. Approximately 68.3%, 95.5%, and 99.7% of the total probability lie within one, two, and three standard deviations ($\sigma$) from the mean, respectively. The famous 'Six Sigma' quality management methodology used in manufacturing originates from this extreme probability tail range.

* **적률 생성 함수 (MGF):**
  
$$
M_X(t) = E[e^{tX}] = \exp\left(\mu t + \frac{1}{2}\sigma^2 t^2\right)
$$

---

## 3. 정규 분포의 선형 결합 성질 (Additive Property of Normals)

**[KR]** 서로 독립인 여러 개의 정규 분포 확률 변수들을 서로 더하거나 특정 상수를 곱하는 선형 결합(Linear Combination)을 수행해도, 그 결과물은 **여전히 완벽한 정규 분포를 유지**합니다. 이는 적률 생성 함수의 유일성 정리를 통해 증명되며, 매우 강력한 통계적 도구가 됩니다. 즉, 독립적인 정규 분포들을 조합할 때는 새로운 분포의 형태를 고민할 필요 없이 오직 새로운 '평균'과 '분산'만 계산해주면 됩니다.

**[EN]** When we perform a linear combination of multiple independent normal random variables (by adding them or multiplying by constants), the resulting distribution **strictly remains a normal distribution**. This is proven via the uniqueness of the moment generating function and serves as a powerful statistical tool. When combining independent normals, you don't need to worry about the shape of the new distribution; you simply calculate the new 'mean' and 'variance'.

* **선형 결합 공식:** $X_i$ 들이 서로 독립인 정규 분포일 때,
  
$$
Y = \sum_{i=1}^n a_i X_i + b \sim N\left(\sum_{i=1}^n a_i \mu_i + b, \, \sum_{i=1}^n a_i^2 \sigma_i^2\right)
$$

### 실전 예제 (Practice Example)
독립적인 두 확률 변수 $X \sim N(3, 4)$ 와 $Y \sim N(4, 6)$ 이 있을 때, 새로운 변수 $2X - 3Y$ 의 분포를 구해봅시다.
* **새로운 평균:** $E[2X - 3Y] = 2E[X] - 3E[Y] = 2(3) - 3(4) = -6$
* **새로운 분산:** $Var(2X - 3Y) = 2^2 Var(X) + (-3)^2 Var(Y) = 4(4) + 9(6) = 16 + 54 = 70$
* **결론:** 정규 분포의 성질을 그대로 물려받아 $2X - 3Y \sim N(-6, 70)$ 이 성립합니다.

---

## 4. 표준화 (Standardization)

**[KR]** 위에서 증명한 선형 결합의 성질을 응용하면, 제각각 다른 평균과 분산을 가진 모든 정규 분포들을 단 하나의 절대적인 기준선으로 통일할 수 있습니다. 확률 변수 $X$에서 자신의 평균 $\mu$를 빼고 표준편차 $\sigma$로 나누어주는 변환 연산($Z$)을 거치면, 무조건 평균이 $0$이고 분산이 $1$인 **표준 정규 분포(Standard Normal Distribution)**로 탈바꿈합니다.

**[EN]** Applying the linear combination property, any normal distribution with its own specific mean and variance can be universally scaled to a single absolute baseline. By subtracting the mean $\mu$ from the variable $X$ and dividing it by its standard deviation $\sigma$, it mathematically transforms into the **Standard Normal Distribution**, which has a fixed mean of $0$ and a variance of $1$.

$$
Z = \frac{X - \mu}{\sigma} \sim N(0, 1)
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-7 Normal Distribution_ Basics-1" src="https://github.com/user-attachments/assets/a053d4ac-2b5f-41cc-ae68-c55b24e7c730" />
    <img width="1264" height="1635" alt="1-7 Normal Distribution_ Basics-2" src="https://github.com/user-attachments/assets/8d157079-e5e4-44e9-a77a-74ab7e5dbdfe" />
    <img width="1264" height="1635" alt="1-7 Normal Distribution_ Basics-3" src="https://github.com/user-attachments/assets/297c17b5-dfda-4e1a-9134-f9feb9b3e4c5" />
  </div>
</details>
