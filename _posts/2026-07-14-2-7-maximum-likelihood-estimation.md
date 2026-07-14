---
title: "2-7 Maximum Likelihood Estimation"
date: 2026-07-14 17:45:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, estimation, mle, maximum-likelihood, likelihood-function]
math: true
---

## 1. 우도 함수와 최대 우도 추정법 (Likelihood Function & MLE)

[cite_start]**[KR]** 통계학에서 미지의 모수(Parameter, $\theta$)를 추정하는 가장 강력하고 대중적인 방법 중 하나가 바로 **최대 우도 추정법(Maximum Likelihood Estimation, MLE)**입니다[cite: 1262].
[cite_start]독립적이고 동일한 분포(i.i.d)를 따르는 표본 데이터 $X_1, \dots, X_n$ 이 주어졌을 때, 이 데이터들이 추출될 확률(또는 확률 밀도)을 모수 $\theta$에 대한 함수로 나타낸 것을 **우도 함수(Likelihood Function, $L(\theta)$)**라고 부릅니다[cite: 1260, 1261].
MLE의 핵심 아이디어는 직관적입니다. [cite_start]"우리가 현재 관측한 이 표본 데이터들이 나올 확률을 가장 극대화(Maximize)하는 $\theta$ 값이 바로 가장 그럴듯한(Most likely) 진짜 모수일 것이다"라는 논리입니다[cite: 1262, 1264].

[cite_start]**[EN]** In statistics, one of the most powerful and popular methods for estimating an unknown parameter ($\theta$) is **Maximum Likelihood Estimation (MLE)**[cite: 1262].
[cite_start]Given an independent and identically distributed (i.i.d) random sample $X_1, \dots, X_n$, the probability (or probability density) of observing this specific data, expressed as a function of the parameter $\theta$, is called the **Likelihood Function ($L(\theta)$)**[cite: 1260, 1261].
[cite_start]The core concept of MLE is intuitive: "The value of $\theta$ that maximizes the probability of observing our current sample data is the 'most likely' true parameter"[cite: 1262, 1264].

* **우도 함수 (Likelihood Function):**
  $$
  L(\theta) \equiv \prod_{i=1}^n f(x_i)
  $$
  [cite_start][cite: 1261]

---

## 2. 로그 변환 트릭 (The Log-Likelihood Trick)

[cite_start]**[KR]** 우도 함수 $L(\theta)$는 수많은 확률(또는 밀도)들의 '곱셈($\prod$)'으로 이루어져 있기 때문에, 이를 그대로 미분하여 최댓값을 찾는 것은 계산상 매우 복잡하고 고통스럽습니다[cite: 1268, 1269].
[cite_start]이를 해결하기 위해 양변에 **자연로그($\ln$)**를 취해주는 마법 같은 트릭을 사용합니다[cite: 1270, 1271, 1273]. [cite_start]로그 함수는 단조 증가(One-to-one, increasing) 함수이므로, 원래의 우도 함수 $L(\theta)$를 최대화하는 $\theta$ 값은 로그 우도 함수 $\ln(L(\theta))$ 역시 완벽하게 최대화합니다[cite: 1270, 1271]. [cite_start]로그를 씌우면 복잡한 곱셈이 다루기 쉬운 '덧셈($\sum$)'으로 쪼개져 미분 계산이 훨씬 수월해집니다[cite: 1272].

[cite_start]**[EN]** Because the likelihood function $L(\theta)$ consists of the 'product ($\prod$)' of numerous probabilities (or densities), directly differentiating it to find the maximum is computationally complex and tedious[cite: 1268, 1269].
[cite_start]To resolve this, we employ a magical trick: taking the **natural logarithm ($\ln$)** of both sides[cite: 1270, 1271, 1273]. [cite_start]Since the logarithmic function is strictly increasing (one-to-one), the exact same $\theta$ that maximizes $L(\theta)$ will also maximize the log-likelihood function $\ln(L(\theta))$[cite: 1270, 1271]. [cite_start]Applying the logarithm transforms the messy multiplication into manageable 'addition ($\sum$)', making differentiation significantly easier[cite: 1272].

---

## 3. 실전 예제: 지수 분포의 MLE (MLE for Exponential Distribution)

[cite_start]**[KR]** $X_1, \dots, X_n$ 이 지수 분포 $Exp(\lambda)$를 따른다고 할 때, 파라미터 $\lambda$의 MLE를 구해봅시다[cite: 1265].
1. [cite_start]**우도 함수 작성:** $L(\lambda) = \prod_{i=1}^n \lambda e^{-\lambda x_i} = \lambda^n \exp(-\lambda \sum_{i=1}^n x_i)$ [cite: 1267]
2. [cite_start]**로그 우도 함수:** $\ln(L(\lambda)) = n \ln(\lambda) - \lambda \sum_{i=1}^n x_i$ [cite: 1272]
3. [cite_start]**미분 및 최대화:** $\lambda$에 대해 미분한 뒤 $0$으로 설정합니다[cite: 1274].
   $$
   \frac{d}{d\lambda} \ln(L(\lambda)) = \frac{n}{\lambda} - \sum_{i=1}^n x_i = 0
   $$
   [cite_start][cite: 1274]
