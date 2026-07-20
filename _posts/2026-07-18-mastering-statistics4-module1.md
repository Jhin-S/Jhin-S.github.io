---
title: "Mastering Statistics4 Module1"
date: 2026-07-20 12:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, confidence-interval, normal-distribution, t-distribution, f-distribution, chi-squared, bernoulli]
math: true
---

이번에는 모듈1(신뢰구간)의 모든 내용을 정리하며 복습해보았습니다. 확률과 통계 과정은 개념도 많고 미적분학, 선형대수학과는 다른 방향성으로 논리가 전개되기에 확실히 어려운 것 같습니다.
다만, 어려운 만큼 이해했을 때 재미있고 큰 성취감과 뿌듯함이 몰려옵니다. 이번 포스팅은 손으로 적은 페이지 수가 17페이지나 되네요. 꾸준히 실력을 증진해나가겠습니다. :)

## 1-1. 신뢰 구간의 도입 (Introduction to Confidence Intervals)

**[KR]** 통계적 추론에서 미지의 모수(Parameter, $\theta$)를 단 하나의 점(Point)으로 추정하는 것에는 필연적인 오차가 따릅니다. 이를 보완하기 위해 통계학에서는 모수를 특정 확률로 품고 있을 것이라 기대되는 '구간(Interval)'을 제시합니다. 
모수 $\theta$에 대한 $100(1-\alpha)\%$ 신뢰 구간은 아래의 확률 부등식을 만족하는 확률 변수 하한($L$)과 상한($U$)으로 정의됩니다. 

**[EN]** In statistical inference, estimating an unknown parameter ($\theta$) with a single point inevitably involves error. To compensate for this, statistics provides an 'interval' that is expected to contain the parameter with a certain probability. 
A $100(1-\alpha)\%$ confidence interval for a parameter $\theta$ is defined by a lower bound ($L$) and an upper bound ($U$) of random variables that satisfy the following probability inequality.

$$ P(L \le \theta \le U) = 1 - \alpha $$

**[KR]** 여기서 $1-\alpha$를 **신뢰 계수(Confidence Coefficient)**라고 부르며, 이는 우리가 샘플링을 반복했을 때 실제 모수가 이 구간 사이에 존재할 확률을 의미합니다.

**[EN]** Here, $1-\alpha$ is called the **Confidence Coefficient**, which represents the probability that the actual parameter exists within this interval if we were to repeat the sampling process.

---

## 1-2. 정규 분포의 평균 추정: 분산을 아는 경우 (Normal Mean, Variance Known)

**[KR]** 알려지지 않은 모평균 $\mu$를 추정하기 위해 표본 평균 $\bar{X}$를 사용합니다. 모집단의 분산 $\sigma^2$을 알고 있다고 가정($X_i \sim N(\mu, \sigma^2)$)하면, 표본 평균을 표준화하여 완벽한 표준 정규 분포를 따르는 **피벗(Pivot)** 통계량 $Z$를 유도할 수 있습니다.

**[EN]** To estimate an unknown population mean $\mu$, we use the sample mean $\bar{X}$. Assuming the population variance $\sigma^2$ is known ($X_i \sim N(\mu, \sigma^2)$), we can standardize the sample mean to derive a **Pivot** statistic $Z$ that perfectly follows a standard normal distribution.

$$ Z \equiv \frac{\bar{X} - \mu}{\sqrt{\sigma^2/n}} \sim N(0, 1) $$

**[KR]** 이 피벗을 활용하여 확률 부등식을 전개하면 $\mu$에 대한 양측 신뢰 구간을 얻을 수 있습니다. 
* **양측 신뢰 구간:** $\bar{X} - z_{\alpha/2}\sqrt{\frac{\sigma^2}{n}} \le \mu \le \bar{X} + z_{\alpha/2}\sqrt{\frac{\sigma^2}{n}}$
* **오차 한계(반폭, $H$)와 표본 크기:** $H = z_{\alpha/2}\sqrt{\sigma^2/n}$ 이며, 원하는 오차 $\epsilon$을 맞추기 위한 최소 표본 크기는 $n \ge \left(\frac{\sigma z_{\alpha/2}}{\epsilon}\right)^2$ 로 계산됩니다. 더 많은 관측치를 모을수록 구간은 짧아지고 정밀해집니다.

