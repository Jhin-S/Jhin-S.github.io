---
title: "2-4 Normal Mean Test with Known Variance: Design"
date: 2026-07-21 13:08:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, sample-size, type-I-error, type-II-error]
math: true
---

## 1. 가설 검정 설계의 목표 (Goal of Design)

**[KR]** 이 단원의 핵심 목표는 제1종 오류($\le \alpha$)와 제2종 오류($= \beta$)에 대한 제약 조건을 모두 만족하는 완벽한 양측 검정을 설계하는 것입니다. 여기서 "설계(Design)"란, 실제 모평균 $\mu$가 사용자가 지정한 특정 대립 평균값 $\mu_1$과 일치하는 특수한 상황에서, 이 두 가지 오류의 한계를 충족시키기 위해 최소 몇 개의 표본($n$)을 추출해야 하는지 수학적으로 결정하는 과정을 의미합니다. 
실제 평균 $\mu_1$이 귀무가설의 평균 $\mu_0$에 가까울수록 두 상황을 구별하기가 훨씬 더 어려워지므로, 이를 정확히 판별하기 위해서는 더 많은 작업량(더 큰 표본 크기 $n$)이 필요합니다.

**[EN]** The core goal of this section is to design a two-sided test that strictly satisfies constraints on both Type I error ($\le \alpha$) and Type II error ($= \beta$). By "design," we refer to the process of determining exactly how many observations ($n$) are required to meet these error bounds, specifically for the case where the true mean $\mu$ happens to equal a user-specified alternative value $\mu_1$. 
Generally, the closer $\mu_1$ is to $\mu_0$, the harder it is to distinguish between the two close cases, which means we need to do more work (i.e., a higher $n$) to achieve the required precision.

---

## 2. 표본 크기 산출 정리 (Theorem for Sample Size)

**[KR]** 실제 평균과 귀무가설 평균의 차이를 $\delta \equiv \mu - \mu_0 = \mu_1 - \mu_0$ 로 정의합시다. (일반성을 잃지 않기 위해 $\mu_1 > \mu_0$ 라고 가정합니다.) $\alpha$와 $\beta$의 설계 요구사항을 달성하기 위한 표본 크기 $n$은 다음 공식을 통해 산출됩니다.

**[EN]** Let us define the difference between the actual and hypothesized means as $\delta \equiv \mu - \mu_0 = \mu_1 - \mu_0$. (Without loss of generality, we will assume $\mu_1 > \mu_0$.) The sample size $n$ required to achieve both the $\alpha$ and $\beta$ design requirements is given by the following formula.

*   **양측 검정 (Two-sided test):**
    $$ n \approx \frac{\sigma^2(z_{\alpha/2} + z_\beta)^2}{\delta^2} $$
*   **단측 검정 (One-sided test):** (양측 검정 공식에서 $z_{\alpha/2}$ 대신 $z_\alpha$를 사용합니다.)
    $$ n \approx \frac{\sigma^2(z_\alpha + z_\beta)^2}{\delta^2} $$

---

## 3. 공식의 수학적 증명 (Proof of the Theorem)

**[KR]** 양측 검정 공식은 제2종 오류 $\beta$를 평가하는 과정에서 유도됩니다. $\beta$는 실제 평균이 $\mu_1$일 때 귀무가설 기각에 실패할 확률입니다.
**[EN]** The formula for the two-sided test is derived by evaluating the Type II error $\beta$. $\beta$ is the probability of failing to reject $H_0$ when the true mean is actually $\mu_1$.

$$ \beta = P(\text{Fail to reject } H_0 \mid H_0 \text{ false }(\mu = \mu_1 > \mu_0)) $$
$$ \beta = P(-z_{\alpha/2} \le Z_0 \le z_{\alpha/2} \mid \mu = \mu_1) $$

검정 통계량 $Z_0$를 확장하고, 새로운 표준 정규 변수 $Z \equiv \frac{\bar{X} - \mu_1}{\sigma/\sqrt{n}} \sim Nor(0, 1)$ 를 정의하여 식을 재구성합니다.
By expanding the test statistic $Z_0$ and defining a new standard normal variable $Z \equiv \frac{\bar{X} - \mu_1}{\sigma/\sqrt{n}} \sim Nor(0, 1)$, we can restructure the equation.