4. [cite_start]**결론:** 식을 정리하면 $\hat{\lambda} = \frac{1}{\bar{X}}$ 가 도출됩니다[cite: 1275]. (지수 분포의 기댓값이 $1/\lambda$ 임을 생각하면 매우 직관적이고 합리적인 결과입니다) [cite_start][cite: 1276, 1277].

[cite_start]**[EN]** Let's find the MLE for $\lambda$ when $X_1, \dots, X_n \sim Exp(\lambda)$[cite: 1265].
1. [cite_start]**Likelihood Function:** $L(\lambda) = \prod_{i=1}^n \lambda e^{-\lambda x_i} = \lambda^n \exp(-\lambda \sum_{i=1}^n x_i)$ [cite: 1267]
2. [cite_start]**Log-Likelihood:** $\ln(L(\lambda)) = n \ln(\lambda) - \lambda \sum_{i=1}^n x_i$ [cite: 1272]
3. [cite_start]**Differentiate & Maximize:** Take the derivative with respect to $\lambda$ and set it to $0$[cite: 1274].
   $$
   \frac{d}{d\lambda} \ln(L(\lambda)) = \frac{n}{\lambda} - \sum_{i=1}^n x_i = 0
   $$
   [cite_start][cite: 1274]
4. [cite_start]**Conclusion:** Solving for $\lambda$ yields $\hat{\lambda} = \frac{1}{\bar{X}}$[cite: 1275]. (This makes perfect sense since $E[X] = 1/\lambda$) [cite_start][cite: 1276, 1277].

---

## 4. 실전 예제: 베르누이 분포의 MLE (MLE for Bernoulli Distribution)

[cite_start]**[KR]** $X_1, \dots, X_n$ 이 베르누이 분포 $Bern(p)$를 따를 때, 성공 확률 $p$의 MLE를 구해봅시다[cite: 1282, 1283].
1. [cite_start]**우도 함수 작성:** 베르누이의 확률 질량 함수(pmf)는 $f(x) = p^x (1-p)^{1-x}$ 로 표현할 수 있으므로, 우도 함수는 다음과 같습니다[cite: 1287, 1288].
   $$
   L(p) = p^{\sum_{i=1}^n x_i} (1-p)^{n - \sum_{i=1}^n x_i}
   $$
   [cite_start][cite: 1290]
2. [cite_start]**로그 우도 함수:** $\ln(L(p)) = \sum_{i=1}^n x_i \ln(p) + \left(n - \sum_{i=1}^n x_i\right) \ln(1-p)$ [cite: 1291]
3. [cite_start]**미분 및 최대화:** $p$에 대해 미분하여 $0$으로 둡니다[cite: 1292].
   $$
   \frac{d}{dp} \ln(L(p)) = \frac{\sum x_i}{p} - \frac{n - \sum x_i}{1-p} = 0
   $$
   [cite_start][cite: 1292]
4. [cite_start]**결론:** 식을 정리하면 $\hat{p} = \bar{X}$ 가 나옵니다[cite: 1294]. (베르누이 시행의 기댓값이 $p$와 같다는 직관적 결과입니다) [cite_start][cite: 1295].

[cite_start]**[EN]** Let's find the MLE for the success probability $p$ when $X_1, \dots, X_n \sim Bern(p)$[cite: 1282, 1283].
1. [cite_start]**Likelihood Function:** Since the pmf is $f(x) = p^x (1-p)^{1-x}$, the likelihood function is: [cite: 1287, 1288]
   $$
   L(p) = p^{\sum_{i=1}^n x_i} (1-p)^{n - \sum_{i=1}^n x_i}
   $$
   [cite_start][cite: 1290]
2. [cite_start]**Log-Likelihood:** $\ln(L(p)) = \sum_{i=1}^n x_i \ln(p) + \left(n - \sum_{i=1}^n x_i\right) \ln(1-p)$ [cite: 1291]
3. [cite_start]**Differentiate & Maximize:** Differentiate w.r.t $p$ and set to $0$[cite: 1292].
   $$
   \frac{d}{dp} \ln(L(p)) = \frac{\sum x_i}{p} - \frac{n - \sum x_i}{1-p} = 0
   $$
   [cite_start][cite: 1292]
4. [cite_start]**Conclusion:** Solving for $p$ yields $\hat{p} = \bar{X}$[cite: 1294]. (This perfectly aligns with the intuition that $E[X] = p$) [cite_start][cite: 1295].

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-7 Maximum Likelihood Estimation-1" src="https://github.com/user-attachments/assets/14d43e83-9c30-4d6b-a6e7-fca04a437200" />
    <img width="1264" height="1635" alt="2-7 Maximum Likelihood Estimation-2" src="https://github.com/user-attachments/assets/e5e919d3-1be8-48ec-b0d0-33a6fd47ecb2" />
    <img width="1264" height="1635" alt="2-7 Maximum Likelihood Estimation-3" src="https://github.com/user-attachments/assets/e3c65b9f-7d50-4b50-9bfa-77de8c975edd" />
  </div>
</details>
