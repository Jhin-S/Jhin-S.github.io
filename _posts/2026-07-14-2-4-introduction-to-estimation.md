---
title: "2-4 Introduction to Estimation"
date: 2026-07-14 16:55:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, estimation, point-estimator, statistic, parameters]
math: true
---

## 1. 통계량의 엄밀한 정의 (Definition of a Statistic)

**[KR]** 통계학에서 **통계량(Statistic)**이란 우리가 현실에서 수집한 표본 데이터(관측치 $X_1, X_2, \dots, X_n$)들만으로 계산할 수 있는 함수를 의미합니다. 여기서 가장 중요한 수학적 제약 조건은, 수식 안에 우리가 절대 알 수 없는 '미지의 모수(Unknown parameters, 예: 모평균 $\mu$ 등)'가 단 하나라도 포함되어서는 안 된다는 것입니다. 
예를 들어, 표본 데이터만으로 구할 수 있는 표본 평균 $\bar{X}$나 표본 분산 $S^2$은 완벽한 통계량입니다. 하지만 $\frac{\bar{X}-\mu}{\sigma}$ 같은 수식은 미지의 모수 $\mu$와 $\sigma$에 의존하고 있으므로 통계량이라고 부를 수 없습니다.

**[EN]** In statistics, a **Statistic** is strictly defined as a function formulated solely from observed sample data ($X_1, X_2, \dots, X_n$). The most critical mathematical constraint here is that the function must not explicitly depend on any 'unknown parameters' (like the true population mean $\mu$).
For instance, the sample mean $\bar{X}$ and the sample variance $S^2$ are perfect statistics because they are calculated purely from available data. However, an expression like $\frac{\bar{X}-\mu}{\sigma}$ cannot be called a statistic because it relies on the unknown population parameters $\mu$ and $\sigma$.

---

## 2. 확률 변수로서의 통계량 (Statistics as Random Variables)

**[KR]** 통계량은 고정된 숫자가 아닙니다. 표본을 새로 추출할 때마다 관측되는 데이터가 달라지기 때문에 통계량의 값 역시 매번 요동치게 됩니다. 즉, **통계량 그 자체도 거대한 확률 분포를 따르는 하나의 '확률 변수(Random Variable)'**입니다.

**[EN]** A statistic is never a fixed number. Because the observed data changes every time a new sample is drawn, the value of the statistic inevitably fluctuates. Therefore, **a statistic itself is fundamentally a 'Random Variable'** that follows its own overarching probability distribution.

---

## 3. 점 추정량 (Point Estimator)

**[KR]** 통계학의 궁극적인 목표 중 하나는 표본을 통해 모집단의 숨겨진 진짜 성질(모수, Parameters)을 알아내는 것입니다. 
우리가 미지의 모수 $\theta$를 추측(Estimate)하기 위해 특정한 통계량 $T(X_1, \dots, X_n)$를 도구로 사용하기로 결정했다면, 이때 이 통계량을 미지의 모수에 대한 **점 추정량(Point Estimator)**이라고 부릅니다.
* **대표적인 예시:** 모평균 $\mu$를 추정하기 위한 점 추정량으로는 주로 표본 평균 $\bar{X}$를 사용하며, 모분산 $\sigma^2$을 추정하기 위한 점 추정량으로는 표본 분산 $S^2$을 사용합니다.

**[EN]** One of the ultimate goals of statistics is to uncover the hidden true properties (Parameters) of a population using sample data.
When we decide to use a specific statistic $T(X_1, \dots, X_n)$ as a tool to guess (estimate) an unknown parameter $\theta$, this statistic is formally called a **Point Estimator** for $\theta$.
* **Classic Examples:** The sample mean $\bar{X}$ is typically used as a point estimator for the true population mean $\mu$, and the sample variance $S^2$ is often used as a point estimator for the true population variance $\sigma^2$.

---

## 4. 좋은 추정량의 조건 (Properties of a Good Estimator)

**[KR]** 수많은 통계량 중에서 미지의 모수를 추정하기 위한 '완벽한 대표 선수'를 뽑으려면 다음 두 가지 이상적인 조건을 만족해야 합니다.
1. **불편성 (Unbiasedness):** 추정량의 기댓값(평균적인 결괏값)이 우리가 추정하려는 실제 모수의 타겟 값과 정확하게 일치해야 합니다 ($E[T(X)] = \theta$). 즉, 영점 조준이 완벽하게 되어 있어야 합니다.
2. **효율성 (Low Variance):** 추정량의 분산이 최대한 작아야 합니다. 이는 표본을 뽑을 때마다 추정값이 타겟에서 크게 벗어나지 않고 안정적으로 중심에 몰려 있어야 함을 의미합니다.

**[EN]** To select the 'perfect representative' among countless statistics for estimating an unknown parameter, the estimator should ideally satisfy two major properties:
1. **Unbiasedness:** The expected value of the estimator should be exactly equal to the true target value of the parameter it is trying to estimate ($E[T(X)] = \theta$). In other words, its sights must be perfectly zeroed in on the target.
2. **Efficiency (Low Variance):** The estimator should possess the lowest possible variance. This ensures that every time a sample is drawn, the estimated value does not wildly fluctuate but consistently lands tightly around the target center.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-4 Introduction to Estimation-1" src="https://github.com/user-attachments/assets/cd6d8db3-f8c2-40c7-bd09-51046bcd7044" />
  </div>
</details>
