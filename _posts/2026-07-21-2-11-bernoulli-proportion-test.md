---
title: "2-11 Bernoulli Proportion Test"
date: 2026-07-21 20:00:22 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, bernoulli-distribution, proportion, sample-size]
math: true
---

## 1. 베르누이 비율 검정 통계량 (Bernoulli Proportion Test Statistic)

**[KR]** 우리는 독립적이고 동일하게 분포된 베르누이 시행 $X_1, X_2, \dots, X_n \sim Bern(p)$ 에서 성공 매개변수 $p$에 대한 가설을 검정하는 데 관심이 있습니다.
**[EN]** We are interested in testing hypotheses about the success parameter $p$ from independent and identically distributed Bernoulli trials $X_1, X_2, \dots, X_n \sim Bern(p)$.

**[KR]** 양측 검정의 가설은 사용자가 지정한 가설적 비율 $p_0$를 바탕으로 $H_0: p = p_0$ 대 $H_1: p \neq p_0$ 로 설정됩니다. 확률 변수 $Y = \sum_{i=1}^n X_i \sim Bin(n, p)$ 를 정의할 때, 검정 통계량 $Z_0$는 다음과 같습니다.
**[EN]** The two-sided test hypotheses are set as $H_0: p = p_0$ versus $H_1: p \neq p_0$ based on a user-specified hypothesized proportion $p_0$. Letting the random variable $Y = \sum_{i=1}^n X_i \sim Bin(n, p)$, the test statistic $Z_0$ is as follows.

$$Z_0 \equiv \frac{Y - n p_0}{\sqrt{n p_0 (1-p_0)}} = \frac{\bar{X} - p_0}{\sqrt{p_0(1-p_0)/n}}$$


**[KR]** 만약 귀무가설 $H_0$가 참이라면, 중심극한정리(CLT)에 의해 검정 통계량은 $Z_0 \approx Nor(0, 1)$ 로 근사할 수 있습니다. 단, 이 근사가 성립하려면 표본 크기 $n$이 충분히 커야 하며(최소 50 이상), 비율이 0이나 1에 너무 가깝지 않도록 $np \ge 5$ 와 $nq \ge 5$ 조건을 만족해야 합니다. ($n$이 크지 않다면 번거로운 이항 분포표를 직접 사용해야 합니다.)
**[EN]** If $H_0$ is true, the central limit theorem (CLT) implies that the test statistic approximates $Z_0 \approx Nor(0, 1)$. For this to work, $n$ needs to be large (at least 50), and both $np \ge 5$ and $nq \ge 5$ must be satisfied so that $p$ isn't too close to 0 or 1. (If $n$ isn't very big, you may have to use tedious Binomial tables instead.)

---

## 2. 가설 검정 규칙 및 예제 (Testing Rules and Example)

**[KR]** 양측 검정의 경우 $\lvert Z_0 \rvert > z_{\alpha/2}$ 이면 $H_0$를 기각합니다. 단측 검정의 규칙은 다음과 같습니다.
**[EN]** For the two-sided test, we reject $H_0$ if $\lvert Z_0 \rvert > z_{\alpha/2}$. The rules for one-sided tests are as follows.

*   **[KR] 우측 검정 ($H_0: p \le p_0$ vs $H_1: p > p_0$):** $Z_0 > z_\alpha$ 일 때 기각합니다.
*   **[EN] Right-sided test ($H_0: p \le p_0$ vs $H_1: p > p_0$):** Reject $H_0$ if $Z_0 > z_\alpha$.
*   **[KR] 좌측 검정 ($H_0: p \ge p_0$ vs $H_1: p < p_0$):** $Z_0 < -z_\alpha$ 일 때 기각합니다.
*   **[EN] Left-sided test ($H_0: p \ge p_0$ vs $H_1: p < p_0$):** Reject $H_0$ if $Z_0 < -z_\alpha$.

**[KR] 📝 실전 예제 1:** 어떤 반도체 샘플 200개 중에서 불량품이 4개 나왔습니다. 불량 확률이 $0.06$ 미만인지 유의수준 $0.05$ 에서 확인해 봅시다 ($H_0: p \ge 0.06$ vs $H_1: p < 0.06$).
**[EN] 📝 Practice Example 1:** In 200 samples of a certain semiconductor, there were only 4 defectives. Let's conduct a test at level $0.05$ to prove that the probability of a defective is less than $0.06$ ($H_0: p \ge 0.06$ vs $H_1: p < 0.06$).