**[EN]** By expanding the probability inequality using this pivot, we can obtain the two-sided confidence interval for $\mu$.
* **Two-sided confidence interval:** $\bar{X} - z_{\alpha/2}\sqrt{\frac{\sigma^2}{n}} \le \mu \le \bar{X} + z_{\alpha/2}\sqrt{\frac{\sigma^2}{n}}$
* **Margin of error (half-width, $H$) and Sample Size:** $H = z_{\alpha/2}\sqrt{\sigma^2/n}$, and the minimum sample size required to meet a desired error $\epsilon$ is calculated as $n \ge \left(\frac{\sigma z_{\alpha/2}}{\epsilon}\right)^2$. The more observations collected, the shorter and more precise the interval becomes.

---

## 1-3. 두 정규 평균의 차이: 분산을 아는 경우 (Difference of Two Normal Means)

**[KR]** 서로 경쟁하는 두 집단(프로세스)의 평균 차이($\mu_x - \mu_y$)를 비교하기 위한 세팅입니다. 두 집단 모두 정규 분포를 따르고 각각의 분산($\sigma_x^2, \sigma_y^2$)을 안다고 가정할 때, 두 표본 평균의 차이 $\bar{X} - \bar{Y}$ 역시 정규 분포를 따릅니다.

**[EN]** This is a setup for comparing the difference in means ($\mu_x - \mu_y$) between two competing groups (or processes). Assuming both groups follow a normal distribution and their respective variances ($\sigma_x^2, \sigma_y^2$) are known, the difference between the two sample means $\bar{X} - \bar{Y}$ also follows a normal distribution.

$$ Z = \frac{\bar{X} - \bar{Y} - (\mu_x - \mu_y)}{\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}} \sim N(0, 1) $$

* **[KR] 양측 신뢰 구간:** $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm z_{\alpha/2}\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}$
* **[EN] Two-sided confidence interval:** $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm z_{\alpha/2}\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}$
* **[KR]** 두 집단의 표본 크기가 같을 때($n=m$), 목표 오차 $\epsilon$을 달성하기 위한 표본 크기는 $n \ge \frac{z_{\alpha/2}^2(\sigma_x^2 + \sigma_y^2)}{\epsilon^2}$ 입니다.
* **[EN]** When the sample sizes of the two groups are equal ($n=m$), the sample size required to achieve the target error $\epsilon$ is $n \ge \frac{z_{\alpha/2}^2(\sigma_x^2 + \sigma_y^2)}{\epsilon^2}$.

---

## 1-4. 정규 분포의 평균 추정: 분산을 모르는 경우 (Normal Mean, Variance Unknown)

**[KR]** 현실적으로 모분산 $\sigma^2$을 아는 경우는 없습니다. 따라서 이를 표본 분산 $S^2$으로 대체해야 합니다. 통계학의 핵심 정리들에 따르면 표본 평균 $\bar{X}$와 분산 $S^2$은 독립이며, 카이제곱 분포의 가법성을 이용한 대수적 증명을 통해 $S^2 \sim \frac{\sigma^2 \chi^2(n-1)}{n-1}$ 임을 유도할 수 있습니다. 
알 수 없는 $\sigma^2$을 식에서 완전히 소거하기 위해 표준 정규 변수 $Z$를 자유도가 $n-1$인 카이제곱 변수 $V$로 나누면 **t-분포**가 탄생합니다.

**[EN]** In reality, the population variance $\sigma^2$ is never known. Therefore, it must be replaced by the sample variance $S^2$. According to key theorems in statistics, the sample mean $\bar{X}$ and variance $S^2$ are independent, and through an algebraic proof using the additive property of the chi-squared distribution, we can derive that $S^2 \sim \frac{\sigma^2 \chi^2(n-1)}{n-1}$. 
To completely eliminate the unknown $\sigma^2$ from the equation, dividing the standard normal variable $Z$ by a chi-squared variable $V$ with $n-1$ degrees of freedom gives rise to the **t-distribution**.

$$ \frac{\bar{X} - \mu}{S/\sqrt{n}} \sim t(n-1) $$

