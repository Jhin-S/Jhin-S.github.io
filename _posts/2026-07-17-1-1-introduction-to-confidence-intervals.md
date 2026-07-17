---
title: "1-1 Introduction to Confidence Intervals"
date: 2026-07-17 09:22:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, confidence-interval, point-estimator, lower-limit, upper-limit]
math: true
---

## 1. 신뢰 구간의 도입 (Introduction to Confidence Intervals)

**[KR]** 지금까지 우리는 미지의 모수(Parameter)를 알아내기 위해 표본 평균이나 표본 분산 같은 단 하나의 고정된 값인 '점 추정량(Point Estimator)'을 사용해 왔습니다[cite: 20]. 하지만 점 추정은 오차가 존재할 수밖에 없으므로, 특정한 확률(신뢰도)을 가지고 실제 모수를 포함할 것이라 기대되는 무작위 **'구간(Interval)'**을 제시하는 것이 훨씬 합리적입니다[cite: 20]. 
예를 들어, 표본 평균 $\bar{X}$를 바탕으로 모평균 $\mu$에 대한 95% 신뢰 구간을 설정한다면, 표준 정규 분포의 상위 2.5% 분위수인 $Z_{0.025}$를 활용하여 다음과 같이 표현할 수 있습니다[cite: 20].

$$
\mu \in \left[ \bar{X} - Z_{0.025}\sqrt{\frac{\sigma^2}{n}}, \bar{X} + Z_{0.025}\sqrt{\frac{\sigma^2}{n}} \right]
$$

**[EN]** Thus far, we have relied on 'Point Estimators'—single fixed values like the sample mean or sample variance—to estimate unknown parameters[cite: 20]. However, since point estimates inherently carry errors, it is much more rational to provide a random **'Interval'** that is expected to contain the true parameter with a specific probability (confidence level)[cite: 20]. 
For instance, if we establish a 95% confidence interval for the population mean $\mu$ based on the sample mean $\bar{X}$, we can use the 0.975 quantile of the standard normal distribution ($Z_{0.025}$) to express it as follows[cite: 20]:

$$
\mu \in \left[ \bar{X} - Z_{0.025}\sqrt{\frac{\sigma^2}{n}}, \bar{X} + Z_{0.025}\sqrt{\frac{\sigma^2}{n}} \right]
$$

---

## 2. 신뢰 구간의 수학적 정의 (Mathematical Definition)

**[KR]** 미지의 모수 $\theta$에 대한 $100(1-\alpha)\%$ 신뢰 구간은 다음의 확률 방정식을 만족하는 두 개의 확률 변수 $L$(하한)과 $U$(상한)로 정의됩니다[cite: 20]. 여기서 $1-\alpha$를 '신뢰 계수(Confidence Coefficient)'라고 부르며, 실제 모수가 $L$과 $U$ 사이에 존재할 확률이 $1-\alpha$ 임을 미리 지정해 두는 것입니다[cite: 20].

**[EN]** A $100(1-\alpha)\%$ confidence interval for an unknown parameter $\theta$ is defined by two random variables, $L$ (lower limit) and $U$ (upper limit), that satisfy the following probability equation[cite: 20]. Here, $1-\alpha$ is known as the 'Confidence Coefficient', meaning we specify in advance that there is a $1-\alpha$ probability the actual parameter lies strictly between $L$ and $U$[cite: 20].

$$
P(L \le \theta \le U) = 1 - \alpha
$$

* **양측 신뢰 구간 (Two-sided CI):** 상한과 하한이 모두 닫혀 있는 구간 $[L, U]$ 입니다[cite: 20]. (예: "대통령의 지지율은 $56\% \pm 3\%$ 이다.")[cite: 20].
* **단측 신뢰 구간 (One-sided CI):** 특정 방향의 경계만 설정하는 구간입니다.
  * **하한 단측 (One-sided lower CI):** $[L, \infty)$ 이며, $P(L \le \theta) = 1-\alpha$ 를 만족합니다[cite: 20].
  * **상한 단측 (One-sided upper CI):** $(-\infty, U]$ 이며, $P(\theta \le U) = 1-\alpha$ 를 만족합니다[cite: 20].

---

## 3. 올바른 통계적 해석: 골디락스와 곰 세 마리 (Proper Interpretation)

**[KR]** 신뢰 구간을 해석할 때 가장 주의해야 할 점은 모수($\theta$)가 움직이는 것이 아니라, 우리가 샘플을 뽑을 때마다 계산되는 구간($[L, U]$)이 무작위로 변한다는 사실입니다[cite: 20]. 
만약 우리가 독립적으로 100개의 관측치를 뽑아 신뢰 구간을 만드는 과정을 수없이 반복한다면, 어떤 구간은 모수보다 너무 높게 설정되어($\theta < L$) 빗나가고, 어떤 구간은 너무 낮게 설정되어($U < \theta$) 모수를 포함하지 못할 것입니다[cite: 20]. 하지만 전체 표본 횟수가 무한히 커진다면, 결국 전체 구간 중 딱 $1-\alpha$ 의 비율만큼은 진짜 모수를 완벽하게 품고 있는 **'딱 알맞은(Just right)'** 구간이 될 것입니다[cite: 20]. 마치 골디락스 동화처럼 말이죠[cite: 20].

**[EN]** The most critical point when interpreting confidence intervals is understanding that the parameter ($\theta$) does not move; rather, it is the interval ($[L, U]$) calculated from each new sample that randomly shifts[cite: 20].
If we repeatedly draw independent samples of 100 observations to construct these intervals countless times, some intervals will miss entirely by being too high ($\theta < L$), and some will miss by being too low ($U < \theta$)[cite: 20]. However, as the number of samples grows infinitely large, the proportion of intervals that perfectly contain the true parameter will approach exactly $1-\alpha$, proving to be **'Just right'**—much like the tale of the Three Little Bears[cite: 20].

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1 Introduction to Confidence Intervals-1" src="https://github.com/user-attachments/assets/3e3edca1-e44c-4419-9874-bbdbe203aebc" />
    <img width="1264" height="1635" alt="1-1 Introduction to Confidence Intervals-2" src="https://github.com/user-attachments/assets/5d8f3903-5b08-4883-993a-abdb28186829" />
  </div>
</details>
