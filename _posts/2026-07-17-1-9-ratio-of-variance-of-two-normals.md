---
title: "1-9 Ratio of Variance of Two Normals"
date: 2026-07-17 10:11:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, normal-distribution, variance-ratio, f-distribution, confidence-interval]
math: true
---

## 1. 두 집단의 변동성 비교 (Comparing Variability of Two Distributions)

**[KR]** 두 정규 모집단 중 어느 쪽의 데이터가 더 넓게 퍼져 있는지, 즉 '변동성(Variability)'을 비교하고 싶을 때는 두 모분산의 차이가 아닌 **비율(Ratio, $\sigma_x^2 / \sigma_y^2$)**에 대한 신뢰 구간을 구해야 합니다. 
각 집단의 모평균과 모분산을 모두 알지 못하는 독립적인 두 표본 $X_1, \dots, X_n \sim Nor(\mu_x, \sigma_x^2)$ 와 $Y_1, \dots, Y_m \sim Nor(\mu_y, \sigma_y^2)$ 가 있다고 가정해 봅시다. 

**[EN]** When we want to determine which of two normal distributions has more variability (i.e., which data is more spread out), we must construct a confidence interval for the **ratio ($\sigma_x^2 / \sigma_y^2$)** of the two population variances, rather than their difference. 
Suppose we have two independent samples, $X_1, \dots, X_n \sim Nor(\mu_x, \sigma_x^2)$ and $Y_1, \dots, Y_m \sim Nor(\mu_y, \sigma_y^2)$, where all population means and variances are unknown.

---

## 2. F-분포와 피벗 통계량 (F-Distribution and Pivot Quantity)

**[KR]** 앞서 배웠듯 표본 분산 $S_x^2$ 와 $S_y^2$ 는 각각 자유도가 $n-1$ 과 $m-1$ 인 카이제곱 분포와 관련이 있습니다. 두 카이제곱 확률 변수를 각각의 자유도로 나눈 뒤 비율을 구하면 **F-분포(F-distribution)**를 따르게 됩니다. 이를 이용해 미지의 분산 비율 $\sigma_x^2 / \sigma_y^2$ 을 포함하는 완벽한 피벗(Pivot) 통계량을 만들어 낼 수 있습니다.

**[EN]** As learned previously, the sample variances $S_x^2$ and $S_y^2$ are associated with chi-squared distributions with $n-1$ and $m-1$ degrees of freedom, respectively. By taking the ratio of these two chi-squared variables divided by their respective degrees of freedom, we obtain a statistic that follows an **F-distribution**. This allows us to construct a perfect pivot quantity containing the unknown variance ratio $\sigma_x^2 / \sigma_y^2$.

* **피벗 통계량 도출:**
$$
\frac{S_y^2 / \sigma_y^2}{S_x^2 / \sigma_x^2} \sim \frac{\chi^2(m-1)/(m-1)}{\chi^2(n-1)/(n-1)} \sim F(m-1, n-1)
$$


---

## 3. 신뢰 구간 도출 (Confidence Interval Derivation)

**[KR]** F-분포의 분위수(Quantiles)를 활용하여 확률 부등식을 세운 뒤 식을 $\sigma_x^2 / \sigma_y^2$ 에 대해 정리하면, 모분산 비율에 대한 신뢰 구간을 도출할 수 있습니다. (주의: F-분포의 역수 성질로 인해 하한값을 계산할 때 분자와 분모의 자유도 순서가 $n-1, m-1$ 로 뒤집히는 것에 유의해야 합니다.)

**[EN]** By setting up a probability inequality using F-distribution quantiles and algebraically solving for $\sigma_x^2 / \sigma_y^2$, we can derive the confidence interval for the population variance ratio. (Note: Due to the reciprocal property of the F-distribution, the order of degrees of freedom flips to $n-1, m-1$ when calculating the lower bound.)

* **$100(1-\alpha)\%$ 양측 신뢰 구간 (Two-sided CI):**
$$
\frac{\sigma_x^2}{\sigma_y^2} \in \left[ \frac{S_x^2}{S_y^2} \frac{1}{F_{\alpha/2, n-1, m-1}}, \frac{S_x^2}{S_y^2} F_{\alpha/2, m-1, n-1} \right]
$$


이 신뢰 구간은 두 표본 분산의 비율인 $S_x^2 / S_y^2$ 에 정비례하며, 모평균 $\mu_x, \mu_y$ 에 대한 어떠한 정보도 필요로 하지 않습니다.

* **$100(1-\alpha)\%$ 하한 단측 (Lower CI):**
$$
\frac{S_x^2}{S_y^2} \frac{1}{F_{\alpha, n-1, m-1}} \le \frac{\sigma_x^2}{\sigma_y^2}
$$


* **$100(1-\alpha)\%$ 상한 단측 (Upper CI):**
$$
\frac{\sigma_x^2}{\sigma_y^2} \le \frac{S_x^2}{S_y^2} F_{\alpha, m-1, n-1}
$$


**(Tip: 만약 반대 비율인 $\sigma_y^2 / \sigma_x^2$ 의 신뢰 구간을 구하고 싶다면, 위 공식의 모든 $X$ 와 $Y$ 의 위치를 통째로 뒤바꾸기만 하면 됩니다.)**

---

## 4. 실전 예제: IQ 테스트 점수의 변동성 비교 (Practice Example)

**[KR]** 독립적인 두 정규 모집단에서 데이터를 추출하여 IQ 테스트 A와 B의 점수를 비교해 봅시다. 
* **테스트 A:** 25명 응시 ($n_A = 25$), 표본 분산 $S_A^2 = 100$
* **테스트 B:** 16명 응시 ($n_B = 16$), 표본 분산 $S_B^2 = 70$

이 데이터를 바탕으로 두 테스트의 모분산 비율 $\sigma_A^2 / \sigma_B^2$ 에 대한 **95% 상한 단측 신뢰 구간(Upper CI)**을 구해봅시다.

1. 공식에 필요한 분위수는 $F_{\alpha, n_B-1, n_A-1}$ 입니다. $\alpha = 0.05$ 이고 자유도가 각각 $15, 24$ 이므로, 분포표에서 $F_{0.05, 15, 24}$ 를 찾으면 $2.11$ 이 나옵니다.
2. 상한 단측 공식에 대입합니다.
$$
\frac{\sigma_A^2}{\sigma_B^2} \le \frac{S_A^2}{S_B^2} F_{0.05, 15, 24} = \frac{100}{70}(2.11) = 3.01
$$


**[결론]** 테스트 A 점수의 변동성(분산)은 95% 신뢰 수준에서 테스트 B 점수 변동성의 최대 3.01배 이하라고 결론 내릴 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-9 Ratio of Variance of Two Normals-1" src="https://github.com/user-attachments/assets/5bdd4c30-9823-47da-a859-baa39361d6f7" />
    <img width="1264" height="1635" alt="1-9 Ratio of Variance of Two Normals-2" src="https://github.com/user-attachments/assets/618d9f47-fed5-4bab-9cd4-334214b7c899" />
  </div>
</details>
