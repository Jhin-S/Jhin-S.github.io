---
title: "1-10 Functions of a Random Variable"
date: 2026-06-11 11:30:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, random-variable, pdf, cdf, transformation]
math: true
---

## 1. 확률 변수의 변환 (Transformation of a Random Variable)

**[KR]** 우리가 이미 확률 분포(pmf 또는 pdf)를 알고 있는 확률 변수 $X$가 있을 때, 이 $X$를 특정한 함수에 대입하여 만든 새로운 확률 변수 $Y = h(X)$ 의 확률 분포를 구하는 것은 통계학에서 매우 빈번하게 발생하는 문제입니다. 앞서 배운 LOTUS 정리가 $Y$의 '기댓값'만을 구하는 것이었다면, 이번 장에서는 $Y$의 '분포 자체'를 완벽하게 찾아내는 방법을 다룹니다.

**[EN]** When we know the probability distribution (pmf or pdf) of a random variable $X$, we often need to find the distribution of a new random variable $Y = h(X)$, which is a function of $X$. While the LOTUS theorem allowed us to find the 'expected value' of $Y$, this chapter focuses on deriving the exact 'probability distribution' of $Y$ itself.

---

## 2. 이산 확률 변수의 경우 (Discrete Case)

**[KR]** 원래의 확률 변수 $X$가 이산형(Discrete)이라면, 함수를 통과한 $Y$ 역시 이산 확률 변수가 됩니다. $Y$가 특정한 값 $y$를 가질 확률은, 함수 $h(x)$에 대입했을 때 $y$가 나오게 만드는 모든 $X$ 값들의 확률을 단순히 더해주면 됩니다.

**[EN]** If the original random variable $X$ is discrete, the transformed variable $Y$ will also be discrete. The probability that $Y$ takes a specific value $y$ is simply the sum of the probabilities of all original $x$ values that map to $y$ under the function $h(x)$.

$$
g(y) = P(Y = y) = \sum_{x \mid h(x)=y} f(x)
$$

### 응용 예제
동전을 2번 던져서 앞면이 나오는 횟수를 $X$라고 합시다. $P(X=0)=\frac{1}{4}$, $P(X=1)=\frac{1}{2}$, $P(X=2)=\frac{1}{4}$ 입니다. 이때 새로운 확률 변수 $Y = X^2 - X$ 의 분포를 구해봅시다.
* $X=0$ 이면 $Y=0$
* $X=1$ 이면 $Y=0$
* $X=2$ 이면 $Y=2$

따라서 $Y=0$이 될 확률은 $X=0$일 때와 $X=1$일 때의 확률을 합친 $\frac{3}{4}$ 이며, $Y=2$가 될 확률은 $\frac{1}{4}$ 이 됩니다.

---

## 3. 연속 확률 변수의 경우: CDF 방법 (Continuous Case: CDF Method)

**[KR]** $X$가 연속 확률 변수라고 해서 $Y$가 무조건 연속형이 되는 것은 아닙니다. 하지만 $Y$가 연속형일 경우, 가장 확실하고 표준적인 풀이 방법은 **누적 분포 함수(CDF)를 먼저 구한 뒤 이를 미분하여 확률 밀도 함수(pdf)를 얻어내는 것**입니다.

**[EN]** Just because $X$ is continuous doesn't guarantee $Y$ is continuous. However, when $Y$ is continuous, the most reliable and standard approach is to **first find the Cumulative Distribution Function (CDF) and then differentiate it to obtain the probability density function (pdf)**.

**[Step 1] $Y$의 CDF $G(y)$ 도출하기:**
$$
G(y) = P(Y \le y) = P(h(X) \le y) = \int_{x \mid h(x) \le y} f(x) \,dx
$$

**[Step 2] CDF를 미분하여 pdf $g(y)$ 얻기:**
$$
g(y) = \frac{d}{dy} G(y)
$$

### 응용 예제
$X$의 pdf가 $f(x) = \vert x \vert \quad (-1 < x < 1)$ 일 때, $Y = X^2$ 의 pdf를 구해보겠습니다.
먼저 CDF인 $G(y)$를 계산합니다. ($0 < y < 1$ 구간)
$$
G(y) = P(X^2 \le y) = P(-\sqrt{y} \le X \le \sqrt{y}) = \int_{-\sqrt{y}}^{\sqrt{y}} \vert x \vert \,dx = y
$$
이제 구한 CDF $G(y) = y$ 를 미분하면, $g(y) = 1 \quad (0 < y < 1)$ 이라는 아주 깔끔한 균등 분포(Uniform Distribution)의 pdf를 얻을 수 있습니다.

---

## 4. 연속 확률 변수의 경우: 단조 함수 공식 (Shortcut for Monotonic Functions)

**[KR]** 만약 함수 $Y = h(X)$가 항상 증가하거나 항상 감소하는 **단조 함수(Monotonic function, 일대일 대응)**라면, 복잡한 CDF 적분 과정을 생략하고 곧바로 pdf를 구할 수 있는 마법의 공식이 있습니다. 미적분학의 치환적분(Jacobian) 원리를 1차원으로 적용한 것입니다.

**[EN]** If the function $Y = h(X)$ is strictly increasing or strictly decreasing (**monotonic / one-to-one mapping**), there is a shortcut formula to find the pdf directly without going through the CDF integration process. This is essentially the 1D application of the Jacobian transformation from calculus.

$$
g(y) = f(x) \left| \frac{dx}{dy} \right| = f(h^{-1}(y)) \left| \frac{d}{dy} h^{-1}(y) \right|
$$

### 응용 예제
$X \sim Unif(0, 1)$ 이고 $f(x) = 1$ 일 때, $Y = -\ln(X)$ 의 pdf를 구해봅시다.
1. 역함수 구하기: $y = -\ln(x) \implies x = e^{-y}$
2. 미분 절댓값 구하기: $\frac{dx}{dy} = -e^{-y}$ 이므로 절댓값은 $e^{-y}$
3. 공식에 대입: $g(y) = 1 \cdot e^{-y} = e^{-y} \quad (y > 0)$
결과적으로 $Y$는 기댓값이 1인 지수 분포 $Exp(1)$를 따른다는 것을 알 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-10 Functions of a Random Variable-1" src="https://github.com/user-attachments/assets/5102464e-ce37-4314-8362-d809415dc621" />
    <img width="1264" height="1635" alt="1-10 Functions of a Random Variable-2" src="https://github.com/user-attachments/assets/d5879efb-5e8b-4db1-8fc4-f53e27d74c5c" />
    <img width="1264" height="1635" alt="1-10 Functions of a Random Variable-3" src="https://github.com/user-attachments/assets/9a190832-9aea-4887-b42a-b951e0825742" />
    <img width="1264" height="1635" alt="1-10 Functions of a Random Variable-4" src="https://github.com/user-attachments/assets/c764be31-b5c1-400e-a222-9a61083fd07f" />
    <img width="1264" height="1635" alt="1-10 Functions of a Random Variable-5" src="https://github.com/user-attachments/assets/b46851fa-f199-4049-87f0-b7d65227c8c6" />
    <img width="1264" height="1635" alt="1-10 Functions of a Random Variable-6" src="https://github.com/user-attachments/assets/29965990-fc07-4232-a966-dc5aa0ad8ee8" />
    <img width="1264" height="1635" alt="1-10 Functions of a Random Variable-7" src="https://github.com/user-attachments/assets/860d8473-2534-4e71-856e-0ef95174aa33" />
  </div>
</details>
