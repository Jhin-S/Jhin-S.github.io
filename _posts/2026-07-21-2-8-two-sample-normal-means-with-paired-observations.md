---
title: "2-8 Two-Sample Normal Means with Paired Observations"
date: 2026-07-21 13:26:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, paired-t-test, dependent-samples]
math: true
---

## 1. 쌍체 표본의 개념 (Concept of Paired Observations)

**[KR]** 서로 경쟁하는 두 정규 모집단에서 관측치를 '쌍(Pair)'으로 수집하는 상황을 다시 고려해 봅시다. 서로 다른 쌍들 간의 확률 변수는 철저하게 독립적입니다. 하지만 동일한 쌍 내부에 존재하는 두 관측치($X_i, Y_i$)는 독립이 아닐 수 있으며, 사실 양의 상관관계(Positively correlated)를 가지는 것이 실험에 더 유리한 경우가 많습니다.

**[EN]** Again consider two competing normal populations where we collect observations in pairs. The random variables between different pairs are completely independent. However, the two observations within the exact same pair ($X_i, Y_i$) may not be independent; in fact, it is often beneficial for them to be positively correlated.

**[KR] 📝 예제:** 쌍둥이 중 한 명에게는 신약을 투여하고, 다른 한 명에게는 위약(Placebo)을 투여하여 결과를 비교하는 실험 등이 대표적인 쌍체 표본 설계입니다.

**[EN] 📝 Example:** A classic example of a paired design is when one twin takes a new drug while the other takes a placebo, and their results are compared.

---

## 2. 차이값과 검정 통계량 (Differences and Test Statistic)

**[KR]** 각 쌍의 차이를 $D_i \equiv X_i - Y_i$ 로 새롭게 정의해 봅시다. 이 차이값들은 정규 분포 $Nor(\mu_d, \sigma_d^2)$ 를 따르게 됩니다. 
여기서 평균은 $\mu_d \equiv \mu_x - \mu_y$ 이며, 분산은 $\sigma_d^2 \equiv \sigma_x^2 + \sigma_y^2 - 2 Cov(X_i, Y_i)$ 로 정의됩니다.

**[EN]** Let us define the pair-wise differences as $D_i \equiv X_i - Y_i$. These differences follow a normal distribution $Nor(\mu_d, \sigma_d^2)$. 
Here, the mean is $\mu_d \equiv \mu_x - \mu_y$, and the variance is defined as $\sigma_d^2 \equiv \sigma_x^2 + \sigma_y^2 - 2 Cov(X_i, Y_i)$.

**[KR]** 단일 정규 분포에서 분산을 모를 때 사용했던 완전히 동일한 수학적 조작(Manipulations)을 적용하여 차이의 표본 평균 $\bar{D}$ 와 표본 분산 $S_d^2$ 을 구합니다. 귀무가설($\mu_d = 0$)이 참이라고 가정할 때, 검정 통계량 $T_0$는 자유도 $n-1$인 t-분포를 따릅니다.

**[EN]** Using the exact same mathematical manipulations as in the single-sample normal mean problem with unknown variance, we calculate the sample mean $\bar{D}$ and sample variance $S_d^2$ of the differences. Assuming the null hypothesis ($\mu_d = 0$) is true, the test statistic $T_0$ follows a t-distribution with $n-1$ degrees of freedom.

$$ T_0 \equiv \frac{\bar{D}}{\sqrt{S_d^2/n}} \sim t(n-1) $$


---

## 3. 가설 검정 규칙 (Hypothesis Testing Rules)

**[KR]** 산출된 검정 통계량 $T_0$를 바탕으로 다음과 같은 기준에 따라 귀무가설 $H_0$를 기각(Reject)합니다.

**[EN]** Based on the calculated test statistic $T_0$, we reject the null hypothesis $H_0$ according to the following rules.

