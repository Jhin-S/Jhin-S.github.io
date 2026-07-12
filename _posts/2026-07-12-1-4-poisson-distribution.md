---
title: "1-4 Poisson Distribution"
date: 2026-07-12 14:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, poisson-distribution, poisson-process, mgf, expected-value]
math: true
---

## 1. 푸아송 프로세스의 이해 (Understanding the Poisson Process)

**[KR]** 푸아송 프로세스(Poisson Process)는 특정 시간 구간이나 공간 내에서 무작위로 발생하는 사건의 횟수 $N(t)$를 추적하는 계수 과정(Counting Process)입니다. 단위 시간당 평균 발생 횟수를 $\lambda$ 라고 할 때, 이 과정이 성립하려면 세 가지 엄격한 수학적 가정이 필요합니다.

**[EN]** A Poisson Process is a counting process $N(t)$ that tracks the number of random events occurring within a specific interval of time or space. Given an average occurrence rate $\lambda$ per unit time, this process relies on three strict mathematical assumptions.

1. **독립성 (Independent Increments):** 겹치지 않는 두 시간 구간에서 발생하는 사건의 횟수는 서로 완벽하게 독립적이어야 합니다.
2. **정상성 (Stationary Increments):** 사건 발생의 패턴이나 비율($\lambda$)이 시간에 따라 변하지 않고 항상 일정하게 유지되어야 합니다.
3. **단발성 (One-at-a-time):** 아주 짧은 찰나의 시간 $h$ 동안 사건이 동시에 2번 이상 발생할 확률은 $0$에 수렴해야 합니다. 오직 한 번씩만 개별적으로 발생해야 합니다.

---

## 2. 푸아송 분포의 도출 (Derivation of the Poisson Distribution)

**[KR]** 위에서 언급한 푸아송 프로세스의 가정들을 미분 방정식으로 변환하여 풀면, 특정 시간 $t$ 동안 사건이 정확히 $x$번 발생할 확률을 계산하는 놀라운 공식을 얻게 됩니다. 단위 시간($t=1$)을 기준으로 할 때, 이를 **푸아송 분포(Poisson Distribution)**라고 부릅니다.

**[EN]** By translating the assumptions of the Poisson process into differential equations and solving them, we discover a remarkable formula calculating the probability of exactly $x$ events occurring in time $t$. For a unit time interval ($t=1$), this is formally known as the **Poisson Distribution**.

$$
P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!} \quad (k = 0, 1, 2, \dots)
$$

* **단위 변환의 유연성:** $\lambda$는 단순히 단위만 바꿔주면 자유롭게 변환됩니다. 예를 들어 1분에 평균 3번 울리는 전화($\lambda=3/\text{min}$)라면, 5분 동안은 $\lambda=15/\text{5min}$가 되며, 40초 동안은 $\lambda=2/\text{40sec}$로 설정하여 동일한 공식을 적용할 수 있습니다.

---

## 3. 적률 생성 함수와 통계량 (MGF, Mean, and Variance)

**[KR]** 푸아송 분포의 가장 우아하고 독특한 특징은 **평균과 분산이 완전히 동일하다는 점**입니다. 이는 무한 급수의 테일러 전개 성질을 활용한 적률 생성 함수(MGF)를 통해 아주 깔끔하게 증명됩니다.

**[EN]** The most elegant and unique characteristic of the Poisson distribution is that **its mean and variance are exactly identical**. This is cleanly proven using the Moment Generating Function (MGF) derived from the Taylor series expansion of exponential functions.

* **적률 생성 함수 (MGF):**
  
$$
M_X(t) = E[e^{tX}] = e^{\lambda(e^t - 1)}
$$

* **평균(기댓값) 및 분산:** MGF를 미분하여 $t=0$을 대입하면 두 값이 같다는 것을 확인할 수 있습니다.
  
$$
E[X] = \lambda, \quad Var(X) = \lambda
$$

---

## 4. 푸아송 분포의 덧셈 정리 (Additive Property of Poissons)

**[KR]** 여러 개의 푸아송 확률 변수들이 서로 **독립(Independent)**이라면, 이들을 모두 더한 새로운 확률 변수 역시 푸아송 분포를 그대로 유지합니다. 이때 새로운 분포의 파라미터는 단순히 기존의 $\lambda$ 값들을 모두 더한 것과 같습니다.

**[EN]** If multiple Poisson random variables are **independent**, the new random variable created by summing them all together perfectly retains the Poisson distribution. The parameter for this new distribution is simply the sum of all individual $\lambda$ values.

$$
\text{If } X_i \sim Pois(\lambda_i) \text{ and independent, then } \sum_{i=1}^n X_i \sim Pois\left(\sum_{i=1}^n \lambda_i\right)
$$

### 실전 예제 (Practice Example)
어떤 주차장에 남성 운전자는 시간당 평균 3대($\lambda_1 = 3$), 여성 운전자는 시간당 평균 5대($\lambda_2 = 5$)의 비율로 들어옵니다. 이 두 그룹의 도착이 완전히 독립적이라면, 전체 도착 차량의 횟수는 시간당 $\lambda = 8$ 인 푸아송 분포를 따릅니다.
만약 다음 '30분' 동안 정확히 2대의 차가 들어올 확률을 묻는다면, 30분에 해당하는 파라미터는 절반인 $\lambda = 4$ 가 되므로 공식에 의해 $P(X=2) = \frac{e^{-4} 4^2}{2!}$ 로 쉽게 계산할 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-4 Poisson Distribution-1" src="https://github.com/user-attachments/assets/2aa2a5be-0959-4e08-b0c9-3832f0f6b107" />
    <img width="1264" height="1635" alt="1-4 Poisson Distribution-2" src="https://github.com/user-attachments/assets/57b3c895-3bb5-46c7-bd2c-92c02940e222" />
    <img width="1264" height="1635" alt="1-4 Poisson Distribution-3" src="https://github.com/user-attachments/assets/a98a4e51-8659-45f5-9a23-995d7420f571" />
    <img width="1264" height="1635" alt="1-4 Poisson Distribution-4" src="https://github.com/user-attachments/assets/55672d98-b502-4b4f-bbf4-a563cf4af2e2" />
    <img width="1264" height="1635" alt="1-4 Poisson Distribution-5" src="https://github.com/user-attachments/assets/6d0d0ffb-da95-40b9-8b5b-200a41ae1575" />
    <img width="1264" height="1635" alt="1-4 Poisson Distribution-6" src="https://github.com/user-attachments/assets/d65e82ba-69e7-4512-86e2-a5acfd0197a9" />
  </div>
</details>