* **[KR] 양측 신뢰 구간:** $\mu \in \bar{X} \pm t_{\alpha/2, n-1} \sqrt{\frac{S^2}{n}}$
* **[EN] Two-sided confidence interval:** $\mu \in \bar{X} \pm t_{\alpha/2, n-1} \sqrt{\frac{S^2}{n}}$

---

## 1-5. 두 정규 평균의 차이: 분산은 모르지만 같은 경우 (Unknown Equal Variance)

**[KR]** 두 모집단의 분산을 모르지만 동일하다($\sigma_x^2 = \sigma_y^2 = \sigma^2$)고 가정하는 상황입니다. 두 집단의 표본 분산을 합쳐 공통 분산을 더 정확히 추정하는 **합동 분산 추정량(Pooled Estimator, $S_p^2$)**을 사용합니다. 

**[EN]** This is a situation where the variances of the two populations are unknown but assumed to be equal ($\sigma_x^2 = \sigma_y^2 = \sigma^2$). We use a **Pooled Estimator ($S_p^2$)**, which combines the sample variances of the two groups to estimate the common variance more accurately.

$$ S_p^2 = \frac{(n-1)S_x^2 + (m-1)S_y^2}{n+m-2} $$

**[KR]** 이 식은 단순 평균이 아닌 '가중 평균(Weighted Average)'입니다. 각 집단의 자유도($n-1$, $m-1$)를 곱해 편차 제곱합을 구하고, 이를 총 자유도($n+m-2$)로 나누어 데이터가 더 많은 쪽에 가중치를 부여합니다.

**[EN]** This formula is not a simple average but a 'Weighted Average'. We multiply by the degrees of freedom ($n-1$, $m-1$) of each group to find the sum of squared deviations, and then divide by the total degrees of freedom ($n+m-2$) to give more weight to the side with more data.

* **[KR] 피벗 및 신뢰 구간:** 피벗은 $t(n+m-2)$ 분포를 따르며, 구간은 $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, n+m-2} S_p \sqrt{\frac{1}{n} + \frac{1}{m}}$ 로 계산됩니다.
* **[EN] Pivot and Confidence Interval:** The pivot follows a $t(n+m-2)$ distribution, and the interval is calculated as $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, n+m-2} S_p \sqrt{\frac{1}{n} + \frac{1}{m}}$.

---

## 1-6. 두 정규 평균의 차이: 분산이 다를 경우 (Variance Unknown and Unequal)

**[KR]** 두 모집단의 분산이 확연히 다르다면 합동 분산을 쓸 수 없으며, **웰치의 근사 방법(Welch's Approximation)**을 동원해야 합니다. $V = \frac{S_x^2}{n} + \frac{S_y^2}{m}$ 라는 새로운 확률 변수를 정의하고, 적률법(MoM)을 통해 카이제곱 분포와 모멘트를 매칭시켜 복잡한 근사 자유도 $\nu$를 유도해냅니다.

**[EN]** If the variances of the two populations are significantly different, the pooled variance cannot be used, and we must employ **Welch's Approximation**. By defining a new random variable $V = \frac{S_x^2}{n} + \frac{S_y^2}{m}$ and matching moments with the chi-squared distribution using the Method of Moments (MoM), we derive a complex approximate degree of freedom $\nu$.

$$ \nu \approx \frac{\left(\frac{S_x^2}{n} + \frac{S_y^2}{m}\right)^2}{\frac{(S_x^2/n)^2}{n-1} + \frac{(S_y^2/m)^2}{m-1}} $$

* **[KR] 신뢰 구간:** 근사된 자유도 $\nu$ (보수적으로 내림하여 정수화)를 가진 $t$-분포를 사용하여 $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, \nu} \sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}$ 의 구간을 얻습니다.
* **[EN] Confidence Interval:** Using a $t$-distribution with the approximated degree of freedom $\nu$ (conservatively rounded down to an integer), we obtain the interval $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, \nu} \sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}$.

---

## 1-7. 쌍체 표본의 평균 차이 (Difference of Paired Normal Means)

**[KR]** 두 모집단에서 데이터를 독립적으로 뽑지 않고 쌍(Pair)으로 수집하면, 외부 노이즈를 제거하여 차이를 더 정밀하게 포착할 수 있습니다. 쌍과 쌍 사이는 독립이지만, 쌍 내부의 $X_i$와 $Y_i$는 독립이 아닐 수 있습니다.
관측치의 차이 $D_i = X_i - Y_i$ 를 구하면, 문제는 단일 정규 분포의 평균과 분산을 모르는 케이스(1-4장)로 완벽히 단순화됩니다.