**[KR]** $p$가 0에 가깝기 때문에 중심극한정리를 작동시키기 위해 200개라는 많은 관측치가 필요했습니다. 검정 통계량을 계산하면 $Z_0 = \frac{4 - 200(0.06)}{\sqrt{200(0.06)(0.94)}} = -2.357$ 입니다. 임계값 $-z_{0.05} = -1.645$ 와 비교할 때, $-2.357 < -1.645$ 이므로 $H_0$를 기각하며, 실제 불량률 $p$는 $0.06$ 미만인 것으로 보입니다.
**[EN]** Since $p$ is close to 0, we really did need to take a lot of observations (200) in order for the CLT to work. Calculating the test statistic gives $Z_0 = \frac{4 - 200(0.06)}{\sqrt{200(0.06)(0.94)}} = -2.357$. Since $-2.357 < -z_{0.05} = -1.645$, we reject $H_0$, meaning it seems $p$ really is $< 0.06$.

---

## 3. 표본 크기 선택 (Sample-Size Selection)

**[KR]** 제1종 오류 확률 $\alpha$와, 실제 비율이 $p$일 때의 제2종 오류 확률 $\beta$를 모두 통제할 수 있는 검정의 표본 크기 $n$을 설계할 수 있습니다.
**[EN]** We can design a test's sample size $n$ such that the Type I error probability is $\alpha$ and the Type II error probability when the true proportion is $p$ is $\beta$.

**[KR]** 양측 검정에 필요한 표본 크기 공식은 다음과 같습니다. (단, 공간 절약을 위해 $q \equiv 1-p$, $q_0 \equiv 1-p_0$ 로 둡니다. 단측 검정의 경우 분자의 $z_{\alpha/2}$ 대신 $z_\alpha$를 사용합니다.)
**[EN]** The necessary sample size formula for a two-sided test is as follows. (Note that to save space, we let $q \equiv 1-p$ and $q_0 \equiv 1-p_0$. For a one-sided test, use $z_\alpha$ instead of $z_{\alpha/2}$.)

$$n \approx \left[ \frac{z_{\alpha/2}\sqrt{p_0 q_0} + z_\beta\sqrt{p q}}{p - p_0} \right]^2$$


**[KR] 📝 실전 예제 2:** 특정 알레르기 약의 효과에 대한 가설 $H_0: p = 0.8$ 대 $H_1: p \neq 0.8$ 을 유의수준 $\alpha = 0.05$ 로 검정합니다. 만약 실제 효과가 $p_1 = 0.7$ 로 저조할 때 이를 놓치는 오류를 $\beta = 0.10$ 으로 방어하고자 합니다.
**[EN] 📝 Practice Example 2:** We hypothesize about a particular allergy medication's effectiveness as $H_0: p = 0.8$ vs $H_1: p \neq 0.8$ at level $\alpha = 0.05$. We want to protect against poor performance by setting Type II error to $\beta = 0.10$ in the special case that $p_1 = 0.7$.

**[KR]** 공식에 값들을 대입하면 다음과 같이 계산됩니다.
**[EN]** Plugging the values into the formula yields the following.

$$n \approx \left[ \frac{1.96\sqrt{(0.8)(0.2)} + 1.28\sqrt{(0.7)(0.3)}}{0.7 - 0.8} \right]^2 = 187.8$$


**[KR]** 따라서 약 188개의 관측치가 필요합니다.
**[EN]** Therefore, we need to take about 188 observations.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-11 Bernoulii Proportion Test-1" src="https://github.com/user-attachments/assets/df3a5938-8df7-4d6e-8364-763a80b9a5a7" />
    <img width="1264" height="1635" alt="2-11 Bernoulii Proportion Test-2" src="https://github.com/user-attachments/assets/e0e46a30-3d10-46a8-bf44-dac720a22e85" />
    <img width="1264" height="1635" alt="2-11 Bernoulii Proportion Test-3" src="https://github.com/user-attachments/assets/dba63039-0b45-4de9-a317-a846b3a9b6c6" />
    <img width="1264" height="1635" alt="2-11 Bernoulii Proportion Test-4" src="https://github.com/user-attachments/assets/d60b87ed-13c8-4f00-8a1d-d4ce0d80db8d" />
  </div>
</details>
