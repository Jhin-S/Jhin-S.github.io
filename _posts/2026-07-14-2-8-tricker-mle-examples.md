---
title: "2-8 Tricker MLE Examples"
date: 2026-07-14 18:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, mle, maximum-likelihood, normal-distribution, gamma-distribution, uniform-distribution]
math: true
---

## 1. 정규 분포의 동시 최대 우도 추정 (Simultaneous MLEs for Normal Distribution)

**[KR]** 확률 변수들이 정규 분포 $N(\mu, \sigma^2)$를 따를 때, 우리가 모르는 파라미터는 평균($\mu$)과 분산($\sigma^2$), 두 가지입니다. 이 두 모수의 최대 우도 추정량(MLE)을 구하기 위해서는 다변수 미적분학의 편미분(Partial Derivative)을 활용하여 두 개의 연립방정식을 동시에 풀어야 합니다.

**[EN]** When random variables follow a normal distribution $N(\mu, \sigma^2)$, there are two unknown parameters: the mean ($\mu$) and the variance ($\sigma^2$). To find the Maximum Likelihood Estimators (MLEs) for both, we must utilize partial derivatives from multivariable calculus to solve a system of two equations simultaneously.

* **로그 우도 함수 설정:** 복잡한 지수 함수 형태를 띤 정규 분포의 우도 함수에 자연로그($\ln$)를 씌워 덧셈 형태로 분해합니다.
* **평균($\mu$)에 대한 편미분:** 수식을 $\mu$에 대해 편미분하여 $0$으로 두면, 우리가 익히 알고 있는 **표본 평균($\bar{X}$)**이 정확히 도출됩니다.
  
$$
\hat{\mu} = \bar{X}
$$

* **분산($\sigma^2$)에 대한 편미분:** 주의할 점은 $\sigma$가 아닌 분산 통째($\sigma^2$)를 하나의 변수로 보고 편미분한다는 것입니다. 이를 $0$으로 두고 풀면 다음과 같은 추정량이 나옵니다.
  
$$
\hat{\sigma}^2 = \frac{1}{n} \sum_{i=1}^n (X_i - \bar{X})^2
$$

**[통계적 통찰 / Statistical Insight]** 이때 도출된 분산의 MLE인 $\hat{\sigma}^2$는 우리가 앞서 불편 추정량(Unbiased Estimator) 파트에서 배웠던 표본 분산 $S^2$과 미세하게 다릅니다. 분모가 $n-1$이 아닌 $n$이기 때문에 이 MLE는 약간의 편향(Biased)을 가집니다. 하지만 데이터의 개수 $n$이 무한히 커질수록 결국 $S^2$과 동일해지며, 심지어 MSE(평균 제곱 오차) 관점에서는 분산이 약간 더 작다는 흥미로운 성질을 가집니다.

---

## 2. 감마 분포와 다이감마 함수 (Gamma Distribution & Digamma Function)

**[KR]** 감마 분포 $Gamma(r, \lambda)$의 두 파라미터를 추정하는 과정은 미적분학의 거대한 난관에 부딪히게 됩니다. $\lambda$에 대한 편미분은 비교적 쉽게 $\hat{\lambda} = r / \bar{X}$ 로 정리되지만, 형상 파라미터 $r$에 대한 편미분을 수행할 때, 팩토리얼의 일반화 버전인 감마 함수 $\Gamma(r)$를 미분해야 하는 골치 아픈 상황이 발생합니다.

**[EN]** The process of estimating the two parameters of a Gamma distribution $Gamma(r, \lambda)$ encounters a massive calculus hurdle. While the partial derivative w.r.t $\lambda$ easily simplifies to $\hat{\lambda} = r / \bar{X}$, differentiating with respect to the shape parameter $r$ creates a headache because it requires taking the derivative of the Gamma function $\Gamma(r)$, the continuous generalization of a factorial.

* **다이감마 함수의 등장:** 우도 함수를 미분하는 과정에서 $\Gamma'(r) / \Gamma(r)$ 이라는 항이 튀어나오며, 이를 통계학에서는 **다이감마 함수(Digamma Function, $\Psi(r)$)**라고 부릅니다.
* **수치해석적 해결 (Numerical Methods):** 다이감마 함수가 포함된 이 복잡한 방정식은 손으로 직접 $r$을 깔끔하게 정리하는 것(Closed-form solution)이 불가능합니다. 따라서 뉴턴-랩슨 법(Newton's method)이나 이분법(Bisection) 같은 컴퓨터 알고리즘을 동원하여 근사해를 찾아내야만 합니다.

---

## 3. 균등 분포의 뼈대 있는 추정 (MLE for Uniform Distribution)

**[KR]** 지금까지는 모두 미분을 통해 최댓값(기울기가 0이 되는 지점)을 찾았지만, 데이터가 미지의 최댓값 $\theta$를 가지는 균등 분포 $Unif(0, \theta)$를 따를 때는 이 미분 기법이 완전히 무용지물이 됩니다. 아주 직관적인 논리와 제약 조건을 통해 풀어야 하는 가장 특이하고 매력적인 MLE 예제입니다.

**[EN]** Up until now, we have used derivatives to find the maximum (where the slope is zero). However, when the data follows a uniform distribution $Unif(0, \theta)$ with an unknown maximum $\theta$, this calculus technique becomes completely useless. This is the most unique and fascinating MLE example, which must be solved using pure intuition and boundary constraints.

1. **우도 함수의 형태:** $L(\theta) = 1 / \theta^n$ 입니다. 
2. **논리적 제약:** 우도 함수를 가장 크게(Maximize) 만들려면, 분모에 있는 $\theta$의 값을 가능한 한 **가장 작게** 만들어야 합니다.
3. **경계 조건 (Boundary Condition):** 그런데 $\theta$는 모든 데이터가 추출된 구간의 '최댓값'을 의미합니다. 따라서 논리적으로 $\theta$는 우리가 뽑은 그 어떤 데이터 샘플보다도 커야만 합니다. 즉, $\theta \ge \max(X_i)$ 라는 강력한 철벽 제약이 생깁니다.
4. **결론:** 우도 함수를 폭발시키기 위해 $\theta$를 한없이 작게 줄여나가다가, 이 제약 조건의 벽에 부딪혀 멈추는 바로 그 지점이 최대 우도 추정량이 됩니다. 따라서 미분 없이 직관적으로 도출된 MLE는 **표본의 최댓값**이 됩니다.

$$
\hat{\theta} = \max_{1 \le i \le n} X_i
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-8 Tricker MLE Examples-1" src="https://github.com/user-attachments/assets/919a75d6-d51f-427f-b227-1c79e43aadc2" />
    <img width="1264" height="1635" alt="2-8 Tricker MLE Examples-2" src="https://github.com/user-attachments/assets/231c4e3b-f3a9-4cd5-882b-6473ca956e68" />
    <img width="1264" height="1635" alt="2-8 Tricker MLE Examples-3" src="https://github.com/user-attachments/assets/7b5894fe-3755-441c-a2be-5d8f90f3acf9" />
  </div>
</details>
