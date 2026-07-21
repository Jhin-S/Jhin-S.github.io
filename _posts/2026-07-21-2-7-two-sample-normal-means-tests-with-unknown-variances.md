---
title: "2-7 Two-Sample Normal Means Tests with Unknown Variances"
date: 2026-07-21 13:18:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, two-sample, t-test, unknown-variance]
math: true
---

## 1. 개요 (Overview)

**[KR]** 서로 독립적인 두 정규 모집단에서 표본 $X$와 $Y$를 추출했으며, 두 모분산 $\sigma_x^2$와 $\sigma_y^2$를 모두 모르는 상황을 가정해 봅시다. 어느 집단의 평균이 더 큰지 알아보기 위해 우리는 분산의 상태에 따라 크게 세 가지 케이스(합동 t-검정, 근사 t-검정, 쌍체 t-검정)를 고려할 수 있습니다.

**[EN]** Suppose we extract samples $X$ and $Y$ from two independent normal populations where both variances $\sigma_x^2$ and $\sigma_y^2$ are unknown. To determine which population has the larger mean, we consider three main cases depending on the variance situation: the pooled t-test, the approximate t-test, and the paired t-test.

---

## 2. 합동 t-검정 (Pooled t-Test: Equal Unknown Variances)

**[KR]** 두 모분산이 동일하다고 가정할 수 있을 때($\sigma_x^2 = \sigma_y^2 = \sigma^2$), 합동 분산 추정량 $S_p^2$를 사용하여 가설 검정을 수행합니다.

**[EN]** When we can assume the two population variances are equal ($\sigma_x^2 = \sigma_y^2 = \sigma^2$), we perform the hypothesis test using the pooled variance estimator $S_p^2$.

*   **합동 분산 추정량 (Pooled Variance Estimator):**
    $$ S_p^2 \equiv \frac{(n-1)S_x^2 + (m-1)S_y^2}{n+m-2} $$
    

*   **검정 통계량 (Test Statistic):**
    $$ T_0 \equiv \frac{\bar{X} - \bar{Y}}{S_p\sqrt{\frac{1}{n} + \frac{1}{m}}} $$
   

**[KR]** 귀무가설 $H_0$가 참일 때 $T_0$는 자유도 $n+m-2$인 t-분포를 따릅니다. 따라서 양측 검정($H_1: \mu_x \neq \mu_y$)의 경우 $\lvert T_0 \rvert > t_{\alpha/2, n+m-2}$ 이면 $H_0$를 기각합니다.

**[EN]** If $H_0$ is true, $T_0$ follows a t-distribution with $n+m-2$ degrees of freedom. Thus, for a two-sided test ($H_1: \mu_x \neq \mu_y$), we reject $H_0$ if $\lvert T_0 \rvert > t_{\alpha/2, n+m-2}$.

**[KR] 📝 예제:** 화학 공정에서 촉매 X 대신 촉매 Y가 더 높은 수율을 주는지 좌측 검정($H_0: \mu_x \ge \mu_y$ vs $H_1: \mu_x < \mu_y$)을 수행합니다. 
데이터($n=8, \bar{X}=91.73, S_x^2=3.89$ / $m=8, \bar{Y}=93.75, S_y^2=4.02$)에서 두 분산이 비슷하므로 합동 분산 $S_p^2 = 3.955$를 구합니다. 통계량 $T_0 = -2.03$ 이며 유의수준 0.05에서 기각역은 $-t_{0.05, 14} = -1.761$ 입니다. $T_0 < -1.761$ 이므로 $H_0$를 기각하고 촉매 Y를 사용해야 한다는 결론을 내립니다.

**[EN] 📝 Example:** We perform a left-sided test ($H_0: \mu_x \ge \mu_y$ vs $H_1: \mu_x < \mu_y$) to see if catalyst Y gives a higher mean yield than catalyst X. 
From the data ($n=8, \bar{X}=91.73, S_x^2=3.89$ / $m=8, \bar{Y}=93.75, S_y^2=4.02$), the variances are close, so we calculate the pooled variance $S_p^2 = 3.955$. The statistic is $T_0 = -2.03$, and the critical value at level 0.05 is $-t_{0.05, 14} = -1.761$. Since $T_0 < -1.761$, we reject $H_0$ and conclude we should probably use catalyst Y.

---

## 3. 근사 t-검정 (Approximate t-Test: Unequal Unknown Variances)

**[KR]** 두 모분산이 서로 다르다고 판단될 때($\sigma_x^2 \neq \sigma_y^2$)는 웰치의 근사 자유도 $\nu$를 사용하는 근사 t-검정을 수행합니다.

**[EN]** When we determine that the two population variances are unequal ($\sigma_x^2 \neq \sigma_y^2$), we perform an approximate t-test using Welch's approximate degrees of freedom $\nu$.

*   **검정 통계량 (Test Statistic):**
    $$ T_0^* \equiv \frac{\bar{X} - \bar{Y}}{\sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}} \approx t(\nu) $$
   

*   **근사 자유도 (Approximate df):**
    $$ \nu \equiv \frac{\left(\frac{S_x^2}{n} + \frac{S_y^2}{m}\right)^2}{\frac{(S_x^2/n)^2}{n-1} + \frac{(S_y^2/m)^2}{m-1}} $$
   

**[KR] 📝 예제:** 양측 검정($H_0: \mu_x = \mu_y$ vs $H_1: \mu_x \neq \mu_y$)을 $\alpha = 0.10$ 수준에서 진행합니다. 데이터는 $n=15, \bar{X}=24.2, S_x^2=10$ 이고 $m=10, \bar{Y}=23.9, S_y^2=20$ 입니다. 
분산 차이가 크므로 근사법을 적용하면, $T_0^* = 0.184$ 이고 자유도 $\nu = 14.9 \approx 15$ 가 됩니다. 임계값 $t_{0.05, 15} = 1.753$ 과 비교할 때 $\lvert T_0^* \rvert < 1.753$ 이므로 기각에 실패합니다. (사실 $T_0^*$가 0에 매우 가깝기 때문에 통계표를 볼 필요도 없었습니다.)

**[EN] 📝 Example:** We run a two-sided test ($H_0: \mu_x = \mu_y$ vs $H_1: \mu_x \neq \mu_y$) at level $\alpha = 0.10$. The data is $n=15, \bar{X}=24.2, S_x^2=10$ and $m=10, \bar{Y}=23.9, S_y^2=20$. 
Since the variances are not close, we use the approximation to get $T_0^* = 0.184$ and $\nu = 14.9 \approx 15$. Comparing it to the critical value $t_{0.05, 15} = 1.753$, we have $\lvert T_0^* \rvert < 1.753$, so we fail to reject $H_0$. (Actually, since $T_0^*$ was so close to 0, we didn't really need the tables.)

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-7 Two-Sample Normal Means Tests with Unknown Variances-1" src="https://github.com/user-attachments/assets/18babb36-9083-476a-9538-08e475415f15" />
    <img width="1264" height="1635" alt="2-7 Two-Sample Normal Means Tests with Unknown Variances-2" src="https://github.com/user-attachments/assets/26be55d4-b468-4f4b-b73c-a739619dbb3c" />
    <img width="1264" height="1635" alt="2-7 Two-Sample Normal Means Tests with Unknown Variances-3" src="https://github.com/user-attachments/assets/369b85c0-b630-44bc-9b59-a9dc694ece6f" />
    <img width="1264" height="1635" alt="2-7 Two-Sample Normal Means Tests with Unknown Variances-4" src="https://github.com/user-attachments/assets/14157b27-8da6-46fa-88d0-59389f60ebe5" />
  </div>
</details>
