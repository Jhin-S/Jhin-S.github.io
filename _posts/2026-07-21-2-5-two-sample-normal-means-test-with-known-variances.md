---
title: "2-5 Two-Sample Normal Means Test with Known Variances"
date: 2026-07-21 13:12:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, two-sample, z-test, known-variance]
math: true
---

## 1. 두 정규 평균의 가설 검정 설정 (Set-up for Two-Sample Test)

**[KR]** 서로 독립적인 두 정규 모집단에서 표본을 추출하는 상황을 가정해 봅시다. 집단 $X$의 데이터는 $X_1, X_2, \dots, X_n \sim Nor(\mu_x, \sigma_x^2)$ 를 따르고, 집단 $Y$의 데이터는 $Y_1, Y_2, \dots, Y_m \sim Nor(\mu_y, \sigma_y^2)$ 를 따릅니다. 이 과정에서 두 모분산 $\sigma_x^2$ 와 $\sigma_y^2$ 는 이미 알려져 있다고 가정합니다.

**[EN]** Suppose we have a set-up where we extract samples from two independent normal populations. The samples are $X_1, X_2, \dots, X_n \sim Nor(\mu_x, \sigma_x^2)$ and $Y_1, Y_2, \dots, Y_m \sim Nor(\mu_y, \sigma_y^2)$. We assume that the samples are completely independent of each other, and that the variances $\sigma_x^2$ and $\sigma_y^2$ are somehow known.

---

## 2. 양측 검정과 검정 통계량 (Two-Sided Test and Test Statistic)

**[KR]** 두 모집단 중 어느 쪽의 평균이 더 큰지, 혹은 두 평균이 과연 서로 다른지 확인하기 위해 양측 검정(Two-sided test)을 수행할 수 있습니다. 
우리가 세우는 가설은 $H_0: \mu_x = \mu_y$ 대 $H_1: \mu_x \neq \mu_y$ 입니다. 검정 통계량 $Z_0$는 기본적으로 다음과 같이 정의됩니다.

**[EN]** To see which of the two populations has the larger mean, or if the means are different, we perform a two-sided test. 
Our hypotheses are set as $H_0: \mu_x = \mu_y$ versus $H_1: \mu_x \neq \mu_y$. The test statistic $Z_0$ is fundamentally defined as follows.

$$ Z_0 = \frac{\bar{X} - \bar{Y} - (\mu_x - \mu_y)}{\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}} $$


**[KR]** 만약 귀무가설 $H_0$가 참이라면 (즉, 두 평균이 동일하다면 $\mu_x - \mu_y = 0$), 위 식의 분자가 지워지며 이 검정 통계량은 완벽한 표준 정규 분포 $Nor(0, 1)$를 따르게 됩니다. 
이전 장들과 동일한 논리에 따라, $\lvert Z_0 \rvert > z_{\alpha/2}$ 일 경우 우리는 귀무가설 $H_0$를 기각(Reject)하게 됩니다.

**[EN]** If $H_0$ is true (i.e., the means are equal), the term for the mean difference drops out, and the test statistic simplifies to follow a standard normal distribution $Nor(0, 1)$. 
$$ Z_0 = \frac{\bar{X} - \bar{Y}}{\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}} \sim Nor(0, 1) $$

Using the same reasoning as before, we reject $H_0$ if $\lvert Z_0 \rvert > z_{\alpha/2}$.

---

## 3. 단측 검정 (One-Sided Tests)

**[KR]** 동일한 통계적 추론 과정을 통해, 방향성이 있는 단측 검정 역시 다음과 같이 수행할 수 있습니다.
**[EN]** Using more of the same reasoning as before, we get the following one-sided tests.

*   **우측 검정 (Right-tailed test):** 
    가설이 $H_0: \mu_x \le \mu_y$ 대 $H_1: \mu_x > \mu_y$ 일 때, $Z_0 > z_\alpha$ 이면 $H_0$를 기각합니다.
*   **좌측 검정 (Left-tailed test):** 
    가설이 $H_0: \mu_x \ge \mu_y$ 대 $H_1: \mu_x < \mu_y$ 일 때, $Z_0 < -z_\alpha$ 이면 $H_0$를 기각합니다.

---

## 4. 실전 예제 (Practice Example)

**[KR]** 양측 검정 $H_0: \mu_x = \mu_y$ 대 $H_1: \mu_x \neq \mu_y$ 를 테스트하기 위해 다음과 같은 표본 데이터를 수집했다고 가정해 봅시다. (두 모집단의 분산은 알고 있다고 가정합니다.)
**[EN]** Suppose we want to test $H_0: \mu_x = \mu_y$ versus $H_1: \mu_x \neq \mu_y$, and we have the following data (where the variances are somehow known).

*   **집단 X 데이터:** $n = 10$, $\bar{X} = 824.9$, $\sigma_x^2 = 40$
*   **집단 Y 데이터:** $m = 10$, $\bar{Y} = 818.6$, $\sigma_y^2 = 50$

검정 통계량 $Z_0$ 값을 계산하면 다음과 같습니다.
Then we evaluate $Z_0$:
$$ Z_0 = \frac{824.9 - 818.6}{\sqrt{\frac{40}{10} + \frac{50}{10}}} = 2.10 $$


**[결론 / Conclusion]**
**[KR]** 유의수준 $\alpha = 0.05$ 를 적용할 때, $\lvert Z_0 \rvert = 2.10$ 은 기각역 기준인 $z_{0.025} = 1.96$ 보다 큽니다. 따라서 우리는 귀무가설 $H_0$를 기각하고 두 평균이 다르다고 결론 내리게 됩니다.
**[EN]** If $\alpha = 0.05$, then $\lvert Z_0 \rvert = 2.10 > z_{0.025} = 1.96$, and so we reject $H_0$.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-5 Two-Sample Normal Means Test with Known Variances-1" src="https://github.com/user-attachments/assets/2fb3bee9-ef21-4c3b-9da0-d75d0a91d823" />
  </div>
</details>
