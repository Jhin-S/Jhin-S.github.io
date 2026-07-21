---
title: "Mastering Statistics4 Hypothesis Test"
date: 2026-07-21 20:16:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, z-test, t-test, f-test, chi-squared, bernoulli]
math: true
---

이번 포스팅은 Module2의 Hypothesis Tests부분을 전부 정리해보았습니다. 전부 정리해보니 27페이지나 되네요. 손으로 필기하며 공부하는 것이 힘들고 오래걸리지만 필기야 말로 가장 확실한 학습이라고 생각됩니다. :)

## 2-1. 가설검정 입문 (Introduction to Hypothesis Testing)

**[KR]** 이 모듈의 핵심 목표는 표본 데이터를 수집하고 이를 분석하여 모집단에 대한 통계적으로 유효하고 타당한 결론을 내리는 것입니다. 가설 검정의 일반적인 접근 방식은 4단계로 구성됩니다. 첫째, 가설을 설정합니다(State a hypothesis). 둘째, 가설의 참/거짓을 검증하기 위한 검정 통계량을 선택합니다(Select a test statistic). 셋째, 관측된 데이터를 바탕으로 검정 통계량을 계산 및 평가합니다(Evaluate the test statistic). 넷째, 계산된 통계량이 가설의 기각(Reject) 또는 기각 실패(Fail to reject)를 지시하는지 해석합니다(Interpret results).

**[EN]** The core goal of this module is to study a population by collecting sample data and making statistically valid and sound conclusions based on that data. The general approach to hypothesis testing consists of four steps. First, state a hypothesis. Second, select a test statistic to verify whether the hypothesis is true or false. Third, evaluate and calculate the test statistic based on the observed data. Fourth, interpret the results to determine if the statistic suggests rejecting or failing to reject the hypothesis.

**[KR]** 가설은 모수(Parameter) 값에 대한 진술이나 주장을 의미합니다. 전체 모수 공간을 포괄할 수 있도록 귀무가설($H_0$, Null Hypothesis)과 대립가설($H_1$, Alternative Hypothesis)을 설정합니다. 귀무가설은 '현재 상태(Status quo)'를 의미하며, 반증되기 전까지는 마지못해 유지하는 가설입니다. 예를 들어 양측 검정은 $H_0: \mu = \mu_0$ 대 $H_1: \mu \neq \mu_0$ 로 설정되며, 단측 검정은 $H_0: \mu \le \mu_0$ 대 $H_1: \mu > \mu_0$ 형태로 설정됩니다.

**[EN]** A hypothesis is a statement or claim about a parameter value. We set up a null hypothesis ($H_0$) and an alternative hypothesis ($H_1$) to cover the entire parameter space. The null hypothesis represents the "status quo" and is grudgingly maintained until proven otherwise. For example, a two-sided test is set as $H_0: \mu = \mu_0$ vs $H_1: \mu \neq \mu_0$, while a one-sided test takes forms like $H_0: \mu \le \mu_0$ vs $H_1: \mu > \mu_0$.

---

## 2-2. 우리가 범할 수 있는 오류들 (The Errors of Our Ways)

**[KR]** 가설 검정 과정에서 우리는 다음과 같은 두 가지 치명적인 오류를 범할 수 있습니다. 
*   **제1종 오류 (Type I Error):** 귀무가설($H_0$)이 실제로 참임에도 불구하고 거짓이라고 잘못 기각하는 오류입니다.
*   **제2종 오류 (Type II Error):** 귀무가설($H_0$)이 실제로 거짓임에도 불구하고 참이라고 잘못 채택하는 오류입니다.

**[EN]** During hypothesis testing, we can commit two critical errors.
*   **Type I Error:** Incorrectly rejecting the null hypothesis ($H_0$) when it is actually true.
*   **Type II Error:** Incorrectly failing to reject the null hypothesis ($H_0$) when it is actually false.