**[EN]** If data from two populations are collected in pairs rather than independently, external noise can be removed to capture the difference more precisely. While pairs are independent of each other, $X_i$ and $Y_i$ within the same pair may not be independent.
By calculating the difference in observations $D_i = X_i - Y_i$, the problem is perfectly simplified to the case of a single normal distribution with unknown mean and variance (Chapter 1-4).

* **[KR] 양측 신뢰 구간:** $\mu_d = \mu_x - \mu_y \in \bar{D} \pm t_{\alpha/2, n-1} \sqrt{\frac{S_d^2}{n}}$
* **[EN] Two-sided confidence interval:** $\mu_d = \mu_x - \mu_y \in \bar{D} \pm t_{\alpha/2, n-1} \sqrt{\frac{S_d^2}{n}}$

---

## 1-8. 정규 분포의 분산 추정 (Normal Variance)

**[KR]** 시스템의 변동성(Variability)을 파악하기 위해 모분산 $\sigma^2$에 대한 신뢰 구간을 구합니다. 카이제곱 분포의 성질 $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1)$ 을 이용합니다.

**[EN]** To understand the variability of a system, we find the confidence interval for the population variance $\sigma^2$. We utilize the property of the chi-squared distribution: $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1)$.

* **[KR] 양측 신뢰 구간:** 확률 부등식을 뒤집고 역수를 취하여 유도합니다.
* **[EN] Two-sided confidence interval:** Derived by flipping the probability inequality and taking the reciprocal.

$$ \sigma^2 \in \left[ \frac{(n-1)S^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)S^2}{\chi^2_{1-\alpha/2, n-1}} \right] $$

**[KR]** 이 구간은 미지의 $\mu$를 포함하지 않으며, 표본 분산 $S^2$에 정비례합니다.
**[EN]** This interval does not contain the unknown $\mu$ and is directly proportional to the sample variance $S^2$.

---

## 1-9. 두 정규 분포의 분산 비율 (Ratio of Variance of Two Normals)

**[KR]** 두 집단 중 어느 쪽의 변동성이 더 큰지 확인하기 위해 분산의 비율 $\sigma_x^2 / \sigma_y^2$ 을 비교합니다. 각각의 카이제곱 확률 변수를 자유도로 나눈 비율은 **F-분포**를 따릅니다.

**[EN]** To determine which of the two groups has greater variability, we compare the ratio of their variances, $\sigma_x^2 / \sigma_y^2$. The ratio of their respective chi-squared random variables divided by their degrees of freedom follows an **F-distribution**.

$$ \frac{S_y^2 / \sigma_y^2}{S_x^2 / \sigma_x^2} \sim F(m-1, n-1) $$

* **[KR] 양측 신뢰 구간:** F-분포의 대칭성과 역수 성질을 이용해 부등식을 정리하면 다음을 얻습니다.
* **[EN] Two-sided confidence interval:** By utilizing the symmetry and reciprocal properties of the F-distribution to rearrange the inequality, we obtain the following:

$$ \frac{\sigma_x^2}{\sigma_y^2} \in \left[ \frac{S_x^2}{S_y^2} \frac{1}{F_{\alpha/2, m-1, n-1}}, \frac{S_x^2}{S_y^2} F_{\alpha/2, n-1, m-1} \right] $$

---

## 1-10. 베르누이 비율의 추정 (Bernoulli Proportion)

**[KR]** 성공 아니면 실패만 존재하는 베르누이 분포 $Bern(p)$에서 진짜 성공 확률 $p$를 추정합니다. 표본 크기 $n$이 충분히 크면 중심극한정리(CLT)에 의해 정규 분포로 근사할 수 있습니다. 
미지의 분산 $pq/n$을 최대우도추정량(MLE)인 $\bar{X}(1-\bar{X})/n$ 으로 과감히 대체(Plug-in)하여 피벗을 만듭니다.

