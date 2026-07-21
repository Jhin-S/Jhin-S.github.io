---
title: "2-10 Two-Sample Normal Variances Test"
date: 2026-07-21 19:58:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, two-sample, variance, f-test]
math: true
---

## 1. 개요 및 검정 통계량 (Overview and Test Statistic)

**[KR]** 두 모집단이 동일한 분산을 가지는지 확인하기 위한 가설 검정입니다. 서로 독립적인 두 정규 모집단 $X_1, \dots, X_n \sim Nor(\mu_x, \sigma_x^2)$ 와 $Y_1, \dots, Y_m \sim Nor(\mu_y, \sigma_y^2)$ 에서 표본을 추출했다고 가정합니다.

**[EN]** This hypothesis test is to determine if two populations have the same variance. We assume that we extract independent samples $X_1, \dots, X_n \sim Nor(\mu_x, \sigma_x^2)$ and $Y_1, \dots, Y_m \sim Nor(\mu_y, \sigma_y^2)$ from two normal populations.

**[KR]** 모분산 $\sigma_x^2$와 $\sigma_y^2$를 추정하기 위해 표본 분산 $S_x^2$와 $S_y^2$를 사용합니다. 귀무가설($H_0$)이 참이라고 가정할 때, 이 두 표본 분산의 비율로 정의되는 검정 통계량 $F_0$는 자유도가 각각 $n-1, m-1$인 F-분포를 따릅니다.

**[EN]** We will estimate the population variances $\sigma_x^2$ and $\sigma_y^2$ by using the sample variances $S_x^2$ and $S_y^2$. If the null hypothesis ($H_0$) is true, the test statistic $F_0$, defined by the ratio of these sample variances, follows an F-distribution with $n-1$ and $m-1$ degrees of freedom.

$$ F_0 = \frac{S_x^2}{S_y^2} \sim F(n-1, m-1) $$


---

## 2. 양측 및 단측 검정 (Two-Sided and One-Sided Tests)

**[KR]** F-분포의 역수 성질($F_{1-\alpha/2, n-1, m-1} = 1 / F_{\alpha/2, m-1, n-1}$)을 활용하여 다음과 같은 가설 검정 규칙을 세울 수 있습니다.

**[EN]** Using a property of the F distribution ($F_{1-\alpha/2, n-1, m-1} = 1 / F_{\alpha/2, m-1, n-1}$), we can establish the following hypothesis testing rules.

*   **양측 검정 (Two-Sided Test):**
    *   **[KR]** 가설: $H_0: \sigma_x^2 = \sigma_y^2$ (즉, $\sigma_x^2/\sigma_y^2 = 1$) vs $H_1: \sigma_x^2 \neq \sigma_y^2$
    *   **[KR]** 기각 조건: $F_0 < \frac{1}{F_{\alpha/2, m-1, n-1}}$ 또는 $F_0 > F_{\alpha/2, n-1, m-1}$ 일 때 $H_0$ 기각
    *   **[EN]** Hypotheses: $H_0: \sigma_x^2 = \sigma_y^2$ (or $\sigma_x^2/\sigma_y^2 = 1$) vs $H_1: \sigma_x^2 \neq \sigma_y^2$ / Reject $H_0$ if $F_0 < \frac{1}{F_{\alpha/2, m-1, n-1}}$ or $F_0 > F_{\alpha/2, n-1, m-1}$

*   **우측 단측 검정 (One-Sided Test, Right):**
    *   **[KR]** 가설: $H_0: \sigma_x^2 \le \sigma_y^2$ vs $H_1: \sigma_x^2 > \sigma_y^2$
    *   **[KR]** 기각 조건: $F_0 > F_{\alpha, n-1, m-1}$ 일 때 $H_0$ 기각
    *   **[EN]** Hypotheses: $H_0: \sigma_x^2 \le \sigma_y^2$ vs $H_1: \sigma_x^2 > \sigma_y^2$ / Reject $H_0$ if $F_0 > F_{\alpha, n-1, m-1}$

*   **좌측 단측 검정 (One-Sided Test, Left):**
    *   **[KR]** 가설: $H_0: \sigma_x^2 \ge \sigma_y^2$ vs $H_1: \sigma_x^2 < \sigma_y^2$
    *   **[KR]** 기각 조건: $F_0 < \frac{1}{F_{\alpha, m-1, n-1}}$ 일 때 $H_0$ 기각
    *   **[EN]** Hypotheses: $H_0: \sigma_x^2 \ge \sigma_y^2$ vs $H_1: \sigma_x^2 < \sigma_y^2$ / Reject $H_0$ if $F_0 < \frac{1}{F_{\alpha, m-1, n-1}}$

---

## 3. 실전 예제 (Practice Example)

**[KR]** 📝 유의수준 $\alpha = 0.05$ 에서 두 프로세스가 동일한 분산을 가지는지 테스트해 봅시다 ($H_0: \sigma_x^2 = \sigma_y^2$ vs $H_1: \sigma_x^2 \neq \sigma_y^2$). 표본 분산의 비율이 너무 높거나 너무 낮으면 귀무가설을 기각하게 됩니다.

**[EN]** 📝 Suppose we want to test at level $0.05$ whether or not two processes have the same variance ($H_0: \sigma_x^2 = \sigma_y^2$ vs $H_1: \sigma_x^2 \neq \sigma_y^2$). If the ratio of the sample variances is too high or too low, we will reject $H_0$.

**[KR]** 수집된 데이터는 집단 X에서 $n=7$, 표본 분산 $S_x^2=7.78$ 이고, 집단 Y에서 $m=8$, 표본 분산 $S_y^2=12.04$ 입니다. 검정 통계량을 계산하면 다음과 같습니다.

**[EN]** The collected data consists of $n=7$ observations with $S_x^2=7.78$ and $m=8$ with $S_y^2=12.04$. Then the test statistic is calculated as follows.

$$ F_0 = \frac{S_x^2}{S_y^2} = \frac{7.78}{12.04} = 0.646 $$


**[KR]** 기각역 설정을 위해 하한과 상한 임계값을 계산합니다.

**[EN]** We calculate the critical values to set the rejection region.

*   **하한 임계값 (Lower critical value):** 
    $$ F_{1-0.025, 6, 7} = \frac{1}{F_{0.025, 7, 6}} = \frac{1}{5.695} = 0.176 $$
   
*   **상한 임계값 (Upper critical value):** 
    $$ F_{0.025, 6, 7} = 5.119 $$
   

**[결론 / Conclusion]**
**[KR]** 검정 통계량 $F_0 = 0.646$ 은 하한값 $0.176$ 과 상한값 $5.119$ 사이에 안전하게 위치하므로 ($0.176 \le 0.646 \le 5.119$), 우리는 귀무가설 $H_0$를 기각하는 데 실패합니다. 즉, 두 모집단의 분산이 다르다고 말할 수 있는 충분한 증거가 없습니다.

**[EN]** Since the test statistic $F_0 = 0.646$ falls safely between the lower limit $0.176$ and the upper limit $5.119$ ($0.176 \le 0.646 \le 5.119$), we fail to reject $H_0$. This means there is not enough evidence to conclude that the two population variances are different.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-10 Two-Sample Normal Variances Test-1" src="https://github.com/user-attachments/assets/73ad845a-c6ce-4aed-ba2d-6fd2d01b9cb5" />
  </div>
</details>