**[KR]** 제1종 오류가 발생할 확률 $\alpha$를 검정의 '크기' 또는 '유의수준(Level of Significance)'이라 부릅니다. 제2종 오류가 발생할 확률은 $\beta$이며, 통상적으로 제1종 오류가 더 심각한 것으로 간주됩니다. 가설 검정의 '검정력(Power)'은 $1 - \beta$ 로 정의되며, 이 값이 높을수록 좋은 검정입니다.

**[EN]** The probability of committing a Type I error, $\alpha$, is called the "size" or "level of significance" of the test. The probability of a Type II error is $\beta$, and a Type I error is generally considered more severe. The "power" of a hypothesis test is defined as $1 - \beta$, and higher power is always better.

---

## 2-3. 모분산을 알 때의 정규모평균 검정 (Normal Mean Test with Known Variance)

**[KR]** 모분산 $\sigma^2$을 알고 있는 정규 모집단에서 모평균 $\mu$를 검정할 때, 검정 통계량 $Z_0$는 다음과 같이 정의됩니다. 귀무가설이 참일 때 이 통계량은 표준 정규 분포 $Nor(0, 1)$를 따릅니다.

**[EN]** When testing the population mean $\mu$ of a normal population with a known variance $\sigma^2$, the test statistic $Z_0$ is defined as follows. If the null hypothesis is true, this statistic follows a standard normal distribution $Nor(0, 1)$.

$$ Z_0 = \frac{\bar{X} - \mu_0}{\sqrt{\sigma^2/n}} $$


**[KR]** 양측 검정의 경우 $\lvert Z_0 \rvert > z_{\alpha/2}$ 이면 $H_0$를 기각하며, 이 영역을 '기각역(Critical region)'이라 합니다. 또한, 가설을 기각하게 만드는 최소 유의수준을 **p-value (유의확률)**라고 정의하며, 양측 검정의 p-value 공식은 $p = 2(1 - \Phi(\lvert Z_0 \rvert))$ 입니다.

**[EN]** For a two-sided test, we reject $H_0$ if $\lvert Z_0 \rvert > z_{\alpha/2}$, and this area is called the "critical region" (or rejection region). Furthermore, the smallest significance level that leads to the rejection of the hypothesis is defined as the **p-value**, and the formula for a two-sided test is $p = 2(1 - \Phi(\lvert Z_0 \rvert))$.

---

## 2-4. 모분산을 알 때의 정규모평균 검정: 설계 (Normal Mean Test with Known Variance: Design)

**[KR]** 가설 검정 설계란, 목표하는 제1종 오류 확률 $\alpha$와 제2종 오류 확률 $\beta$를 모두 만족하기 위해 필요한 표본 크기 $n$을 수학적으로 산출하는 것을 뜻합니다. 실제 모평균($\mu_1$)과 가설상의 평균($\mu_0$)의 차이를 $\delta = \mu_1 - \mu_0$ 라고 할 때, 필요한 표본 크기는 다음과 같습니다.

**[EN]** Hypothesis test design refers to mathematically calculating the required sample size $n$ to satisfy both the target Type I error probability $\alpha$ and Type II error probability $\beta$. Letting the difference between the true mean ($\mu_1$) and hypothesized mean ($\mu_0$) be $\delta = \mu_1 - \mu_0$, the necessary sample size is given by.

$$ n \approx \frac{\sigma^2(z_{\alpha/2} + z_\beta)^2}{\delta^2} $$


---

## 2-5. 모분산을 알 때 두 독립표본 정규모평균 검정 (Two-Sample Normal Means Test with Known Variances)

**[KR]** 서로 독립적인 두 집단에서 모분산 $\sigma_x^2$와 $\sigma_y^2$를 알고 있을 때, 두 모평균이 서로 다른지($H_0: \mu_x = \mu_y$ vs $H_1: \mu_x \neq \mu_y$) 확인하는 양측 검정의 통계량은 다음과 같습니다. 

**[EN]** When we know the population variances $\sigma_x^2$ and $\sigma_y^2$ of two independent groups, the test statistic for a two-sided test to see if the two means are different ($H_0: \mu_x = \mu_y$ vs $H_1: \mu_x \neq \mu_y$) is as follows.