*   **양측 검정 (Two-sided test):**
    *   **[KR]** 가설: $H_0: \mu_d = 0$ 대 $H_1: \mu_d \neq 0$
    *   **[KR]** 기각 조건: $\lvert T_0 \rvert > t_{\alpha/2, n-1}$
    *   **[EN]** Hypotheses: $H_0: \mu_d = 0$ vs $H_1: \mu_d \neq 0$ / Reject if $\lvert T_0 \rvert > t_{\alpha/2, n-1}$

*   **우측 단측 검정 (One-sided test, Right):**
    *   **[KR]** 가설: $H_0: \mu_d \le 0$ 대 $H_1: \mu_d > 0$
    *   **[KR]** 기각 조건: $T_0 > t_{\alpha, n-1}$
    *   **[EN]** Hypotheses: $H_0: \mu_d \le 0$ vs $H_1: \mu_d > 0$ / Reject if $T_0 > t_{\alpha, n-1}$

*   **좌측 단측 검정 (One-sided test, Left):**
    *   **[KR]** 가설: $H_0: \mu_d \ge 0$ 대 $H_1: \mu_d < 0$
    *   **[KR]** 기각 조건: $T_0 < -t_{\alpha, n-1}$
    *   **[EN]** Hypotheses: $H_0: \mu_d \ge 0$ vs $H_1: \mu_d < 0$ / Reject if $T_0 < -t_{\alpha, n-1}$

---

## 4. 평행 주차 실전 예제 (Parallel Parking Example)

**[KR]** 📝 동일한 사람 5명에게 혼다(Honda)와 캐딜락(Cadillac) 두 대의 평행 주차 소요 시간을 각각 측정하게 한 데이터를 분석해 봅시다. 귀무가설 $H_0: \mu_H = \mu_C$ 에 대해 유의수준 $\alpha = 0.10$ 에서 양측 검정을 수행합니다.

**[EN]** 📝 Let's analyze data where the exact same 5 individuals timed their parallel parking using both a Honda and a Cadillac. We test the null hypothesis $H_0: \mu_H = \mu_C$ at a significance level of $\alpha = 0.10$.

**[KR]** 표본 데이터에서 $n=5$, 차이의 평균 $\bar{D} = -9$, 차이의 표본 분산 $S_d^2 = 42.5$ 가 주어졌습니다. 
이를 공식에 대입하면 검정 통계량의 절댓값 $\lvert T_0 \rvert = 3.087$ 이 계산됩니다. 
자유도가 4인 t-분포표에서 임계값은 $t_{0.05, 4} = 2.13$ 입니다. 
결과적으로 $3.087 > 2.13$ 이므로 우리는 $H_0$를 강력하게 기각합니다. 
**결론:** 두 차량의 주차 시간 평균은 다르며($\mu_H \neq \mu_C$), 아마도 혼다를 주차하는 것이 통계적으로 더 쉽다는 결론을 내릴 수 있습니다.

**[EN]** The sample data gives us $n=5$, a mean difference of $\bar{D} = -9$, and a sample variance of $S_d^2 = 42.5$. 
Plugging these into the formula, the absolute value of the test statistic is $\lvert T_0 \rvert = 3.087$. 
From the t-distribution table with 4 degrees of freedom, the critical value is $t_{0.05, 4} = 2.13$. 
Consequently, since $3.087 > 2.13$, we strongly reject $H_0$. 
**Conclusion:** We conclude that the mean parking times are different ($\mu_H \neq \mu_C$), and it's probably the case that Hondas are easier to park.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-8 Two-Sample Normal Means with Paired Observations-1" src="https://github.com/user-attachments/assets/39a57fdb-b855-4c9f-92fc-09140a817883" />
    <img width="1264" height="1635" alt="2-8 Two-Sample Normal Means with Paired Observations-2" src="https://github.com/user-attachments/assets/d24872fb-9e05-4862-9303-ef5b41461573" />
  </div>
</details>
