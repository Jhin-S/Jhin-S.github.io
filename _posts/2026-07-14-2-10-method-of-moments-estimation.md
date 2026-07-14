---
title: "2-10 Method of Moments Estimation"
date: 2026-07-14 22:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, estimation, method-of-moments, mom, sample-moment]
math: true
---

## 1. 적률법의 기본 개념 (Concept of Method of Moments)

**[KR]** 통계학에서 미지의 모수(Parameter)를 추정하는 직관적이고 고전적인 방법 중 하나가 바로 **적률법(Method of Moments, MoM)**입니다. 확률 변수 $X$의 $k$차 모적률(Population Moment)은 기댓값 $\mu_k = E[X^k]$ 로 정의됩니다. 이를 추정하기 위해, 우리가 수집한 독립적인 표본 데이터 $X_1, \dots, X_n$을 사용하여 $k$차 표본 적률(Sample Moment)인 $m_k = \frac{1}{n} \sum_{i=1}^n X_i^k$ 를 계산합니다. 
대수의 법칙(Law of Large Numbers)에 따라 표본의 크기 $n$이 커지면 표본 적률 $m_k$는 실제 모적률 $\mu_k$로 수렴하게 됩니다.

**[EN]** Another intuitive and classical approach to estimating unknown parameters in statistics is the **Method of Moments (MoM)**. The $k$-th population moment of a random variable $X$ is defined as the expected value $\mu_k = E[X^k]$. To estimate this, we compute the $k$-th sample moment $m_k = \frac{1}{n} \sum_{i=1}^n X_i^k$ using our independent sample data $X_1, \dots, X_n$. 
According to the Law of Large Numbers, as the sample size $n$ increases, the sample moment $m_k$ naturally converges to the true population moment $\mu_k$.

* **기초 적률 예시 (Basic Moments):**
  * 1차 적률 (평균): 모평균 $\mu_1 = \mu = E[X]$ 의 MoM 추정량은 표본 평균 $m_1 = \bar{X} = \frac{1}{n}\sum X_i$ 입니다.
  * 분산의 추정: 분산은 $Var(X) = \mu_2 - \mu_1^2$ 이므로, 이에 대한 MoM 추정량은 $m_2 - m_1^2 = \frac{1}{n}\sum X_i^2 - \bar{X}^2 = \frac{n-1}{n}S^2$ 이 됩니다.

---

## 2. 적률법의 일반적인 절차와 예제 (General Game Plan & Examples)

**[KR]** 적률법의 핵심 전략은 우리가 알고 싶은 미지의 파라미터를 실제 모적률($E[X]$, $E[X^2]$ 등)에 대한 수학적 방정식으로 표현한 뒤, 그 자리에 표본 적률($\bar{X}$, $S^2$ 등)을 그대로 치환하여 대입하는 것입니다.

**[EN]** The general game plan of MoM is to express the parameter of interest in terms of the true mathematical moments (like $E[X]$, $E[X^2]$), and then directly substitute these with the calculated sample moments (like $\bar{X}$, $S^2$).

### 예제 1: 푸아송 분포와 정규 분포 (Poisson and Normal Distributions)
* **푸아송 분포 $Pois(\lambda)$:** 푸아송 분포는 $\lambda = E[X]$ 이므로, $\lambda$의 MoM 추정량은 간단히 $\bar{X}$ 가 됩니다. 하지만 동시에 $\lambda = Var(X)$ 이기도 하므로, $\frac{n-1}{n}S^2$ (혹은 단순히 표본 분산 $S^2$) 역시 추정량이 될 수 있습니다. 여러 추정량이 나올 수 있는 경우, 계산이 더 간단한 형태를 선택하는 것이 일반적입니다.
* **정규 분포 $N(\mu, \sigma^2)$:** 평균 $\mu$와 분산 $\sigma^2$의 MoM 추정량은 각각 $\bar{X}$ 와 $\frac{n-1}{n}S^2$ (또는 $S^2$)가 됩니다. 이는 앞서 배운 최대 우도 추정량(MLE)과 완벽하게 동일한 결과입니다.

---

## 3. 심화 예제: 베타 분포의 파라미터 추정 (Advanced Example: Beta Distribution)

**[KR]** 복잡한 분포인 베타 분포 $Beta(a, b)$ 의 두 파라미터 $a, b$ 를 적률법으로 추정해 봅시다. 
베타 분포의 기댓값과 분산은 다음과 같이 주어집니다.

$$
E[X] = \frac{a}{a+b}, \quad Var(X) = \frac{ab}{(a+b)^2(a+b+1)}
$$

1. 평균 식을 $a$ 에 대해 정리하면 $a = \frac{b E[X]}{1 - E[X]}$ 가 되며, 이를 표본 데이터로 치환하면 $a = \frac{b\bar{X}}{1 - \bar{X}}$ 로 추정할 수 있습니다.
2. 이 $a$ 를 분산 식에 대입하고, 기댓값 자리에 $\bar{X}$, 분산 자리에 $S^2$ 를 넣고 방정식의 해를 구하면 다음과 같이 $b$ 의 MoM 추정량이 도출됩니다.

$$
b = \frac{(1-\bar{X})^2\bar{X}}{S^2} - 1 + \bar{X}
$$

**실제 데이터 적용:** $n=10$ 개의 관측치로부터 표본 평균 $\bar{X} = 0.67$, 표본 분산 $S^2 = 0.04971$ 을 얻었다면, 위 공식에 대입하여 즉각적으로 추정치 $b \approx 1.1377$ 과 $a \approx 2.310$ 을 쉽게 계산해 낼 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-10 Method of Moments Estimation-1" src="https://github.com/user-attachments/assets/4b00beff-fb36-4ba5-9b89-bfd93eb5bd1b" />
    <img width="1264" height="1635" alt="2-10 Method of Moments Estimation-2" src="https://github.com/user-attachments/assets/d18599df-d2a0-4953-bb11-5d5e7c35c666" />
    <img width="1264" height="1635" alt="2-10 Method of Moments Estimation-3" src="https://github.com/user-attachments/assets/79c29cfd-16a1-4a17-891d-85f77c43e3ed" />
  </div>
</details>