$$ \beta = P\left(-z_{\alpha/2} - \frac{\sqrt{n}\delta}{\sigma} \le Z \le z_{\alpha/2} - \frac{\sqrt{n}\delta}{\sigma}\right) $$
$$ \beta = \Phi\left(z_{\alpha/2} - \frac{\sqrt{n}\delta}{\sigma}\right) - \Phi\left(-z_{\alpha/2} - \frac{\sqrt{n}\delta}{\sigma}\right) $$

여기서 $-z_{\alpha/2} < 0$ 이고 $\delta > 0$ 이므로 두 번째 $\Phi(\cdot)$ 항은 거의 0에 가까워져 무시할 수 있습니다.
Since $-z_{\alpha/2} < 0$ and $\delta > 0$, the second $\Phi(\cdot)$ term approaches zero and can be practically ignored.

$$ \beta \approx \Phi\left(z_{\alpha/2} - \frac{\sqrt{n}\delta}{\sigma}\right) $$

표준 정규 분포의 대칭성에 의해 $\Phi^{-1}(\beta) = -z_\beta$ 가 성립하므로, 역함수를 취하고 $n$에 대해 정리하면 최종 공식이 완성됩니다.
Due to the symmetry of the standard normal distribution, $\Phi^{-1}(\beta) = -z_\beta$ holds true. By taking the inverse and solving for $n$, the final formula is completed.

$$ -z_\beta \approx z_{\alpha/2} - \frac{\sqrt{n}\delta}{\sigma} \implies n \approx \frac{\sigma^2(z_{\alpha/2} + z_\beta)^2}{\delta^2} $$

---

## 4. 실전 예제 (Practice Example)

**[KR]** 9세 어린이들의 체중이 표준편차 $\sigma = 4$ 인 정규 분포를 따른다고 가정해 봅시다. 귀무가설 $H_0: \mu = 60$ 과 대립가설 $H_1: \mu \neq 60$ 에 대해 테스트를 진행하려고 합니다. 만약 실제 평균이 $\mu_1 = 62$ 일 때, $\alpha = 0.05$ 와 $\beta = 0.05$ 의 제약 조건을 모두 만족시키려면 최소 몇 개의 표본을 수집해야 할까요?

**[EN]** Suppose the weights of 9-year-old kids follow a normal distribution with $\sigma = 4$. We wish to test $H_0: \mu = 60$ versus $H_1: \mu \neq 60$. If the true mean happens to equal $\mu_1 = 62$, how many observations should we take to satisfy both $\alpha = 0.05$ and $\beta = 0.05$?

*   차이($\delta$) 계산: $\delta = 62 - 60 = 2$
*   표준 정규 분포 분위수: $z_{0.025} = 1.96$, $z_{0.05} = 1.645$
*   공식 대입: 
    $$ n \approx \frac{16}{4}(1.96 + 1.645)^2 = 51.98 $$

**[결론 / Conclusion]**
**[KR]** 계산 결과에 따라 우리는 설계 요구사항을 충족하기 위해 **약 52개의 관측치**가 필요하다는 것을 알 수 있습니다.
**[EN]** Based on the calculation, we conclude that we need **about 52 observations** to meet the design requirements.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-4 Normal Mean Test with Known Variance_ Design-1" src="https://github.com/user-attachments/assets/ea650f3a-41c2-442a-bb0d-c5b503ad6a31" />
    <img width="1264" height="1635" alt="2-4 Normal Mean Test with Known Variance_ Design-2" src="https://github.com/user-attachments/assets/b627c9f5-84f3-4755-8677-85a07d810ad6" />
    <img width="1264" height="1635" alt="2-4 Normal Mean Test with Known Variance_ Design-3" src="https://github.com/user-attachments/assets/b1f62c7c-0e54-4fe7-b912-f9c7f5e2288f" />
  </div>
</details>
