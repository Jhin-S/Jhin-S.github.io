---
title: "2-9 Normal Variance Test"
date: 2026-07-21 19:53:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, variance, chi-squared-test]
math: true
---

## 1. 정규 분산 검정의 설정과 검정 통계량 (Set up and Test Statistic)

**[KR]** 모평균 $\mu$와 모분산 $\sigma^2$을 모두 알지 못하는 정규 모집단에서 추출된 독립적인 표본 $X_1, \dots, X_n \sim Nor(\mu, \sigma^2)$ 을 가정해 봅시다. 우리는 사용자가 지정한 특정한 가설적 분산 값 $\sigma_0^2$에 대하여 가설 검정을 수행하고자 합니다.

**[EN]** Suppose we have independent samples $X_1, \dots, X_n \sim Nor(\mu, \sigma^2)$ from a normal population where both $\mu$ and $\sigma^2$ are completely unknown. We want to consider a hypothesis test regarding a specific user-specified hypothesized variance $\sigma_0^2$.

**[KR]** 이를 위해 표본 분산 $S^2$의 분포 성질을 다시 한번 상기해 봅니다.
**[EN]** To do this, we recall (yet again) the distributional property of the sample variance $S^2$.

$$ S^2 \equiv \frac{1}{n-1}\sum_{i=1}^{n}(X_i - \bar{X})^2 \sim \frac{\sigma^2 \chi^2(n-1)}{n-1} $$


**[KR]** 만약 귀무가설($H_0$)이 참이라면, 우리는 자유도가 $n-1$인 카이제곱 분포를 따르는 다음과 같은 검정 통계량 $\chi_0^2$를 정의하여 사용할 수 있습니다.
**[EN]** If the null hypothesis ($H_0$) is true, we can define and use the following test statistic $\chi_0^2$, which follows a chi-squared distribution with $n-1$ degrees of freedom.

$$ \chi_0^2 \equiv \frac{(n-1)S^2}{\sigma_0^2} \sim \chi^2(n-1) $$


---

## 2. 양측 및 단측 검정 규칙 (Two-sided and One-sided Tests)

**[KR]** 카이제곱 검정 통계량을 활용하여 다음과 같은 세 가지 형태의 가설 검정을 수행할 수 있습니다.

**[EN]** Using the chi-squared test statistic, we can perform the following three types of hypothesis tests.

*   **양측 검정 (Two-sided Test):**
    *   **[KR]** 가설: $H_0: \sigma^2 = \sigma_0^2$ vs $H_1: \sigma^2 \neq \sigma_0^2$
    *   **[KR]** 기각 조건: $\chi_0^2 < \chi_{1-\alpha/2, n-1}^2$ 이거나 $\chi_0^2 > \chi_{\alpha/2, n-1}^2$ 일 때 $H_0$ 기각
    *   **[EN]** Hypotheses: $H_0: \sigma^2 = \sigma_0^2$ vs $H_1: \sigma^2 \neq \sigma_0^2$ / Reject $H_0$ if $\chi_0^2 < \chi_{1-\alpha/2, n-1}^2$ or $\chi_0^2 > \chi_{\alpha/2, n-1}^2$

*   **우측 단측 검정 (One-sided Test, Right):**
    *   **[KR]** 가설: $H_0: \sigma^2 \le \sigma_0^2$ vs $H_1: \sigma^2 > \sigma_0^2$
    *   **[KR]** 기각 조건: $\chi_0^2 > \chi_{\alpha, n-1}^2$ 일 때 $H_0$ 기각
    *   **[EN]** Hypotheses: $H_0: \sigma^2 \le \sigma_0^2$ vs $H_1: \sigma^2 > \sigma_0^2$ / Reject $H_0$ if $\chi_0^2 > \chi_{\alpha, n-1}^2$

*   **좌측 단측 검정 (One-sided Test, Left):**
    *   **[KR]** 가설: $H_0: \sigma^2 \ge \sigma_0^2$ vs $H_1: \sigma^2 < \sigma_0^2$
    *   **[KR]** 기각 조건: $\chi_0^2 < \chi_{1-\alpha, n-1}^2$ 일 때 $H_0$ 기각
    *   **[EN]** Hypotheses: $H_0: \sigma^2 \ge \sigma_0^2$ vs $H_1: \sigma^2 < \sigma_0^2$ / Reject $H_0$ if $\chi_0^2 < \chi_{1-\alpha, n-1}^2$

---

## 3. 실전 예제 (Practice Example)

**[KR]** 📝 어떤 프로세스의 분산이 $0.02$ 이하인지 유의수준 $\alpha = 0.05$ 에서 검정한다고 가정해 봅시다. 명시적으로 가설을 세우면 $H_0: \sigma^2 \le 0.02$ 대 $H_1: \sigma^2 > 0.02$ 가 됩니다. 만약 표본 분산이 너무 높게 나온다면 우리는 $H_0$를 기각할 것입니다.

**[EN]** 📝 Suppose we want to test at level $0.05$ whether or not the variance of a certain process is $\le 0.02$. Specifically, the hypotheses are $H_0: \sigma^2 \le 0.02$ vs $H_1: \sigma^2 > 0.02$. If the sample variance is too high, we will reject $H_0$.

**[KR]** 표본 데이터가 $n = 20$, 표본 평균 $\bar{X} = 125.12$, 그리고 표본 분산 $S^2 = 0.0225$ 로 주어졌다고 합시다. 검정 통계량 $\chi_0^2$를 계산하면 다음과 같습니다. (참고로 이 통계량은 표본 평균 $\bar{X}$ 값에 명시적으로 의존하지 않습니다.)

**[EN]** Suppose we have $n = 20$, $\bar{X} = 125.12$, and $S^2 = 0.0225$. Then the test statistic $\chi_0^2$ is calculated as follows. (Note that it isn't explicitly dependent on $\bar{X}$).

$$ \chi_0^2 = \frac{(n-1)S^2}{\sigma_0^2} = \frac{19 \times 0.0225}{0.02} = 21.375 $$


**[결론 / Conclusion]**
**[KR]** 임계값인 카이제곱 분위수를 구하면 $\chi_{0.05, 19}^2 = 30.14$ 입니다. 우리가 계산한 검정 통계량 $21.375$ 가 기각역 기준인 $30.14$ 를 넘지 않으므로 ($\chi_0^2 \ngtr 30.14$), 우리는 귀무가설 $H_0$를 기각하는 데 실패합니다.
**[EN]** Furthermore, the critical value is $\chi_{\alpha, n-1}^2 = \chi_{0.05, 19}^2 = 30.14$. Since our test statistic $21.375$ is not greater than the critical value $30.14$, we fail to reject $H_0$.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-9 Normal Variance Test-1" src="https://github.com/user-attachments/assets/b8e92af7-1f12-48f8-8258-698122c634e3" />
  </div>
</details>