$$ Z_0 = \frac{\bar{X} - \bar{Y}}{\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}} \sim Nor(0, 1) $$


**[KR]** 단일 표본일 때와 동일하게 $\lvert Z_0 \rvert > z_{\alpha/2}$ 이면 $H_0$를 기각합니다.

**[EN]** Just like in the single-sample case, we reject $H_0$ if $\lvert Z_0 \rvert > z_{\alpha/2}$.

---

## 2-6. 모분산을 모를 때의 정규모평균 검정 (Normal Mean Test with Unknown Variance)

**[KR]** 현실적으로 모분산 $\sigma^2$을 모르는 경우가 많으므로, 이를 표본 분산 $S^2$으로 대체합니다. 이때 검정 통계량 $T_0$는 자유도 $n-1$인 t-분포를 따르게 됩니다.

**[EN]** Since the population variance $\sigma^2$ is realistically unknown in most cases, we replace it with the sample variance $S^2$. The test statistic $T_0$ then follows a t-distribution with $n-1$ degrees of freedom.

$$ T_0 = \frac{\bar{X} - \mu_0}{\sqrt{S^2/n}} \sim t(n-1) $$


**[KR]** 양측 검정의 경우 $\lvert T_0 \rvert > t_{\alpha/2, n-1}$ 이면 $H_0$를 기각합니다. 이때의 p-value는 CDF 역함수 규칙에 의해 $p = 2(1 - F_{n-1}(\lvert T_0 \rvert))$ 로 계산됩니다.

**[EN]** For a two-sided test, we reject $H_0$ if $\lvert T_0 \rvert > t_{\alpha/2, n-1}$. The p-value is calculated as $p = 2(1 - F_{n-1}(\lvert T_0 \rvert))$ according to the CDF inverse rule.

---

## 2-7. 모분산을 모를 때 두 독립표본 정규모평균 검정 (Two-Sample Normal Means Tests with Unknown Variances)

**[KR]** 두 독립 표본의 모분산을 모를 경우, 분산의 동일성 여부에 따라 검정 방법이 나뉩니다.
*   **합동 t-검정 (Pooled t-test):** 두 모분산이 같다고 가정할 때($\sigma_x^2 = \sigma_y^2$), 합동 분산 추정량 $S_p^2$를 사용합니다. 통계량 $T_0$는 자유도 $n+m-2$를 따릅니다.
*   **근사 t-검정 (Approximate t-test):** 두 모분산이 다르다고 가정할 때($\sigma_x^2 \neq \sigma_y^2$), 웰치(Welch)의 근사 자유도 $\nu$를 사용하는 통계량 $T_0^*$를 적용합니다.

**[EN]** When the population variances of two independent samples are unknown, the testing method depends on whether the variances are assumed equal.
*   **Pooled t-test:** Assuming equal variances ($\sigma_x^2 = \sigma_y^2$), we use the pooled variance estimator $S_p^2$. The statistic $T_0$ follows $n+m-2$ degrees of freedom.
*   **Approximate t-test:** Assuming unequal variances ($\sigma_x^2 \neq \sigma_y^2$), we apply the statistic $T_0^*$ using Welch's approximate degrees of freedom $\nu$.

---

## 2-8. 대응 표본을 이용한 두 정규모평균 검정 (Two-Sample Normal Means Test with Paired Observations)

**[KR]** 관측치가 독립적이지 않고 '쌍(Pair)'을 이루는 경우(예: 쌍둥이 실험, 동일인의 전후 비교), 각 쌍의 차이 $D_i = X_i - Y_i$ 를 계산하여 단일 표본 t-검정과 완전히 동일한 수식 전개를 거칩니다. 

**[EN]** When observations are not independent but paired (e.g., twin experiments, before-and-after for the same person), we calculate the pair-wise difference $D_i = X_i - Y_i$ and apply the exact same mathematical development as the single-sample t-test.

$$ T_0 = \frac{\bar{D}}{\sqrt{S_d^2/n}} \sim t(n-1) $$


---

