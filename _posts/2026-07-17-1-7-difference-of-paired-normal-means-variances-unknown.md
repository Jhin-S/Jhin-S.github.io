---
title: "1-7 Difference of Paired Normal Means (Variances Unknown)"
date: 2026-07-17 10:04:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, paired-t-test, normal-distribution, confidence-interval, unknown-variance]
math: true
---

## 1. 쌍체 표본의 도입 (Introduction to Paired Observations)

**[KR]** 두 정규 모집단의 평균을 비교할 때, 완전히 독립적인 두 집단을 구성하는 대신 '쌍(Pair)'으로 데이터를 묶어서 수집할 수 있습니다. 예를 들어, 쌍둥이 중 한 명에게는 신약을, 다른 한 명에게는 위약을 투여하여 그 결과를 비교하는 방식입니다. 
이러한 설계에서는 서로 다른 쌍끼리는 철저하게 독립적이지만, 동일한 쌍 내부에 있는 두 관측치($X_i$와 $Y_i$)는 서로 독립이 아닐 수 있습니다. 이렇게 실험을 쌍으로 설계하는 핵심적인 목적은 외부의 불필요한 노이즈(Extraneous noise)를 효과적으로 제거하여 두 집단 간의 실질적인 차이를 훨씬 더 정밀하게 포착하기 위함입니다.

**[EN]** When comparing means from two competing normal populations, instead of using completely independent groups, we can collect observations structured in 'pairs'. A classic example is administering a new drug to one twin and a placebo to the other. 
In this setup, observations between different pairs are strictly independent; however, the two observations within the exact same pair ($X_i$ and $Y_i$) may not be independent of each other. The core idea behind designing experiments this way is to eliminate extraneous noise, which allows us to capture the true difference between the populations much more precisely.

---

## 2. 차이값에 대한 t-분포 도출 (Derivation of t-distribution for Differences)

**[KR]** 두 집단의 모분산($\sigma_x^2, \sigma_y^2$)을 모르는 상태에서, 각 쌍의 관측치 차이를 $D_i \equiv X_i - Y_i$ 로 새롭게 정의해 봅시다. 이 새로운 확률 변수 $D_i$는 평균이 $\mu_d = \mu_x - \mu_y$ 이고 분산이 $\sigma_d^2 = \sigma_x^2 + \sigma_y^2 - 2Cov(X_i, Y_i)$ 인 단일 정규 분포를 따르게 됩니다. 
이렇게 변환하고 나면 문제는 단순히 '하나의 정규 모집단에서 모평균과 모분산을 모를 때'의 기초적인 상황으로 완벽하게 축소됩니다. 따라서 표본 차이의 평균 $\bar{D}$와 표본 차이의 분산 $S_d^2$을 구한 뒤 피벗을 구성하면, 자유도가 $n-1$인 익숙한 t-분포를 얻을 수 있습니다.

**[EN]** With the population variances ($\sigma_x^2, \sigma_y^2$) unknown, let's define a new variable representing the pair-wise difference: $D_i \equiv X_i - Y_i$. These newly formed differences follow a single normal distribution with a mean of $\mu_d = \mu_x - \mu_y$ and a variance of $\sigma_d^2 = \sigma_x^2 + \sigma_y^2 - 2Cov(X_i, Y_i)$. 
Through this transformation, the problem beautifully reduces to the basic scenario of a single normal population where both the mean and variance are unknown. Therefore, by calculating the sample mean of the differences $\bar{D}$ and the sample variance $S_d^2$, we construct a pivot that perfectly follows a t-distribution with $n-1$ degrees of freedom.

$$ 
\frac{\bar{D} - \mu_d}{\sqrt{S_d^2/n}} \sim t(n-1) 
$$ 


---

## 3. 신뢰 구간 공식 (Confidence Interval Formulas)

**[KR]** 이 피벗 통계량을 통해 두 모평균 차이 $\mu_d$ 에 대한 신뢰 구간을 다음과 같이 손쉽게 도출할 수 있습니다.

**[EN]** Using this pivot statistic, we can easily derive the confidence intervals for the mean difference $\mu_d$ as follows.

