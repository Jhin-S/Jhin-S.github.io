---
title: "1-5 Difference of Two Normal Means (unknown equal variance)"
date: 2026-07-17 09:57:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, normal-distribution, pooled-variance, t-distribution, confidence-interval]
math: true
---

## 1. 모분산을 모르지만 같다고 가정하는 상황 (Unknown but Equal Variances)

**[KR]** 두 개의 서로 다른 정규 모집단을 비교할 때, 현실에서는 각 집단의 실제 분산($\sigma_x^2, \sigma_y^2$)을 알지 못하는 경우가 대부분입니다. 이번 장에서는 두 모집단의 분산을 비록 정확한 수치로는 모르지만, 그 두 분산이 서로 동일하다($\sigma_x^2 = \sigma_y^2 = \sigma^2$)는 강력한 가정을 전제로 모평균의 차이($\mu_x - \mu_y$)에 대한 신뢰 구간을 구하는 방법을 다룹니다. 

**[EN]** When comparing two competing normal populations, it is standard in the real world to not know the true variances ($\sigma_x^2, \sigma_y^2$) of each group. In this section, we cover how to construct a confidence interval for the difference in population means ($\mu_x - \mu_y$) under the strong assumption that while the two variances are unknown, they are strictly equal to a common variance ($\sigma_x^2 = \sigma_y^2 = \sigma^2$).

---

## 2. 합동 분산 추정량과 t-분포 (Pooled Variance Estimator & t-distribution)

**[KR]** 두 집단에서 각각 표본 크기 $n$과 $m$을 추출하여 표본 분산 $S_x^2$와 $S_y^2$를 계산할 수 있습니다. 두 집단이 공통의 분산 $\sigma^2$을 공유한다고 가정했으므로, 이 두 표본 분산의 정보를 하나로 합치면 공통 분산에 대한 훨씬 더 훌륭하고 강력한 추정량을 얻을 수 있으며, 이를 **'합동 분산 추정량(Pooled Estimator for Variance, $S_p^2$)'**이라고 부릅니다.

**[EN]** We can extract sample sizes $n$ and $m$ from the two populations to calculate their respective sample variances, $S_x^2$ and $S_y^2$. Since we assumed both populations share a common variance $\sigma^2$, combining the information from both sample variances provides a much better and more robust estimator for the common variance, known as the **'Pooled Estimator for Variance ($S_p^2$)'**.

* **합동 분산 계산식:**
  $$ S_p^2 \equiv \frac{(n-1)S_x^2 + (m-1)S_y^2}{n+m-2} $$
 

독립적인 카이제곱 확률 변수들의 합의 성질에 의해, 이 합동 분산 추정량 $S_p^2$은 자유도가 $n+m-2$인 카이제곱 분포와 밀접한 수학적 관계를 가집니다. 이를 바탕으로 표준화 및 대수적 정리를 거치면, 우리가 원하는 피벗(Pivot) 통계량은 자유도 $n+m-2$의 t-분포를 따르게 됩니다.

* **피벗 통계량:**
  $$ \frac{\bar{X} - \bar{Y} - (\mu_x - \mu_y)}{S_p \sqrt{\frac{1}{n} + \frac{1}{m}}} \sim t(n+m-2) $$
 

---

## 3. 신뢰 구간 도출 공식 (Confidence Interval Formulas)

**[KR]** 위에서 구한 t-분포 피벗을 확률 부등식에 적용하여 정리하면, 두 모평균 차이에 대한 신뢰 구간을 다음과 같이 도출할 수 있습니다. (여기서 $t$는 자유도가 $n+m-2$인 t-분포의 분위수입니다.)

**[EN]** By applying the t-distribution pivot derived above to a probability inequality, we can establish the confidence intervals for the difference between the two population means as follows. (Here, $t$ represents the quantile of the t-distribution with $n+m-2$ degrees of freedom.)

* **$100(1-\alpha)\%$ 양측 신뢰 구간 (Two-sided CI):**
  $$ \mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, n+m-2} S_p \sqrt{\frac{1}{n} + \frac{1}{m}} $$
 
* **하한 단측 (One-sided Lower CI):**
  $$ \mu_x - \mu_y \ge \bar{X} - \bar{Y} - t_{\alpha, n+m-2} S_p \sqrt{\frac{1}{n} + \frac{1}{m}} $$
  
* **상한 단측 (One-sided Upper CI):**
  $$ \mu_x - \mu_y \le \bar{X} - \bar{Y} + t_{\alpha, n+m-2} S_p \sqrt{\frac{1}{n} + \frac{1}{m}} $$
 

---

## 4. 실전 예제: 두 집단의 평균 비교 (Practice Example)

**[KR]** 조지아 공대(GT, 집단 $x$) 학생들과 조지아 대학교(UGA, 집단 $y$) 학생들의 IQ 평균을 비교하는 상황을 가정해 봅시다. 두 집단의 IQ가 정규 분포를 따르며, 공통의 분산을 가진다고 가정합니다.
* **GT 데이터:** $n = 25$, 표본 평균 $\bar{X} = 120$, 표본 분산 $S_x^2 = 100$
* **UGA 데이터:** $m = 36$, 표본 평균 $\bar{Y} = 80$, 표본 분산 $S_y^2 = 95$

두 표본 분산값(100과 95)이 매우 비슷하게 나왔으므로 분산이 같다는 초기 가정은 꽤 합리적입니다. 합동 분산 추정량 $S_p^2$를 계산하면 다음과 같습니다.

$$ S_p^2 = \frac{(24 \times 100) + (35 \times 95)}{59} = 97.03 $$


이를 공식에 대입하여 95% 양측 신뢰 구간을 구하면 다음과 같이 계산됩니다.

$$ \mu_x - \mu_y \in 120 - 80 \pm 2.00 \sqrt{97.03} \sqrt{0.0678} = 40 \pm 5.13 $$


**[결론]** 모평균의 차이($\mu_x - \mu_y$)에 대한 95% 신뢰 구간은 $34.87 \le \mu_x - \mu_y \le 45.13$ 입니다. 이 구간 내에 $0$이 포함되어 있지 않으므로(심지어 0과 매우 멀리 떨어져 있으므로), 우리는 통계적으로 GT 학생들의 IQ가 UGA 학생들보다 확실히 더 높다고 결론 내릴 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-5 Difference of Two Normal Means (unknown equal variance)-1" src="https://github.com/user-attachments/assets/34fc61b3-1e5d-4df9-9a8f-808a1e741379" />
    <img width="1264" height="1635" alt="1-5 Difference of Two Normal Means (unknown equal variance)-2" src="https://github.com/user-attachments/assets/5bf49957-7ed3-4d53-82c7-9bfebda8e667" />
    <img width="1264" height="1635" alt="1-5 Difference of Two Normal Means (unknown equal variance)-3" src="https://github.com/user-attachments/assets/c326a84f-07fe-47a5-811c-f3e2729ac8bf" />
  </div>
</details>
