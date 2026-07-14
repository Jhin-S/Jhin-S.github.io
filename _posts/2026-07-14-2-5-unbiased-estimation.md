---
title: "2-5 Unbiased Estimation"
date: 2026-07-14 17:15:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, estimation, unbiased-estimator, sample-mean, sample-variance, efficiency]
math: true
---

## 1. 불편 추정량의 정의 (Definition of Unbiased Estimation)

**[KR]** 통계학에서 어떤 점 추정량이 타겟으로 삼은 미지의 모수를 얼마나 정확히 가리키고 있는지를 평가하는 첫 번째 잣대가 바로 **불편성(Unbiasedness)**입니다. 어떤 통계량 $T(X)$의 기댓값을 구했을 때, 그 값이 추정하고자 하는 실제 모수 $\theta$와 완벽하게 일치한다면($E[T(X)] = \theta$), 우리는 이 통계량을 편향되지 않은 '불편 추정량(Unbiased Estimator)'이라고 부릅니다. 쉽게 말해, 표본을 여러 번 뽑아 추정치들을 구한 뒤 이들의 평균을 내면 결국 진짜 정답에 도달하게 된다는 뜻입니다.

**[EN]** In statistics, the primary criterion for evaluating how accurately a point estimator targets an unknown parameter is **Unbiasedness**. If the expected value of a statistic $T(X)$ is perfectly equal to the actual parameter $\theta$ it is trying to estimate ($E[T(X)] = \theta$), we call this statistic an 'Unbiased Estimator'. Simply put, if you draw multiple samples, calculate the estimates, and average them out, you will eventually hit the exact true answer without any systematic directional bias.

---

## 2. 대표적인 불편 추정량 (Classic Unbiased Estimators)

**[KR]** 우리가 흔히 사용하는 표본 평균과 표본 분산은 불편성을 만족하도록 정교하게 설계된 대표적인 통계량입니다.
* **표본 평균 ($\bar{X}$):** 모평균 $\mu$를 추정하기 위한 가장 완벽한 불편 추정량입니다. 기댓값의 선형성에 의해 $E[\bar{X}] = \mu$가 아주 자연스럽게 성립합니다.
* **표본 분산 ($S^2$):** 모분산 $\sigma^2$을 추정하기 위한 불편 추정량입니다. 표본 분산을 계산할 때 데이터의 개수인 $n$이 아니라 **$n-1$**로 나누어 주는 이유가 바로 이 불편성을 맞추기($E[S^2] = \sigma^2$) 위함입니다. 만약 $n$으로 나누면 값이 미세하게 작아지는 편향(Bias)이 발생하게 됩니다. (주의: 표본 분산은 불편 추정량이지만, 표본 표준편차 $S$는 모표준편차 $\sigma$에 대한 불편 추정량이 아닙니다.)

**[EN]** The commonly used sample mean and sample variance are prime examples of statistics meticulously designed to satisfy unbiasedness.
* **Sample Mean ($\bar{X}$):** It is the most perfect unbiased estimator for the population mean $\mu$. By the linearity of expectations, $E[\bar{X}] = \mu$ naturally holds true.
* **Sample Variance ($S^2$):** It is the unbiased estimator for the population variance $\sigma^2$. The fundamental reason we divide by **$n-1$** instead of $n$ when calculating the sample variance is precisely to guarantee this unbiasedness ($E[S^2] = \sigma^2$). Dividing by $n$ would systematically underestimate the true variance. (Caution: While $S^2$ is unbiased for $\sigma^2$, the sample standard deviation $S$ is *not* strictly unbiased for $\sigma$.)

---

## 3. 세 가지 추정량 비교 예제 (Good, Better, Ugly Estimators)

**[KR]** 평균뿐만 아니라 특정 분포의 파라미터를 추정할 때도 불편 추정량을 만들 수 있습니다. 데이터 $X_1, \dots, X_n$ 이 미지의 최댓값 $\theta$를 가지는 균등 분포 $Unif(0, \theta)$를 따른다고 가정해 봅시다. 여기서 $\theta$를 알아맞히기 위해 세 가지 불편 추정량을 제안해 볼 수 있습니다.

**[EN]** We can construct unbiased estimators for distribution-specific parameters, not just means. Suppose data $X_1, \dots, X_n$ follow a uniform distribution $Unif(0, \theta)$ with an unknown maximum $\theta$. To guess $\theta$, we can propose three different unbiased estimators.

### 1) 쓸만한 추정량 (The "Good" Estimator)
균등 분포의 평균이 $\theta/2$ 라는 점에 착안하여, 표본 평균에 2를 곱해줍니다.
$$Y_1 = 2\bar{X}$$
$E[2\bar{X}] = 2(\theta/2) = \theta$ 이므로 훌륭한 불편 추정량입니다.

### 2) 더 나은 추정량 (The "Better" Estimator)
데이터 중 가장 큰 값(최댓값, $M = \max X_i$)을 찾은 뒤, 여기에 $\frac{n+1}{n}$ 이라는 보정치를 곱해줍니다.
$$Y_2 = \frac{n+1}{n} \max_{1 \le i \le n} X_i$$
최댓값 $M$의 누적 분포 함수와 확률 밀도 함수를 유도하여 기댓값을 구해보면 이 역시 완벽히 $\theta$가 나옵니다. 그런데 분산을 비교해 보면, **$Y_2$의 분산이 $Y_1$의 분산보다 압도적으로 작습니다.** 즉, 언제나 타겟 근처에 훨씬 안정적으로 꽂히는 '더 나은(Efficient)' 추정량입니다.

### 3) 기괴한 추정량 (The "Ugly" Estimator)
동전을 던져서 앞면이 나오면 $12\bar{X}$를, 뒷면이 나오면 $-8\bar{X}$를 추정값으로 삼는다고 가정해 봅시다.
$$E[Y_3] = \frac{1}{2}(12E[\bar{X}]) + \frac{1}{2}(-8E[\bar{X}]) = 2E[\bar{X}] = \theta$$
놀랍게도 기댓값은 정확히 $\theta$가 나오므로 이 역시 '불편 추정량'의 자격을 가집니다. 하지만 길이나 최댓값을 나타내는 $\theta$가 음수가 될 수도 있는 말도 안 되는 추정량입니다. 

**[결론 / Conclusion]**
'기괴한 추정량' 예시가 보여주듯, 그저 기댓값이 정답과 같다는 **'불편성' 하나만으로는 훌륭한 통계량이 될 수 없습니다.** 우리는 불편성을 기본으로 갖추되, 분산이 가장 작아서 안정적인(Better Estimator 같은) 추정량을 찾아야만 합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-5 Unbiased Estimation-1" src="https://github.com/user-attachments/assets/12cfc45c-63db-4ffa-b90d-7ae66aa5b5d0" />
    <img width="1264" height="1635" alt="2-5 Unbiased Estimation-2" src="https://github.com/user-attachments/assets/f643917b-5577-4ca3-865c-eb1301e4eb9f" />
    <img width="1264" height="1635" alt="2-5 Unbiased Estimation-3" src="https://github.com/user-attachments/assets/0a16f216-fb5b-4a2d-b86e-c493c3fc72fc" />
  </div>
</details>
