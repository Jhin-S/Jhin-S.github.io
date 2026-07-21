---
title: "2-1 Introduction to Hypothesis Testing"
date: 2026-07-21 12:52:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, null-hypothesis, alternative-hypothesis, test-statistic]
math: true
---

## 1. 가설 검정의 목표와 4단계 접근법 (Goal and General Approach)

**[KR]** 가설 검정의 핵심 목표는 표본 데이터를 수집하여 이를 분석하고, 그 결과를 바탕으로 전체 모집단에 대한 통계적으로 타당하고 건전한 결론을 도출하는 것입니다. 이를 위한 일반적인 통계적 접근 방식은 다음의 4단계로 이루어집니다.
* **1단계:** 검증하고자 하는 가설을 설정합니다.
* **2단계:** 설정한 가설이 참인지 거짓인지 판별하기 위한 검정 통계량(Test statistic)을 선택합니다.
* **3단계:** 관측된 표본 데이터를 바탕으로 해당 검정 통계량의 값을 계산하고 평가합니다.
* **4단계:** 계산된 통계량이 가설을 기각(Reject)할 것을 시사하는지, 아니면 기각에 실패(Fail to reject)할 것을 시사하는지 최종 결과를 해석합니다.

**[EN]** The primary goal of hypothesis testing is to study a population by collecting data and making statistically sound, valid conclusions about that population based on the collected data. The general approach to achieve this consists of four distinct steps.
* **Step 1:** State a specific hypothesis regarding the population.
* **Step 2:** Select an appropriate test statistic to evaluate whether or not the stated hypothesis is true.
* **Step 3:** Evaluate and calculate the test statistic based entirely on the observations that have been collected.
* **Step 4:** Interpret the final results to determine if the test statistic suggests that you should reject or fail to reject your initial hypothesis.

---

## 2. 귀무가설과 대립가설의 설정 (Setting Up Hypotheses)

**[KR]** 가설이란 모집단의 파라미터(Parameter) 값에 대한 진술이나 주장이며, 우리는 이 주장을 증명하거나 반증하기 위해 테스트를 수행합니다. 전체 파라미터 공간을 완벽하게 포괄하기 위해 우리는 귀무가설($H_0$)과 대립가설($H_1$)을 설정합니다. 
귀무가설($H_0$)은 일종의 '현재 상태(Status quo)'를 의미하며, 이것이 반드시 진실이라서가 아니라 반증될 때까지는 마지못해 유지하는 보수적인 입장입니다. 반면 대립가설($H_1$)은 실질적인 증거가 확보되어야만 채택할 수 있는 새롭고 급진적인 주장입니다. 쉽게 말해, 귀무가설은 "유죄가 입증될 때까지는 무죄(Innocent until proven guilty)"라는 법적 원칙과 똑같이 작동합니다.

**[EN]** Hypotheses are essentially statements or claims regarding parameter values, and we perform tests to either prove or disprove these claims. We set up a null hypothesis ($H_0$) and an alternative hypothesis ($H_1$) in a way that covers the entire parameter space. 
The null hypothesis ($H_0$) represents the conservative "status quo"; it is not necessarily true, but we grudgingly stick with it until it is definitively proven otherwise. The alternative hypothesis ($H_1$), on the other hand, is the news or the radical claim that requires substantial evidence to be supported. Think of $H_0$ as the concept of "innocent until proven guilty".

* **양측 검정 (Two-sided test):** 평균이 특정 값 $\mu_0$ 와 같은지 다른지 판별합니다 ($H_0: \mu = \mu_0$ vs $H_1: \mu \neq \mu_0$).
* **단측 검정 (One-sided test):** 한쪽 방향으로의 치우침을 판별합니다 ($H_0: \mu \le \mu_0$ vs $H_1: \mu > \mu_0$ 또는 $H_0: \mu \ge \mu_0$ vs $H_1: \mu < \mu_0$).

---

## 3. 검정 통계량 선택과 평가의 논리 (Selecting and Evaluating the Test Statistic)

