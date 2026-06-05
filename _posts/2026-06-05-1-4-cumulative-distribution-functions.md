---
title: "1-4 Cumulative Distribution Functions"
date: 2026-06-06 00:25:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, cdf, cumulative-distribution, continuous, discrete]
math: true
---

## 1. 누적 분포 함수 (Cumulative Distribution Function, CDF)

**[KR]** 확률 변수가 이산형이든 연속형이든 관계없이, 누적 분포 함수(CDF)는 확률 변수 $X$가 특정 값 $x$보다 **작거나 같을 확률**을 나타냅니다. 기호로는 $F(x)$로 표기하며, 주어진 값까지의 모든 확률을 차곡차곡 더하거나(적분하여) 누적한 값입니다.

**[EN]** Regardless of whether a random variable is discrete or continuous, its Cumulative Distribution Function (CDF) measures the probability that $X$ will take a value less than or equal to a given value $x$. It is denoted as $F(x)$ and is calculated by accumulating (summing or integrating) all probabilities up to $x$.

$$
F(x) \equiv P(X \le x)
$$

* **이산 확률 변수 (Discrete RV):** 특정 지점들에서의 확률(PMF)을 단순 합산합니다.
  
$$
F(x) = \sum_{y \le x} f(y) = \sum_{y \le x} P(X=y)
$$

* **연속 확률 변수 (Continuous RV):** 확률 밀도 함수(PDF)를 $-\infty$부터 $x$까지 적분하여 구합니다.
  
$$
F(x) = \int_{-\infty}^{x} f(y)dy
$$

---

## 2. 이산형 CDF와 계단 함수 (Discrete CDFs & Step Functions)

**[KR]** 이산 확률 변수의 CDF는 값이 불연속적으로 점프하는 **계단 함수(Step Function)**의 형태를 띱니다. 예를 들어, 동전을 2번 던져 앞면(H)이 나오는 횟수를 $X$라고 하면, 확률은 $P(X=0)=\frac{1}{4}$, $P(X=1)=\frac{1}{2}$, $P(X=2)=\frac{1}{4}$입니다. 이를 누적 분포 함수로 표현하면 다음과 같습니다.

**[EN]** The CDF of a discrete random variable takes the shape of a **step function**, where probabilities jump discontinuously. For instance, if $X$ is the number of heads in 2 coin flips, the probabilities are $\frac{1}{4}$ for 0, $\frac{1}{2}$ for 1, and $\frac{1}{4}$ for 2. The resulting CDF is defined piecewise:

$$
F(x) = 
\begin{cases} 
0 & \text{if } x < 0 \\ 
1/4 & \text{if } 0 \le x < 1 \\ 
3/4 & \text{if } 1 \le x < 2 \\ 
1 & \text{if } x \ge 2 
\end{cases}
$$

**💡 주의사항 (Warning):** 계단 함수에서는 점프가 일어나는 구간의 경계값에서 부등호($\le$와 $<$)를 매우 엄격하게 구분해서 사용해야 합니다.

---

## 3. 연속형 CDF와 미적분학의 기본 정리 (Continuous CDFs)

**[KR]** 연속 확률 변수의 경우, 미적분학의 기본 정리(Fundamental Theorem of Calculus)에 의해 **CDF를 미분하면 원래의 확률 밀도 함수(PDF)**가 됩니다. 반대로 PDF를 적분하면 CDF를 얻을 수 있습니다.

**[EN]** For continuous random variables, the relationship between the CDF and the PDF is governed by the Fundamental Theorem of Calculus. Assuming the derivative exists, **differentiating the CDF $F(x)$ yields the original PDF $f(x)$**.

$$
F'(x) = \frac{d}{dx} \int_{-\infty}^{x} f(t)dt = f(x)
$$

### 지수 분포의 예시와 중앙값 구하기 (Exponential Example & Median)
$X \sim Exp(\lambda)$일 때, PDF는 $f(x) = \lambda e^{-\lambda x}$입니다. 이를 적분한 누적 분포 함수 $F(x)$는 다음과 같습니다 ($x > 0$).

$$
F(x) = \int_{0}^{x} \lambda e^{-\lambda t} dt = 1 - e^{-\lambda x}
$$

**[KR]** 누적 확률이 정확히 절반(0.5)이 되는 지점을 중앙값(Median, $m$)이라고 합니다. 위 공식을 이용하면 중앙값을 쉽게 도출할 수 있습니다.
**[EN]** The median $m$ is the exact point where the accumulated probability reaches 0.5. We can easily find it by setting the CDF equal to 0.5:

$$
0.5 = F(m) = 1 - e^{-\lambda m} \implies m = \frac{\ln 2}{\lambda}
$$

---

## 4. 누적 분포 함수의 핵심 성질 (Properties of All CDFs)

**[KR]** 이산형과 연속형을 불문하고 모든 누적 분포 함수는 다음의 수학적 성질들을 반드시 만족합니다.

**[EN]** Regardless of the type of random variable, all CDFs universally exhibit the following mathematical properties:

1. **단조 증가 (Non-decreasing):** 확률은 계속해서 누적되므로 함수는 감소하지 않습니다. ($a < b \implies F(a) \le F(b)$)
2. **극한값 (Limits):** 가장 작은 극단에서는 0에서 시작하고, 가장 큰 극단에서는 1로 수렴합니다.
   $$\lim_{x \to -\infty} F(x) = 0, \quad \lim_{x \to \infty} F(x) = 1$$
3. **우극한 연속 (Right-continuous):** 모든 점에서 우극한 값은 해당 점의 함숫값과 일치합니다.

이러한 성질들을 활용하면 특정 구간이나 반대 구간의 확률을 매우 쉽게 계산할 수 있습니다.

* **여사건의 확률 (Tail Probabilities):** $$P(X > x) = 1 - P(X \le x) = 1 - F(x)$$
* **구간의 확률 (Interval Probabilities):** $a < b$ 일 때,
  $$P(a < X \le b) = F(b) - F(a)$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-4 Cumulative Distribution Functions-1" src="https://github.com/user-attachments/assets/159524db-fa63-4507-8e1f-c78a814152b5" />
    <img width="1264" height="1635" alt="1-4 Cumulative Distribution Functions-2" src="https://github.com/user-attachments/assets/12c30f94-b8f9-4d7b-935f-ba707eca5207" />
    <img width="1264" height="1635" alt="1-4 Cumulative Distribution Functions-3" src="https://github.com/user-attachments/assets/3f46c75b-df14-437e-a709-431cb769da4e" />
  </div>
</details>
