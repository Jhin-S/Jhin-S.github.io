---
title: "1-6 Difference of Two Normal Means (Variance Unknown)"
date: 2026-07-17 10:01:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, normal-distribution, welch-approximation, confidence-interval, unequal-variances]
math: true
---

## 1. 모분산을 모르고 서로 다른 경우 (Unknown and Unequal Variances)

**[KR]** 통계학에서 두 정규 모집단의 평균 차이($\mu_x - \mu_y$)를 비교할 때 부딪히는 가장 현실적이고 까다로운 상황은, 두 집단의 실제 분산($\sigma_x^2, \sigma_y^2$)을 모를 뿐만 아니라 심지어 그 둘이 서로 다르다고 의심될 때입니다. 
앞선 장에서는 분산이 같다고 가정하여 두 표본 분산을 하나로 합치는 '합동 분산 추정량($S_p^2$)'을 사용했지만, 두 분산이 명백히 다를 때는 이 합동 분산을 절대로 사용할 수 없습니다. 

**[EN]** The most realistic and challenging scenario when comparing the difference in means ($\mu_x - \mu_y$) of two normal populations is when their true variances ($\sigma_x^2, \sigma_y^2$) are not only unknown but also suspected to be strictly unequal. 
In the previous lesson, we assumed equal variances and used the 'pooled variance estimator ($S_p^2$)', but when the variances are clearly different, using the pooled estimator is entirely invalid.

---

## 2. 웰치의 근사법 (Welch's Approximation Method)

**[KR]** 이 문제를 돌파하기 위해 통계학에서는 **'웰치의 근사법(Welch's approximation method)'**을 도입합니다. 합동 분산 대신 각 집단의 독립적인 표본 분산($S_x^2, S_y^2$)과 표본 크기($n, m$)를 그대로 살려 피벗(Pivot) 통계량 $t^*$를 구성합니다. 이 통계량은 완벽한 t-분포는 아니지만, 복잡한 자유도 $\nu$를 가지는 t-분포에 매우 가깝게 근사(Approximate)된다는 수학적 성질을 이용합니다.

**[EN]** To overcome this hurdle, statisticians employ **'Welch's approximation method'**. Instead of pooling, we construct a pivot statistic $t^*$ that directly utilizes the independent sample variances ($S_x^2, S_y^2$) and sample sizes ($n, m$) of each group. While this statistic doesn't follow a perfect t-distribution, it closely approximates a t-distribution with a complex degrees of freedom $\nu$.

* **피벗 통계량:**
  $$t^* \equiv \frac{\bar{X} - \bar{Y} - (\mu_x - \mu_y)}{\sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}} \approx t(\nu)$$
 

* **웰치의 자유도($\nu$) 계산 공식:**
  $$\nu \equiv \frac{\left(\frac{S_x^2}{n} + \frac{S_y^2}{m}\right)^2}{\frac{(S_x^2/n)^2}{n-1} + \frac{(S_y^2/m)^2}{m-1}}$$
 

---

## 3. 신뢰 구간 도출 (Confidence Interval Derivation)

**[KR]** 근사된 자유도 $\nu$를 바탕으로 대수적 정리를 거치면, 실무에서 아주 폭넓게 활용되는(Very wide application in practice) 강력한 근사 양측 신뢰 구간을 얻을 수 있습니다.

**[EN]** By applying the approximated degrees of freedom $\nu$ through standard algebraic manipulation, we obtain a powerful approximate two-sided confidence interval that has very wide application in real-world practice.

* **$100(1-\alpha)\%$ 양측 신뢰 구간:**
  $$\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, \nu} \sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}$$
 

---

## 4. 실전 예제 및 보수적 반내림 (Practice Example & Conservative Rounding)

**[KR]** 두 정규 모집단에서 데이터를 추출한 결과가 다음과 같다고 해봅시다.
* 집단 1: $n = 25$, 표본 평균 $\bar{X} = 100$, 표본 분산 $S_x^2 = 400$
* 집단 2: $m = 16$, 표본 평균 $\bar{Y} = 80$, 표본 분산 $S_y^2 = 100$

두 표본 분산이 $400$과 $100$으로 무려 4배나 차이가 나기 때문에, 분산이 같다는 가정은 즉시 기각되며 웰치의 근사법을 사용해야만 합니다.
복잡한 자유도 공식을 계산하면 $\nu \approx 39.90$ 이 도출됩니다. 이때 중요한 통계적 원칙은, 더 안전하고 **보수적인(Conservative)** 신뢰 구간을 만들기 위해 소수점이 어떻게 나오든 **무조건 내림(Round down)**하여 정수 자유도 $\nu = 39$로 맞춘다는 점입니다. 자유도가 작아질수록 t-분포의 꼬리가 두꺼워져 오차 범위가 약간 더 길고 넉넉해지기 때문입니다.

자유도가 $39$인 $95\%$ 신뢰 수준의 t-분위수는 $t_{0.025, 39} = 2.026$ 이며, 이를 대입하면 다음과 같습니다.

$$\mu_x - \mu_y \in 20 \pm 2.026 \sqrt{22.25} = 20 \pm 9.56$$


**[결론]** 두 모평균의 차이에 대한 95% 신뢰 구간은 $10.44 \le \mu_x - \mu_y \le 29.56$ 이 됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-6 Difference of Two Normal Means (Variance Unknown)-1" src="https://github.com/user-attachments/assets/3f73deb8-62a8-4d4b-8bc3-f1f1d15b4dba" />
    <img width="1264" height="1635" alt="1-6 Difference of Two Normal Means (Variance Unknown)-2" src="https://github.com/user-attachments/assets/b5af1020-caf4-4a58-8533-441982c4591a" />
  </div>
</details>