**[KR]** 가설을 검정하기 위해 우리는 확률 변수인 검정 통계량을 선택해야 합니다. 예를 들어, 모분산 $\sigma^2$을 아는 상황이라면 $z_{obs} = \frac{\bar{X}-\mu_0}{\sigma/\sqrt{n}}$ 를 사용하고, 모른다면 $t_{obs} = \frac{\bar{X}-\mu_0}{S/\sqrt{n}}$ 를 사용합니다. 
가설 검정의 핵심 논리 흐름은 다음과 같습니다. 먼저 수집한 데이터를 바탕으로 통계량을 계산한 뒤, 귀무가설($H_0$)이 '참'이라고 굳게 가정합니다. 그 가정이 참일 때 우리가 수집한 표본 결과가 나올 확률을 수학적으로 계산하여 $H_0$가 얼마나 타당한지(Plausible) 결정합니다. 이 확률이 낮다면 $H_0$를 기각하고 $H_1$을 선택하며, 확률이 높다면 기각에 실패하게 됩니다.

**[EN]** To test the hypothesis, we must select a test statistic, which is a random variable used to determine if $H_0$ is true. For example, if the variance $\sigma^2$ is known, we use $z_{obs} = \frac{\bar{X}-\mu_0}{\sigma/\sqrt{n}}$; if unknown, we use $t_{obs} = \frac{\bar{X}-\mu_0}{S/\sqrt{n}}$. 
The core logic of evaluating the test statistic follows this path. We calculate the statistic based on the sample data and then strictly assume that $H_0$ (the status quo) is true. We then determine the probability of obtaining our sample result under the assumption that $H_0$ is true to see if $H_0$ remains plausible. If this probability is remarkably low, we reject $H_0$ and select $H_1$; if it is high, we fail to reject $H_0$.

---

## 4. 실전 예제 및 결과 해석 (Practice Example and Interpretation)

**[KR]** 새로운 약의 대사 시간이 기존의 15분보다 짧아졌는지 테스트한다고 가정해 봅시다. 우리는 $H_0: \mu \ge 15$ 와 $H_1: \mu < 15$ 로 가설을 세웠습니다. 
표본 데이터($n=20, \bar{X}=14.88, S=0.333$)를 바탕으로 검정 통계량을 계산하면 $t_{obs} = -1.61$ 이 도출됩니다. 
자유도가 19인 t-분포표를 보면, 유의수준 0.05에 해당하는 분위수는 $-1.729$ 이고 유의수준 0.10에 해당하는 분위수는 $-1.328$ 입니다. 우리의 관측치 $-1.61$이 나올 확률($p$-value)은 0.05와 0.10 사이에 존재합니다 ($0.05 < p < 0.10$). 
**[결론]** 따라서 유의수준 0.10 에서는 귀무가설을 공식적으로 기각($-1.61 < -1.328$)할 수 있지만, 더 엄격한 유의수준 0.05 에서는 기각에 실패($-1.61 > -1.729$)하게 됩니다.

**[EN]** Let's assume we are testing whether the metabolism time for a new drug is less than the current 15 minutes. We set our hypotheses as $H_0: \mu \ge 15$ and $H_1: \mu < 15$. 
Based on our sample data ($n=20, \bar{X}=14.88, S=0.333$), the calculated test statistic is $t_{obs} = -1.61$. 
Looking at the t-distribution table with 19 degrees of freedom, the quantile for a 0.05 significance level is $-1.729$, and for a 0.10 level, it is $-1.328$. The probability of getting our observed value of $-1.61$ falls between 0.05 and 0.10 ($0.05 < p < 0.10$). 
**[Conclusion]** Formally, we would reject $H_0$ at the 0.10 level (since $-1.61 < -1.328$), but we would fail to reject $H_0$ at the stricter 0.05 level (since $-1.61 > -1.729$).

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-1 Introduction to Hypothesis Testing-1" src="https://github.com/user-attachments/assets/81966933-1681-47e0-8893-650db41a84a8" />
    <img width="1264" height="1635" alt="2-1 Introduction to Hypothesis Testing-2" src="https://github.com/user-attachments/assets/e787a719-eb19-40c1-859d-cf9d799e38fb" />
    <img width="1264" height="1635" alt="2-1 Introduction to Hypothesis Testing-3" src="https://github.com/user-attachments/assets/715e022b-cd24-4073-a087-5ca1c32e0d1b" />
    <img width="1264" height="1635" alt="2-1 Introduction to Hypothesis Testing-4" src="https://github.com/user-attachments/assets/7a65d741-0d46-439e-9377-6473ccc74d70" />
  </div>
</details>