## 2-9. 정규분산 검정 (Normal Variance Test)

**[KR]** 단일 정규 모집단의 분산 $\sigma^2$이 가설상의 특정 분산 $\sigma_0^2$과 일치하는지 검정할 때는 카이제곱($\chi^2$) 분포를 활용합니다.

**[EN]** When testing whether the variance $\sigma^2$ of a single normal population matches a specific hypothesized variance $\sigma_0^2$, we utilize the Chi-squared ($\chi^2$) distribution.

$$ \chi_0^2 = \frac{(n-1)S^2}{\sigma_0^2} \sim \chi^2(n-1) $$


**[KR]** 양측 검정의 기각역은 $\chi_0^2 < \chi_{1-\alpha/2, n-1}^2$ 또는 $\chi_0^2 > \chi_{\alpha/2, n-1}^2$ 입니다.

**[EN]** The rejection region for a two-sided test is $\chi_0^2 < \chi_{1-\alpha/2, n-1}^2$ or $\chi_0^2 > \chi_{\alpha/2, n-1}^2$.

---

## 2-10. 두 독립표본 정규분산 검정 (Two-Sample Normal Variances Test)

**[KR]** 두 정규 모집단이 동일한 분산을 가지는지($\sigma_x^2 = \sigma_y^2$) 검정할 때는 두 표본 분산의 비율을 통해 F-분포를 따르는 검정 통계량을 사용합니다.

**[EN]** When testing whether two normal populations have the same variance ($\sigma_x^2 = \sigma_y^2$), we use a test statistic that follows an F-distribution by taking the ratio of the two sample variances.

$$ F_0 = \frac{S_x^2}{S_y^2} \sim F(n-1, m-1) $$


**[KR]** 양측 검정의 기각역은 $F_0 < \frac{1}{F_{\alpha/2, m-1, n-1}}$ 또는 $F_0 > F_{\alpha/2, n-1, m-1}$ 로 설정됩니다.

**[EN]** The rejection region for a two-sided test is set as $F_0 < \frac{1}{F_{\alpha/2, m-1, n-1}}$ or $F_0 > F_{\alpha/2, n-1, m-1}$.

---

## 2-11. 베르누이 비율 검정 (Bernoulli Proportion Test)

**[KR]** 성공 확률 파라미터 $p$에 대한 단일 표본 가설 검정입니다. 표본 크기 $n$이 충분히 크다면 중심극한정리(CLT)에 의해 통계량은 표준 정규 분포에 근사합니다.

**[EN]** This is a single-sample hypothesis test for the success probability parameter $p$. If the sample size $n$ is sufficiently large, the statistic approximates the standard normal distribution due to the Central Limit Theorem (CLT).

$$ Z_0 = \frac{Y - np_0}{\sqrt{np_0(1-p_0)}} = \frac{\bar{X} - p_0}{\sqrt{p_0(1-p_0)/n}} $$


**[KR]** 양측 검정에 필요한 표본 크기 설계 공식은 다음과 같습니다.

**[EN]** The sample size design formula needed for a two-sided test is as follows.

$$ n \approx \left[ \frac{z_{\alpha/2}\sqrt{p_0 q_0} + z_\beta\sqrt{pq}}{p - p_0} \right]^2 $$


---

## 2-12. 두 독립표본 베르누이 비율 검정 (Two-Sample Bernoulli Proportions Test)

**[KR]** 두 독립적인 베르누이 집단의 성공 확률 차이($p_x - p_y$)를 검정합니다. 귀무가설($H_0: p_x = p_y$)이 참일 때를 가정하여 두 표본 데이터를 합친 **합동 비율 추정량(Pooled estimator)** $\hat{p}$를 구하여 검정 통계량 $Z_0$를 산출합니다.

**[EN]** We test the difference in success probabilities ($p_x - p_y$) between two independent Bernoulli populations. Assuming the null hypothesis ($H_0: p_x = p_y$) is true, we calculate a **pooled estimator** $\hat{p}$ by combining both sample data to derive the test statistic $Z_0$.

