---
title: "2-9 Invariance Property of MLEs"
date: 2026-07-14 21:57:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, mle, maximum-likelihood, invariance-property, estimator]
math: true
---

## 1. 최대 우도 추정량의 불변성 (The Invariance Property of MLEs)

**[KR]** 최대 우도 추정법(MLE)이 통계학자들에게 사랑받는 가장 큰 이유 중 하나는 바로 **'불변성(Invariance Property)'**이라는 엄청난 특성 때문입니다. 
어떤 미지의 모수 $\theta$에 대한 MLE인 $\hat{\theta}$를 이미 구해두었다면, 모수 $\theta$로 이루어진 새로운 함수 $h(\theta)$의 MLE를 구하기 위해 처음부터 미분 방정식을 다시 풀 필요가 없습니다. 그저 기존에 구한 $\hat{\theta}$를 함수 $h$에 대입하기만 하면, 그것이 곧바로 $h(\theta)$의 MLE가 됩니다. 즉, **함수의 MLE는 MLE의 함수와 같습니다.**

**[EN]** One of the primary reasons statisticians favor Maximum Likelihood Estimation (MLE) is a tremendously powerful characteristic known as the **'Invariance Property'**.
If you have already found the MLE $\hat{\theta}$ for an unknown parameter $\theta$, you do not need to solve the differential equations all over again to find the MLE of a new function $h(\theta)$. You simply plug your existing $\hat{\theta}$ directly into the function $h$, and that instantly becomes the MLE for $h(\theta)$. In short, **the MLE of a function is the function of the MLE.**

* **통계적 주의사항 (Crucial Remark):** 이 편리한 불변성은 MLE만의 특권입니다. 앞서 배운 **불편성(Unbiasedness)**에는 이러한 성질이 적용되지 않습니다. 예를 들어, 표본 분산 $S^2$의 기댓값은 정확히 $\sigma^2$($E[S^2] = \sigma^2$)이지만, 여기에 루트를 씌운 기댓값 $E[\sqrt{S^2}]$은 $\sigma$와 같지 않습니다.

---

## 2. 불변성의 실전 적용 예제 (Practical Examples)

**[KR]** 함수 $h(\cdot)$가 일대일 대응(One-to-one) 함수일 때는 이 성질을 증명하기가 매우 쉽습니다. 설령 함수가 다소 복잡한 형태를 띠더라도 이 불변성의 원리는 일반적으로 굳건하게 성립합니다.

**[EN]** Proving this property is very straightforward when the function $h(\cdot)$ is strictly one-to-one. Even if the function takes on a nastier, more complex form, this principle of invariance generally holds remarkably strong.

### 예제 1: 정규 분포의 표준편차 추정 (Normal Distribution)
정규 분포 $N(\mu, \sigma^2)$에서 모분산 $\sigma^2$의 MLE는 앞선 단원에서 $\hat{\sigma}^2 = \frac{1}{n}\sum(X_i - \bar{X})^2$ 임을 유도했습니다.
그렇다면 분산이 아닌 **표준편차 $\sigma$의 MLE**는 어떻게 될까요? 불변성에 의해, 굳이 다시 계산할 필요 없이 기존 결과에 단순하게 제곱근(루트)만 씌워주면 됩니다.

$$
\hat{\sigma} = \sqrt{\hat{\sigma}^2} = \sqrt{\frac{1}{n}\sum_{i=1}^n (X_i - \bar{X})^2}
$$

### 예제 2: 베르누이 분포의 분산 추정 (Bernoulli Distribution)
베르누이 분포 $Bern(p)$에서 성공 확률 $p$의 MLE는 $\hat{p} = \bar{X}$ 였습니다.
베르누이 분포의 분산은 $p(1-p)$ 로 정의됩니다. 따라서 분산의 MLE를 구하고 싶다면, $p$ 자리에 $\bar{X}$를 대입하기만 하면 끝납니다.

$$
\text{MLE of } Var(X) = \hat{p}(1-\hat{p}) = \bar{X}(1-\bar{X})
$$

---

## 3. 보험 계리 공학에서의 활용 (Application in Actuarial Sciences)

**[KR]** 불변성은 특히 생명 보험이나 연금 모델을 다루는 보험 계리 공학(Actuarial Sciences)에서 매우 자주 활용됩니다. 수명이나 생존 기간을 지수 분포 $Exp(\lambda)$로 모델링해 봅시다.

**[EN]** This invariance property is exceptionally heavily utilized in Actuarial Sciences, which deals with life insurance and pension modeling. Let's model a lifespan or survival time using the exponential distribution $Exp(\lambda)$.

1. **생존 함수 (Survival Function):** 특정 시간 $x$ 이상 생존할 확률을 나타내는 생존 함수는 누적 분포 함수(CDF)의 반대인 $\bar{F}(x) = P(X > x) = 1 - F(x) = e^{-\lambda x}$ 로 정의됩니다.
2. **파라미터의 MLE:** 지수 분포에서 $\lambda$의 MLE는 $\hat{\lambda} = 1/\bar{X}$ 였습니다.
3. **생존 함수의 MLE:** 불변성을 이용하면, 우리가 원하는 특정 시점 $x$에서의 생존 확률에 대한 MLE를 아주 우아하게 즉시 도출해 낼 수 있습니다.

$$
\text{MLE of } \bar{F}(x) = e^{-\hat{\lambda} x} = e^{-x / \bar{X}}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-9 Invariance Property of MLEs-1" src="https://github.com/user-attachments/assets/b8fb0a0e-a262-42a5-a533-8b084a2f5958" />
  </div>
</details>
