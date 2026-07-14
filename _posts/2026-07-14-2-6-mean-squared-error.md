---
title: "2-6 Mean Squared Error"
date: 2026-07-14 17:30:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, estimation, mse, mean-squared-error, bias, variance, efficiency]
math: true
---

## 1. 평균 제곱 오차와 편향 (Mean Squared Error & Bias)

**[KR]** 어떤 추정량이 훌륭한지 평가할 때, 단순히 '불편성(Unbiasedness)'이나 '분산(Variance)' 중 하나만 고려하는 것은 불완전할 수 있습니다. 이 두 가지 요소를 동시에 종합적으로 평가하는 통계학의 가장 강력하고 보편적인 지표가 바로 **평균 제곱 오차(Mean Squared Error, MSE)**입니다. 
MSE는 추정량 $T(X)$가 실제 타겟 모수 $\theta$로부터 얼마나 떨어져 있는지를 제곱하여 기댓값을 취한 것입니다. 이때 추정량의 평균적인 결괏값과 실제 모수의 차이를 **편향(Bias)**이라고 정의합니다.

**[EN]** When evaluating the quality of an estimator, relying solely on 'Unbiasedness' or 'Variance' can be incomplete. The most robust and universal metric in statistics that comprehensively evaluates both simultaneously is the **Mean Squared Error (MSE)**. 
MSE is defined as the expected value of the squared difference between the estimator $T(X)$ and the actual target parameter $\theta$. The difference between the expected value of the estimator and the true parameter is formally defined as **Bias**.

* **평균 제곱 오차 (MSE):** $MSE(T(X)) \equiv E[(T(X) - \theta)^2]$
* **편향 (Bias):** $Bias(T(X)) \equiv E[T(X)] - \theta$

---

## 2. MSE 공식의 분해 (Decomposition of MSE)

**[KR]** MSE 공식을 전개해 보면 아주 우아하고 직관적인 수학적 결과를 얻을 수 있습니다. 놀랍게도 MSE는 통계량의 **'분산'과 '편향의 제곱'을 더한 값과 완벽히 일치**합니다. 
이는 아주 중요한 사실을 시사합니다. 아무리 편향이 0(완벽한 불편 추정량)이라도 분산이 너무 크면 좋은 추정량이 될 수 없습니다. 반대로, 약간의 편향(Bias)이 존재하더라도 분산이 압도적으로 작다면 MSE 관점에서는 훨씬 더 훌륭하고 실용적인 추정량으로 평가받을 수 있습니다.

**[EN]** Expanding the MSE formula yields a highly elegant and intuitive mathematical result. Surprisingly, MSE is perfectly equal to the sum of the estimator's **'Variance' and the 'Square of its Bias'**. 
This implies a crucial point: even if the bias is strictly zero (a perfect unbiased estimator), a massive variance makes it a poor estimator. Conversely, an estimator with a slight bias but an overwhelmingly smaller variance can be considered a vastly superior and more practical estimator from the MSE perspective.

* **증명 과정 (Proof):**
  
$$
MSE(T(X)) = E[(T(X) - \theta)^2] = E[T^2] - 2\theta E[T] + \theta^2
$$
  
$$
= (E[T^2] - (E[T])^2) + ((E[T])^2 - 2\theta E[T] + \theta^2)
$$
  
$$
= Var(T(X)) + (E[T(X)] - \theta)^2 = Var(T(X)) + [Bias(T(X))]^2
$$

---

## 3. 상대적 효율성과 실전 예제 (Relative Efficiency & Example)

**[KR]** 두 개의 추정량 $T_1$과 $T_2$ 중 어떤 것이 더 나은지 비교하기 위해 두 추정량의 MSE 비율을 구하는 것을 **상대적 효율성(Relative Efficiency)**이라고 합니다. 비율 $MSE(T_2) / MSE(T_1)$ 이 $1$보다 작다면, $T_2$의 오차가 더 작다는 뜻이므로 $T_2$를 선택하는 것이 합리적입니다.

**[EN]** To compare which of two estimators, $T_1$ and $T_2$, is better, we calculate the ratio of their MSEs, known as **Relative Efficiency**. If the ratio $MSE(T_2) / MSE(T_1)$ is less than $1$, it indicates that $T_2$ has a smaller error, making it the more rational choice.

**[비교 예제]**
* **추정량 A:** 편향 = 3, 분산 = 10 $\implies MSE(A) = 3^2 + 10 = 19$
* **추정량 B:** 편향 = -2, 분산 = 14 $\implies MSE(B) = (-2)^2 + 14 = 18$
* **결론:** 추정량 B가 분산은 더 크지만, 편향이 작아 최종적인 MSE 값이 더 낮으므로 **추정량 B가 더 우수한 추정량**입니다.

---

## 4. 불편 추정량 간의 MSE 비교 (MSE of Unbiased Estimators)

**[KR]** 이전 단원에서 살펴보았던 균등 분포 $Unif(0, \theta)$의 미지의 모수 $\theta$를 추정하는 상황으로 돌아가 봅시다. 우리가 제안했던 두 추정량 $Y_1 = 2\bar{X}$와 $Y_2 = \frac{n+1}{n}\max X_i$는 모두 편향이 0인 '불편 추정량(Bias = 0)'이었습니다. 편향이 0이므로, 이들의 MSE는 곧 '분산' 자체와 완벽하게 동일해집니다.

**[EN]** Let's return to the previous scenario of estimating the unknown parameter $\theta$ of a uniform distribution $Unif(0, \theta)$. Both proposed estimators, $Y_1 = 2\bar{X}$ and $Y_2 = \frac{n+1}{n}\max X_i$, were 'Unbiased Estimators', meaning their Bias = 0. Since the bias is zero, their MSEs are exactly equal to their respective variances.

* $MSE(Y_1) = Var(Y_1) = \frac{\theta^2}{3n}$
* $MSE(Y_2) = Var(Y_2) = \frac{\theta^2}{n(n+2)}$

**결론:** $n$이 커질수록 $Y_2$의 분모가 $Y_1$의 분모보다 이차함수 스케일로 훨씬 커지게 됩니다. 즉, $Y_2$의 평균 제곱 오차(MSE)가 압도적으로 작아지므로, **$Y_2$가 훨씬 더 강력하고 우수한 추정량**이라는 것을 수학적으로 명확히 증명할 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-6 Mean Squared Error-1" src="https://github.com/user-attachments/assets/bf58165d-af49-4bb3-a97c-f02494a1b871" />
  </div>
</details>