*   **$100(1-\alpha)\%$ 양측 신뢰 구간 (Two-sided CI):** $\mu_d \in \bar{D} \pm t_{\alpha/2, n-1}\sqrt{\frac{S_d^2}{n}}$
*   **하한 단측 (One-sided Lower):** $\mu_d \ge \bar{D} - t_{\alpha, n-1}\sqrt{\frac{S_d^2}{n}}$
*   **상한 단측 (One-sided Upper):** $\mu_d \le \bar{D} + t_{\alpha, n-1}\sqrt{\frac{S_d^2}{n}}$

---

## 4. 평행 주차 실전 예제와 쌍체 t-검정의 강력함 (Parking Example & Power of Paired-t)

**[KR]** 5명의 운전자에게 혼다와 캐딜락을 각각 평행 주차하게 한 뒤 그 소요 시간의 차이를 측정했다고 가정해 보겠습니다. 사람 간에는 서로 독립이지만, 동일한 운전자의 주차 기록 두 개는 서로 독립이 아니므로 쌍체(Paired) 분석을 적용하는 것이 맞습니다.
데이터를 계산한 결과 $n=5$, 차이의 평균 $\bar{D} = -9$, 분산 $S_d^2 = 42.5$ 가 도출되었습니다. 이를 바탕으로 $90\%$ 신뢰 구간을 구하면 $-9 \pm 2.13\sqrt{42.5/5} = -9 \pm 6.21$ 이 됩니다.

**왜 일반적인 두 독립 표본 방법(Usual method)을 쓰지 않을까요?**
만약 10명의 각기 다른 사람을 동원하여 독립 표본 근사법을 사용한다면, 사람마다 천차만별인 기본 주차 실력(자연적 변동성) 때문에 데이터에 엄청난 노이즈가 유입됩니다. 실제로 이 독립 표본 방식으로 계산해 보면, 자유도가 $n-1$보다 더 큼에도 불구하고 신뢰 구간이 $-9 \pm 12.13$ 으로 쌍체 분석보다 훨씬 더 넓어지는 현상이 발생합니다. 
**[결론/Moral]** 따라서 데이터를 쌍으로 묶어서 수집할 수 있는 환경이라면, 주저하지 말고 쌍체 t-분석(Paired-t)을 사용하는 것이 압도적으로 유리합니다.

**[EN]** Suppose we ask 5 individuals to parallel park a Honda and a Cadillac, and we measure the difference in their parking times. The individuals themselves are independent, but the two parking times from the exact same person are not, making a paired analysis the correct approach.
Calculating the data yields $n=5$, a mean difference of $\bar{D} = -9$, and a variance of $S_d^2 = 42.5$. Constructing a $90\%$ CI with these values gives $-9 \pm 2.13\sqrt{42.5/5} = -9 \pm 6.21$.

**Why not just use the "usual" two-sample method?**
If we used 10 entirely different people and applied the usual approximate method, the natural variation in individual parking skills would introduce significantly more noise into the system. In fact, computing the CI with the usual method yields an interval of $-9 \pm 12.13$, which is much wider than the paired version, even though the usual method has a higher approximate degree of freedom. 
**[Moral]** The lesson here is clear: whenever your data allows for it, you should always use the paired-t method.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-7 Difference of Paired Normal Means (Variances Unknown)-1" src="https://github.com/user-attachments/assets/6f859aec-9599-4c17-80a3-d0e12a71fefe" />
    <img width="1264" height="1635" alt="1-7 Difference of Paired Normal Means (Variances Unknown)-2" src="https://github.com/user-attachments/assets/8fc272c1-0e1d-49dc-a26c-3757a7b2050e" />
    <img width="1264" height="1635" alt="1-7 Difference of Paired Normal Means (Variances Unknown)-3" src="https://github.com/user-attachments/assets/ad3c77af-3611-40f9-8a4c-109818678c46" />
    <img width="1264" height="1635" alt="1-7 Difference of Paired Normal Means (Variances Unknown)-4" src="https://github.com/user-attachments/assets/04ef594a-6c13-48b2-8b76-41a30c23a762" />
  </div>
</details>
