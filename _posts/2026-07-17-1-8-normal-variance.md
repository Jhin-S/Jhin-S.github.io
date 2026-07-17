---
title: "1-8 Normal Variance"
date: 2026-07-17 10:08:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, normal-distribution, variance, confidence-interval, chi-squared]
math: true
---

## 1. 모분산 추정의 필요성과 피벗 통계량 (Introduction & Pivot Quantity)

**[KR]** 어떤 시스템이 얼마나 일관성 있게 작동하는지, 즉 '변동성(Variability)'의 크기를 파악하고자 할 때는 모평균이 아닌 모분산 $\sigma^2$에 대한 신뢰 구간을 설정해야 합니다. 정규 분포 $Nor(\mu, \sigma^2)$를 따르는 표본 데이터 $X_1, \dots, X_n$이 주어졌을 때, 표본 분산 $S^2$은 카이제곱 분포와 밀접한 관계를 맺습니다. 
이러한 성질을 활용하여, 미지의 $\sigma^2$을 포함하지만 그 분포는 $\sigma^2$에 영향을 받지 않는 다음과 같은 피벗(Pivot) 통계량을 구성할 수 있습니다.

**[EN]** To understand how much variability we can expect from a system, we must establish a confidence interval for the population variance $\sigma^2$ rather than the mean. Given sample data $X_1, \dots, X_n$ following a normal distribution $Nor(\mu, \sigma^2)$, the sample variance $S^2$ is intrinsically linked to the chi-squared distribution. 
Leveraging this property, we can construct the following pivot statistic that contains the unknown $\sigma^2$ but whose distribution does not depend on it.

* **피벗 통계량:**
  $$ \frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1) $$


---

## 2. 모분산의 신뢰 구간 도출 (Derivation of Confidence Interval)

**[KR]** 위에서 찾은 카이제곱 피벗 통계량을 확률 부등식에 대입하여 식을 정리하면 됩니다. 카이제곱 분포의 분위수를 활용하여 부등식을 세우고 역수를 취해 부등호 방향을 뒤집는 대수적 조작을 거치면 다음과 같은 과정이 전개됩니다.

**[EN]** We can formulate a probability inequality by substituting the chi-squared pivot statistic found above. Utilizing the quantiles of the chi-squared distribution, taking the reciprocal, and flipping the inequality signs, we unfold the following algebraic process.

$$ 1 - \alpha = P\left(\chi^2_{1-\alpha/2, n-1} \le \frac{(n-1)S^2}{\sigma^2} \le \chi^2_{\alpha/2, n-1}\right) $$


$$ = P\left(\frac{(n-1)S^2}{\chi^2_{\alpha/2, n-1}} \le \sigma^2 \le \frac{(n-1)S^2}{\chi^2_{1-\alpha/2, n-1}}\right) $$


* **$100(1-\alpha)\%$ 양측 신뢰 구간 (Two-sided CI):**
  $$ \sigma^2 \in \left[ \frac{(n-1)S^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)S^2}{\chi^2_{1-\alpha/2, n-1}} \right] $$


**[통계적 특징]** 
1. 모분산의 신뢰 구간은 우리가 계산한 표본 분산 $S^2$ 값에 직접적으로 비례합니다.
2. 이 신뢰 구간 공식에는 미지의 모평균 $\mu$에 대한 어떠한 정보나 참조도 필요하지 않습니다.

---

## 3. 단측 신뢰 구간 (One-sided Confidence Intervals)

**[KR]** 모분산이 특정 임계치를 넘는지 혹은 그 이하인지 한쪽 방향만 알고 싶을 때는 상/하한 단측 신뢰 구간을 사용합니다. 양측으로 확률을 나누지 않으므로 $\alpha/2$ 대신 $\alpha$를 사용합니다.

**[EN]** When we only need to know whether the population variance exceeds or falls below a certain threshold, we use one-sided confidence intervals. Since we are not splitting the probability into two tails, we use $\alpha$ instead of $\alpha/2$.

* **$100(1-\alpha)\%$ 하한 단측 (Lower CI):** 
  $$ \frac{(n-1)S^2}{\chi^2_{\alpha, n-1}} \le \sigma^2 $$

* **$100(1-\alpha)\%$ 상한 단측 (Upper CI):** 
  $$ \sigma^2 \le \frac{(n-1)S^2}{\chi^2_{1-\alpha, n-1}} $$


---

## 4. 실전 예제: IQ 테스트 점수의 변동성 (Practice Example)

**[KR]** 25명의 사람들이 IQ 테스트를 치렀고, 이들의 점수 분포가 정규 분포를 따른다고 가정해 봅시다. 수집한 데이터의 표본 분산이 $S^2 = 100$으로 나왔을 때, 모분산 $\sigma^2$에 대한 **95% 상한 단측 신뢰 구간(Upper CI)**을 구해봅시다.

**[EN]** Suppose 25 people take an IQ test, and we assume their scores are normally distributed. If the calculated sample variance is $S^2 = 100$, let's find the **95% upper one-sided confidence interval** for the population variance $\sigma^2$.

* $n = 25$ 이므로 자유도는 $24$ 입니다. 
* 카이제곱 분포표에서 $\chi^2_{0.95, 24}$ 값을 찾으면 $13.85$ 가 됩니다.
* 상한 단측 신뢰 구간 공식에 대입하면 다음과 같습니다.

$$ \sigma^2 \le \frac{(25-1) \times 100}{\chi^2_{0.95, 24}} = \frac{2400}{13.85} = 173.3 $$


**[결론]** 따라서 95%의 신뢰 수준에서 해당 집단의 IQ 점수 모분산은 $173.3$ 이하일 것이라고 결론 내릴 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-8 Normal Variance-1" src="https://github.com/user-attachments/assets/b117ea4c-9da2-4060-ba80-029804cc151e" />
    <img width="1264" height="1635" alt="1-8 Normal Variance-2" src="https://github.com/user-attachments/assets/e16388f6-c875-48b5-ad27-78381aa4012e" />
  </div>
</details>