$$ \hat{p} = \frac{\sum X_i + \sum Y_j}{n + m} $$

$$ Z_0 = \frac{\bar{X} - \bar{Y}}{\sqrt{\hat{p}(1-\hat{p})\left[\frac{1}{n} + \frac{1}{m}\right]}} \approx Nor(0, 1) $$


**[KR]** 예를 들어, 버거 폴-A와 맥웬디스의 고객 리뷰 만족도를 비교하여 맥웬디스의 비율이 통계적으로 유의미하게 더 높은지 검증할 때 이 식을 사용합니다.

**[EN]** For example, this equation is used when comparing the customer review satisfaction of Burger Fol-A and McWendy's to verify if McWendy's proportion is statistically significantly higher.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-01" src="https://github.com/user-attachments/assets/d179c0e9-288f-4256-8550-cc1bea5c09aa" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-02" src="https://github.com/user-attachments/assets/68c5e71b-fe78-4d06-b7d3-50614b74ac2c" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-03" src="https://github.com/user-attachments/assets/bf7a35a7-3c3e-44d6-b2ab-542858cda963" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-04" src="https://github.com/user-attachments/assets/ad901d82-60e3-4f97-b912-21d60ae2ba26" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-05" src="https://github.com/user-attachments/assets/dd5bbe17-7f6b-449a-a9be-06fc00398b0a" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-06" src="https://github.com/user-attachments/assets/019bd255-780d-4d92-a499-8d4846443b8f" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-07" src="https://github.com/user-attachments/assets/b269ecf5-f19b-4b2f-8c33-b36debd8104f" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-08" src="https://github.com/user-attachments/assets/3b362a66-2412-46e9-9eef-2e1c89f1b1d7" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-09" src="https://github.com/user-attachments/assets/33285f8b-661e-4021-b804-36ae4508d3ed" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-10" src="https://github.com/user-attachments/assets/b5efdbb0-c3f3-4b12-a7dd-0fc884b88bf4" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-11" src="https://github.com/user-attachments/assets/e8ca0946-c7a7-4cb2-bafc-5de1e8f9917e" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-12" src="https://github.com/user-attachments/assets/65943906-6024-45c3-a60e-aa460994e995" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-13" src="https://github.com/user-attachments/assets/5abf489a-1ea7-4a89-b6de-e903e571d56c" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-14" src="https://github.com/user-attachments/assets/cc883ec7-ebbb-4e82-8886-208e780e576e" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-15" src="https://github.com/user-attachments/assets/019815f4-1719-40ea-bbb8-50c1c3f039d2" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-16" src="https://github.com/user-attachments/assets/55f56292-a78b-4b43-bc8f-ef655b972a9f" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-17" src="https://github.com/user-attachments/assets/28176963-c88c-44b0-8585-f3082a2b2f20" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-18" src="https://github.com/user-attachments/assets/93601d35-234d-4497-a6f1-3766597ef458" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-19" src="https://github.com/user-attachments/assets/f818ee66-502c-4d43-9941-fe9f89d16d9c" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-20" src="https://github.com/user-attachments/assets/431bd86c-368d-4e64-aec8-f43c73ae8b6e" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-21" src="https://github.com/user-attachments/assets/bffc952d-49db-4d06-a7fc-9380831d5b79" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-22" src="https://github.com/user-attachments/assets/bff11fb2-354d-4c48-9e8f-c620a5ef339a" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-23" src="https://github.com/user-attachments/assets/420092be-695e-4ff5-bd1f-5c86004d1c63" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-24" src="https://github.com/user-attachments/assets/ac9e92cc-ea83-4bbd-a301-219f40ea86a4" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-25" src="https://github.com/user-attachments/assets/7be10354-3dc5-4476-a662-c06c826dceaf" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-26" src="https://github.com/user-attachments/assets/53eabd0c-4554-45dc-97d0-6e35b6fb0b51" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Hypothesis Test-27" src="https://github.com/user-attachments/assets/d500e4e4-4f53-4f38-a3f5-a511b1285da4" />
  </div>
</details>