**[EN]** We estimate the true success probability $p$ in a Bernoulli distribution $Bern(p)$, where only success or failure exists. If the sample size $n$ is sufficiently large, it can be approximated to a normal distribution by the Central Limit Theorem (CLT). 
We boldly substitute (plug-in) the unknown variance $pq/n$ with its Maximum Likelihood Estimator (MLE), $\bar{X}(1-\bar{X})/n$, to create a pivot.

* **[KR] 양측 신뢰 구간:** $p \in \bar{X} \pm z_{\alpha/2}\sqrt{\frac{\bar{X}(1-\bar{X})}{n}}$
* **[EN] Two-sided confidence interval:** $p \in \bar{X} \pm z_{\alpha/2}\sqrt{\frac{\bar{X}(1-\bar{X})}{n}}$
* **[KR] 표본 크기 결정:** 오차 한계를 통제하기 위한 $n$을 구할 때, $p$를 모르므로 수학적 최댓값인 $1/4$를 대입하는 **보수적 방법($n \ge \frac{z_{\alpha/2}^2}{4\epsilon^2}$)**과 사전 연구 추정치 $\hat{p}$를 활용하는 방법이 있습니다.
* **[EN] Determining Sample Size:** When calculating $n$ to control the margin of error, since $p$ is unknown, there is a **conservative method** of substituting the mathematical maximum value of $1/4$ ($n \ge \frac{z_{\alpha/2}^2}{4\epsilon^2}$), as well as a method utilizing a prior study estimate $\hat{p}$.
* **[KR] 두 모비율 차이의 구간:** 두 집단의 차이 역시 $p_x - p_y \in (\bar{X} - \bar{Y}) \pm z_{\alpha/2}\sqrt{\frac{\bar{X}(1-\bar{X})}{n} + \frac{\bar{Y}(1-\bar{Y})}{m}}$ 으로 확장할 수 있습니다.
* **[EN] Interval for the difference of two population proportions:** The difference between two groups can also be expanded to $p_x - p_y \in (\bar{X} - \bar{Y}) \pm z_{\alpha/2}\sqrt{\frac{\bar{X}(1-\bar{X})}{n} + \frac{\bar{Y}(1-\bar{Y})}{m}}$.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-01" src="https://github.com/user-attachments/assets/bc76cdc2-ac83-44ef-9de1-00e801e5a81c" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-02" src="https://github.com/user-attachments/assets/8b9241d6-2ec7-423c-8c9c-88532d3ae28a" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-03" src="https://github.com/user-attachments/assets/b82ff6a5-9586-4f36-a25b-32b1783d8a9e" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-04" src="https://github.com/user-attachments/assets/4a02daa8-b629-4ce2-9bd6-452f7da4332c" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-05" src="https://github.com/user-attachments/assets/e2bef5bf-d304-487f-8325-6e42b7e2b58c" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-06" src="https://github.com/user-attachments/assets/0f451f70-ead8-4315-a138-240a534fd8a3" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-07" src="https://github.com/user-attachments/assets/00e85f8d-273b-4ad4-9c6f-a689c1cf5bb9" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-08" src="https://github.com/user-attachments/assets/7715f2d1-64a5-4360-8a1e-187b967bac83" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-09" src="https://github.com/user-attachments/assets/9f546ec7-d86c-4551-af59-2c408e37b0d8" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-10" src="https://github.com/user-attachments/assets/fa5056e8-2a06-4193-8a9e-39ee0bfbc1ff" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-11" src="https://github.com/user-attachments/assets/aaa775c8-0acf-4b8f-8ece-db6be8ff9325" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-12" src="https://github.com/user-attachments/assets/7dcbb8b8-fbc1-4464-bf73-9256281317cd" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-13" src="https://github.com/user-attachments/assets/e993eedc-2405-4e03-8a8f-7b978b312d7f" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-14" src="https://github.com/user-attachments/assets/f2fc4158-727f-4f23-8f8f-9c6ef77cc0ec" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-15" src="https://github.com/user-attachments/assets/6b493b63-a9a7-4970-9357-3bef3d96b246" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-16" src="https://github.com/user-attachments/assets/be2154d2-bd3e-41ea-9f03-7ce724bff60f" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-17" src="https://github.com/user-attachments/assets/64c51536-0e2b-4c74-b4b5-b8c8a2c77f2f" />
  </div>
</details>
