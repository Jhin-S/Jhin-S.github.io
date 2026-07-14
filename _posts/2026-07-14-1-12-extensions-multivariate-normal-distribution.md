---
title: "1-12 Extensions - Multivariate Normal Distribution"
date: 2026-07-14 15:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, multivariate-normal, bivariate-normal, conditional-distribution, covariance-matrix]
math: true
---

## 1. 이변량 정규 분포 (Bivariate Normal Distribution)

**[KR]** 서로 연관성을 가지는 두 개의 확률 변수 $X$와 $Y$가 각각 정규 분포를 따를 때, 이 두 변수를 2차원 공간에서 동시에 모델링하는 것을 **이변량 정규 분포(Bivariate Normal Distribution)**라고 합니다. 사람의 '키'와 '몸무게'처럼 양의 상관관계(Correlation)를 가지는 데이터들을 동시에 분석할 때 주로 사용됩니다. 결합 확률 밀도 함수(Joint PDF)는 두 변수 간의 상관계수 $\rho$를 포함한 매우 복잡한 지수 함수 형태를 띠게 됩니다.

**[EN]** When two correlated random variables $X$ and $Y$ individually follow a normal distribution, modeling them simultaneously in a 2D space creates the **Bivariate Normal Distribution**. It is heavily used to analyze datasets with inherent correlations, such as a person's 'height' and 'weight'. The joint probability density function (Joint PDF) takes on a highly complex exponential form that incorporates the correlation coefficient $\rho$.

---

## 2. 조건부 정규 분포의 마법 (Conditional Distribution)

**[KR]** 이변량 정규 분포가 가지는 가장 매력적이고 강력한 수학적 성질은, **한 변수의 값이 확정되었을 때 나머지 한 변수의 조건부 분포 역시 완벽한 정규 분포를 유지**한다는 것입니다. 즉, $X$에 대한 추가 정보가 들어오면 기존 $Y$의 분포(평균과 분산)를 아주 정교하게 업데이트(Update)할 수 있습니다. 후일 회귀 분석(Regression)을 다룰 때 뼈대가 되는 아주 중요한 원리입니다.

**[EN]** The most fascinating and powerful mathematical property of the bivariate normal distribution is that **the conditional distribution of one variable, given the exact value of the other, remains a perfect normal distribution**. In other words, observing the value of $X$ allows us to precisely update the distribution (mean and variance) of $Y$. This principle forms the core foundation for Regression analysis later on.

* **조건부 평균 (Updated Mean):** 기존 $Y$의 평균에, $X$가 자신의 평균에서 벗어난 정도를 상관계수를 반영하여 보정해 줍니다.
  
$$
E[Y \mid X=x] = \mu_Y + \rho \left(\frac{\sigma_Y}{\sigma_X}\right) (x - \mu_X)
$$

* **조건부 분산 (Updated Variance):** $X$를 알게 되면서 불확실성이 줄어들기 때문에, 분산은 항상 기존보다 작아집니다.
  
$$
Var(Y \mid X=x) = \sigma_Y^2 (1 - \rho^2)
$$

---

## 3. 실전 응용 예제 (Practice Example: SAT & GPA)

**[KR]** 어떤 대학교 학생들의 결합된 SAT 점수($X$)와 1학년 평균 학점($Y$)을 분석한 결과 다음과 같은 통계량을 얻었다고 가정해 봅시다. 
(SAT 평균 $\mu_X = 1300$, 분산 $\sigma_X^2 = 6400$ / 학점 평균 $\mu_Y = 2.3$, 분산 $\sigma_Y^2 = 0.25$ / 상관계수 $\rho = 0.6$)
이때 SAT 점수가 900점인 학생이 학점을 2.0 이상 받을 확률은 얼마일까요?

**[EN]** Suppose a university analyzes its students' combined SAT scores ($X$) and freshman GPA ($Y$) and discovers the following parameters: 
($\mu_X = 1300, \sigma_X^2 = 6400$ / $\mu_Y = 2.3, \sigma_Y^2 = 0.25$ / $\rho = 0.6$). 
What is the probability that a student who scored 900 on the SAT will achieve a GPA of 2.0 or higher?

**[Step 1] 업데이트된 평균 계산:**
$$
E[Y \mid X=900] = 2.3 + (0.6)\left(\sqrt{\frac{0.25}{6400}}\right)(900 - 1300) = 0.8
$$
(이 학생의 기대 학점은 0.8점으로 예측됩니다.)

**[Step 2] 업데이트된 분산 계산:**
$$
Var(Y \mid X=900) = 0.25(1 - 0.6^2) = 0.16
$$

**[Step 3] 확률 계산:** 이 학생의 예상 학점 분포는 $Y \mid X=900 \sim N(0.8, 0.16)$ 을 따릅니다. 이를 표준화하여 확률을 구합니다.
$$
P(Y \ge 2.0 \mid X=900) = P\left(Z \ge \frac{2.0 - 0.8}{\sqrt{0.16}}\right) = P(Z \ge 3) = 1 - \Phi(3) = 0.0013
$$
결과적으로 이 학생이 2.0 이상의 좋은 학점을 받을 확률은 약 0.13%로 매우 낮습니다.

---

## 4. 다변량 정규 분포 (Multivariate Normal Distribution)

**[KR]** 2차원(이변량)을 넘어 $k$개의 확률 변수들을 한꺼번에 묶어서 다루는 벡터 공간으로 확장하면 **다변량 정규 분포(Multivariate Normal Distribution)**가 탄생합니다. 기존 스칼라 형태의 평균은 $k$차원의 '평균 벡터(Mean Vector, $\boldsymbol{\mu}$)'로, 하나의 분산은 변수들 간의 모든 분산과 공분산(Covariance)을 담고 있는 거대한 '공분산 행렬(Covariance Matrix, $\Sigma$)'로 진화하게 됩니다.

**[EN]** Expanding beyond 2D into a vector space handling $k$ random variables simultaneously gives rise to the **Multivariate Normal Distribution**. The traditional scalar mean evolves into a $k$-dimensional 'Mean Vector ($\boldsymbol{\mu}$)', and the single variance is replaced by a massive 'Covariance Matrix ($\Sigma$)' that elegantly stores all individual variances and cross-covariances among the variables.

* **표기법 (Notation):** $\mathbf{X} \sim N_k(\boldsymbol{\mu}, \Sigma)$
* **결합 확률 밀도 함수 (Joint PDF):** 행렬의 행렬식($|\Sigma|$)과 역행렬($\Sigma^{-1}$)을 사용하여 지수 함수 형태로 나타냅니다.
  
$$
f(\mathbf{x}) = \frac{1}{(2\pi)^{k/2} |\Sigma|^{1/2}} \exp\left\{ -\frac{1}{2} (\mathbf{x} - \boldsymbol{\mu})^T \Sigma^{-1} (\mathbf{x} - \boldsymbol{\mu}) \right\}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-12 Extensions - Multivariate Normal Distribution-1" src="https://github.com/user-attachments/assets/e27951e1-2472-4ebc-ba97-831a15aab0b9" />
    <img width="1264" height="1635" alt="1-12 Extensions - Multivariate Normal Distribution-2" src="https://github.com/user-attachments/assets/805b4ec4-a868-40a5-bbe4-658daa453383" />
    <img width="1264" height="1635" alt="1-12 Extensions - Multivariate Normal Distribution-3" src="https://github.com/user-attachments/assets/d12345cf-dbd7-4d74-bff2-34063656be3a" />
  </div>
</details>
