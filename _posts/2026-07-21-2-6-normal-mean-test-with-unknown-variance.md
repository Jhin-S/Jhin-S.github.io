---
title: "2-6 Normal Mean Test with Unknown Variance"
date: 2026-07-21 13:15:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, t-test, unknown-variance, p-value]
math: true
---

## 1. 모분산을 모르는 경우의 검정 통계량 (Test Statistic with Unknown Variance)

**[KR]** 모분산 $\sigma^2$을 모르는 정규 모집단에서 표본 $X_1, \dots, X_n \sim Nor(\mu, \sigma^2)$ 을 추출했다고 가정합니다. 모평균 $\mu$를 추정하기 위해 표본 평균 $\bar{X}$를 사용하며, 미지의 $\sigma^2$을 추정하기 위해서는 표본 분산 $S^2$을 사용합니다.
**[EN]** Suppose we extract samples $X_1, \dots, X_n \sim Nor(\mu, \sigma^2)$ from a normal population where $\sigma^2$ is unknown. We use the sample mean $\bar{X}$ to estimate $\mu$, and we use the sample variance $S^2$ to estimate the unknown $\sigma^2$.

**[KR]** 이를 바탕으로 정의되는 검정 통계량 $T_0$는 다음과 같습니다.
**[EN]** Based on this, the test statistic $T_0$ is defined as follows.

$$ T_0 \equiv \frac{\bar{X} - \mu_0}{S/\sqrt{n}} $$


**[KR]** 만약 귀무가설 $H_0$가 참이라면, 이 통계량은 자유도가 $n-1$인 t-분포를 따르게 됩니다 ($T_0 \sim t(n-1)$).
**[EN]** If the null hypothesis $H_0$ is true, this statistic follows a t-distribution with $n-1$ degrees of freedom ($T_0 \sim t(n-1)$).

---

## 2. 기각 규칙: 양측 및 단측 검정 (Rejection Rules: Two-Sided and One-Sided)

**[KR]** 이전 장들과 동일한 논리를 사용하여 검정의 기각역을 설정할 수 있습니다.
**[EN]** We can set up the rejection regions for the tests using the exact same reasoning as in previous lessons.

*   **양측 검정 (Two-sided test):** 
    *   **[KR]** 가설 $H_0: \mu = \mu_0$ 대 $H_1: \mu \neq \mu_0$ 에서, $\lvert T_0 \rvert > t_{\alpha/2, n-1}$ 이면 $H_0$를 기각합니다.
    *   **[EN]** For hypotheses $H_0: \mu = \mu_0$ vs $H_1: \mu \neq \mu_0$, we reject $H_0$ if $\lvert T_0 \rvert > t_{\alpha/2, n-1}$.

*   **우측 검정 (Right-sided test):** 
    *   **[KR]** 가설 $H_0: \mu \le \mu_0$ 대 $H_1: \mu > \mu_0$ 에서, $T_0 > t_{\alpha, n-1}$ 이면 $H_0$를 기각합니다.
    *   **[EN]** For hypotheses $H_0: \mu \le \mu_0$ vs $H_1: \mu > \mu_0$, we reject $H_0$ if $T_0 > t_{\alpha, n-1}$.

*   **좌측 검정 (Left-sided test):** 
    *   **[KR]** 가설 $H_0: \mu \ge \mu_0$ 대 $H_1: \mu < \mu_0$ 에서, $T_0 < -t_{\alpha, n-1}$ 이면 $H_0$를 기각합니다.
    *   **[EN]** For hypotheses $H_0: \mu \ge \mu_0$ vs $H_1: \mu < \mu_0$, we reject $H_0$ if $T_0 < -t_{\alpha, n-1}$.

---

## 3. P-값의 계산 (p-value Calculation)

**[KR]** p-값은 $H_0$를 기각할 수 있게 만드는 가장 작은 유의수준 $\alpha$를 의미합니다. 모분산을 모르는 경우의 양측 검정에서 p-값은 $t(n-1)$ 분포의 누적 분포 함수(CDF)인 $F_{n-1}$을 사용하여 아래와 같이 계산됩니다.
**[EN]** The p-value is the smallest level of significance $\alpha$ that would lead to the rejection of $H_0$. For the two-sided test with unknown variance, the p-value is calculated using $F_{n-1}$, the cumulative distribution function (CDF) of the $t(n-1)$ distribution, as follows.

$$ p = 2(1 - F_{n-1}(\lvert T_0 \rvert)) $$


---

## 4. 실전 예제 (Practice Example)

**[KR]** 어떤 프로세스의 평균이 150인지 아닌지를 유의수준 $\alpha = 0.05$ 에서 양측 검정한다고 가정해 봅시다. 수집된 데이터는 $n=15, \bar{X}=152.18, S^2=16.63$ 입니다.
**[EN]** Suppose we want to test at level $0.05$ whether or not the mean of some process is 150. The collected data is $n=15, \bar{X}=152.18$, and $S^2=16.63$.

**[KR]** 검정 통계량 $T_0$를 계산하면 2.07이 도출됩니다.
**[EN]** Calculating the test statistic $T_0$ yields 2.07.
$$ T_0 \equiv \frac{\bar{X} - \mu_0}{S/\sqrt{n}} = 2.07 $$


**[KR] 결론:** 유의수준 $\alpha = 0.05$ 일 때, 임계값은 $t_{0.025, 14} = 2.145$ 입니다. $\lvert T_0 \rvert = 2.07 < 2.145$ 이므로 아주 간발의 차이로 $H_0$ 기각에 실패하게 됩니다.
엑셀 함수(T.DIST 등)를 이용하여 CDF를 계산하면 p-값은 $0.0574$ 로 나옵니다. 이 p-값이 유의수준 $\alpha = 0.05$ 보다 크기 때문에 기각하지 못한다는 동일한 결론을 얻게 됩니다.

**[EN] Conclusion:** For a significance level of $\alpha = 0.05$, the critical value is $t_{0.025, 14} = 2.145$. Since $\lvert T_0 \rvert = 2.07 < 2.145$, we barely fail to reject $H_0$.
Alternatively, if we evaluate the CDF using an Excel function, the p-value is $0.0574$. Since $p = 0.0574 > 0.05 = \alpha$, we reach the exact same conclusion that we didn't quite reject $H_0$.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-6 Normal Mean Test with Unknown Variance-1" src="https://github.com/user-attachments/assets/dcaa8c76-01d0-4f05-8875-2ebe26cc0ef2" />
    <img width="1264" height="1635" alt="2-6 Normal Mean Test with Unknown Variance-2" src="https://github.com/user-attachments/assets/bc24931b-7829-456d-85e5-77fa9303af86" />
  </div>
</details>
