---
title: "2-3 Two-Sample Normal Means Tests with known Variances"
date: 2026-07-21 13:06:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, normal-distribution, z-test, p-value]
math: true
---

## 1. 모분산을 아는 경우의 양측 검정 (Two-sided Test with Known Variance)

**[KR]** 모분산 $\sigma^2$이 알려져 있다는 다소 비현실적인 가정하에, 정규 모집단의 평균 $\mu$에 대한 가설 검정을 수행해 봅시다. 검정하고자 하는 양측 검정(단순 검정)의 가설은 $H_0: \mu = \mu_0$ 대 $H_1: \mu \neq \mu_0$ 로 설정됩니다. 표본 평균 $\bar{X}$가 귀무가설의 $\mu_0$와 '유의미하게 다를 경우' 우리는 $H_0$를 기각하게 됩니다. 
이를 판별하기 위해 귀무가설이 참이라고 가정($E[\bar{X}] = \mu_0$, $Var(\bar{X}) = \sigma^2/n$)하고 다음과 같은 표준 정규 분포 $Nor(0, 1)$를 따르는 검정 통계량 $Z_0$를 정의합니다.

**[EN]** Under the somewhat unrealistic assumption that the population variance $\sigma^2$ is known, let's perform a hypothesis test on the mean $\mu$ of a normal distribution. The hypotheses for a two-sided test (also known as a simple test) are set as $H_0: \mu = \mu_0$ versus $H_1: \mu \neq \mu_0$. If the sample mean $\bar{X}$ is 'significantly different' from $\mu_0$, we will reject $H_0$. 
To determine this, assuming $H_0$ is true ($E[\bar{X}] = \mu_0$, $Var(\bar{X}) = \sigma^2/n$), we define the test statistic $Z_0$ which follows a standard normal distribution $Nor(0, 1)$.

$$ Z_0 \equiv \frac{\bar{X} - \mu_0}{\sigma/\sqrt{n}} $$


**[KR] 의사결정 규칙:**
$Z_0$ 값이 구간 $[-z_{\alpha/2}, z_{\alpha/2}]$ 를 벗어난다면, 귀무가설이 참일 때 일어나기 매우 희박한 일이 발생한 것입니다. 따라서 $\lvert Z_0 \rvert > z_{\alpha/2}$ 일 때 $H_0$를 기각(Reject)하며, 이 영역을 **기각역(Critical region)**이라고 부릅니다. 반대로 $\lvert Z_0 \rvert \le z_{\alpha/2}$ 라면 **채택역(Acceptance region)**에 머물게 됩니다. 이때 제1종 오류의 확률은 정확히 유의수준 $\alpha$와 일치합니다.

**[EN] Decision Rule:**
If the value of $Z_0$ falls outside the interval $[-z_{\alpha/2}, z_{\alpha/2}]$, it is highly unlikely assuming $H_0$ is true. Therefore, we reject $H_0$ if $\lvert Z_0 \rvert > z_{\alpha/2}$, and this area is called the **rejection region (or critical region)**. Conversely, if $\lvert Z_0 \rvert \le z_{\alpha/2}$, we are in the **acceptance region**. The probability of a Type I error in this case perfectly matches the significance level $\alpha$.

---

## 2. 단측 검정 (One-sided Tests)

**[KR]** 만약 관심 있는 방향이 한쪽뿐이라면 단측 검정을 수행하며, 이때는 양측으로 면적을 나누지 않으므로 $z_{\alpha/2}$ 대신 $z_\alpha$를 사용합니다.
**[EN]** If we are only interested in one direction, we perform a one-sided test, and since we do not split the area, we use $z_\alpha$ instead of $z_{\alpha/2}$.

* **우측 검정 (Right-tailed test):** 
  가설 $H_0: \mu \le \mu_0$ vs $H_1: \mu > \mu_0$ 일 때, $Z_0 > z_\alpha$ 이면 $H_0$를 기각합니다.
* **좌측 검정 (Left-tailed test):** 
  가설 $H_0: \mu \ge \mu_0$ vs $H_1: \mu < \mu_0$ 일 때, $Z_0 < -z_\alpha$ 이면 $H_0$를 기각합니다.

---

## 3. P-값의 정의와 계산 (P-value Definition and Calculation)

**[KR]** **P-값(p-value)**이란 귀무가설 $H_0$를 기각할 수 있는 가장 작은 유의수준 $\alpha$를 의미합니다. 통계학 연구자들은 자신이 수행한 검정의 결과를 보고할 때 거의 항상 이 p-값을 함께 명시합니다. P-값은 누적 분포 함수(CDF)인 $\Phi$를 이용하여 다음과 같이 계산됩니다.

**[EN]** The **p-value** is defined as the smallest level of significance $\alpha$ that would lead to the rejection of $H_0$. Researchers routinely report the p-values for any statistical tests they conduct. The p-value is calculated using the cumulative distribution function (CDF) $\Phi$ as follows.

* **양측 검정 (Two-sided test):** $p = 2(1 - \Phi(\lvert Z_0 \rvert))$
* **우측 검정 (One-sided, $>$):** $p = 1 - \Phi(Z_0)$
* **좌측 검정 (One-sided, $<$):** $p = \Phi(Z_0)$

---

## 4. 실전 예제 (Practice Example)

**[KR]** 9세 어린이 25명의 체중을 조사한 결과, 표본 평균이 $\bar{X} = 62$ 로 나타났습니다. 체중이 정규 분포를 따르며 모표준편차가 $\sigma = 4$ 로 알려져 있을 때, 모평균이 60인지 아닌지 유의수준 $\alpha = 0.05$ 에서 양측 검정을 수행해 봅시다.

**[EN]** We examined the weights of 25 nine-year-old kids and found the sample mean to be $\bar{X} = 62$. Assuming the weights are normally distributed and the population standard deviation is known to be $\sigma = 4$, let's test the hypothesis that the mean weight is 60 at a significance level of $\alpha = 0.05$.

1. **가설 설정:** $H_0: \mu = 60$ vs $H_1: \mu \neq 60$
2. **검정 통계량 계산:**
   $$ Z_0 = \frac{62 - 60}{4 / \sqrt{25}} = 2.5 $$
 
3. **결과 해석:** $\lvert Z_0 \rvert = 2.5$ 는 $z_{0.025} = 1.96$ 보다 크므로 귀무가설 $H_0$를 기각합니다.
4. **P-값 계산:** $p = 2(1 - \Phi(2.5)) = 0.0124$

**(참고: 만약 유의수준을 $\alpha = 0.01$ 로 더 낮춘다면, 기각 기준이 $z_{0.005} = 2.58$ 로 높아져서 $2.5 < 2.58$ 이 되므로 기각에 실패하게 됩니다. 즉, $\alpha$가 작을수록 귀무가설을 기각하기가 더 "어려워집니다.")**

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-3 Two-Sample Normal Means Tests with known Variances-1" src="https://github.com/user-attachments/assets/8b4baea7-5bfc-44df-b376-7f6768f67b75" />
    <img width="1264" height="1635" alt="2-3 Two-Sample Normal Means Tests with known Variances-2" src="https://github.com/user-attachments/assets/fadb38c4-3517-4906-933b-bc558758472d" />
    <img width="1264" height="1635" alt="2-3 Two-Sample Normal Means Tests with known Variances-3" src="https://github.com/user-attachments/assets/f0366e65-5cfa-473b-8521-18b4f282080e" />
  </div>
</details>
