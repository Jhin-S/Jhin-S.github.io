---
title: "1-12 Honors Bonus Results"
date: 2026-06-11 11:51:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, random-variable, pdf, lotus, chain-rule]
math: true
---

## 1. 연속 확률 변수의 변환 공식 (PDF of a Transformed Continuous RV)

**[KR]** 연속 확률 변수 $X$를 단조 함수(Monotonic function)인 $Y = h(X)$에 대입하여 새로운 확률 변수 $Y$를 만들었을 때, 누적 분포 함수(CDF)를 거치지 않고 곧바로 확률 밀도 함수(pdf)인 $g(y)$를 구하는 공식입니다. 미적분학의 연쇄 법칙(Chain Rule)을 활용하여 도출됩니다.

**[EN]** When a new random variable $Y$ is defined by a monotonic function $Y = h(X)$ of a continuous random variable $X$, we can find its probability density function (pdf) $g(y)$ directly without determining the cumulative distribution function (CDF) first. This is derived using the Chain Rule from calculus.

* **수학적 유도 과정 (Derivation):**
  $Y$의 CDF인 $G(y)$를 미분하여 pdf를 얻습니다. (함수 $h$가 단조 증가 함수라고 가정합니다.)

$$
g(y) = \frac{d}{dy} G(y) = \frac{d}{dy} P(Y \le y) = \frac{d}{dy} P(h(X) \le y)
$$

역함수를 취하여 $X$에 대해 정리한 뒤 미분 연쇄 법칙을 적용합니다.

$$
= \frac{d}{dy} P(X \le h^{-1}(y)) = \frac{d}{dy} F_X(h^{-1}(y))
$$

$$
g(y) = f(h^{-1}(y)) \left| \frac{d}{dy} h^{-1}(y) \right|
$$

---

## 2. 실전 예제 (Practice Example)

**[KR]** 확률 변수 $X$의 pdf가 $f(x) = 3x^2 \quad (0 < x < 1)$ 일 때, 단조 증가 함수인 $Y = h(X) = x^{1/2}$ 의 pdf $g(y)$를 위 공식을 통해 직접 구해봅시다.

**[EN]** Let the pdf of a random variable $X$ be $f(x) = 3x^2$ for $0 < x < 1$. Let's directly find the pdf $g(y)$ of the monotonically increasing function $Y = h(X) = x^{1/2}$ using the formula above.

1. **역함수와 미분값 구하기:**
   $y = x^{1/2} \implies x = y^2$
   이 식을 $y$에 대해 미분하면 $\frac{dx}{dy} = 2y$ 가 됩니다.

2. **공식에 대입하기:**
   기존 pdf $f(x)$의 $x$ 자리에 $y^2$를 대입하고, 미분값의 절댓값인 $\left| 2y \right|$를 곱해줍니다.

$$
g(y) = f(y^2) \left| \frac{dy^2}{dy} \right| = 3(y^2)^2 \cdot (2y) = 6y^5 \quad (0 < y < 1)
$$

---

## 3. 무의식적인 통계학자의 법칙(LOTUS)의 증명 (Proof of LOTUS)

**[KR]** 앞서 도출한 확률 변수 변환 공식을 사용하면, 기댓값을 구할 때 새로운 함수의 분포를 몰라도 기존 분포만으로 계산할 수 있다는 **LOTUS (Law of the Unconscious Statistician)** 정리를 수학적으로 완벽하게 증명할 수 있습니다.

**[EN]** Using the transformation formula derived above, we can mathematically prove the **LOTUS (Law of the Unconscious Statistician)**, which states that the expected value of a function of a random variable can be calculated using only the original distribution.

새로운 변수 $Y = h(X)$ 의 기댓값 정의에서 출발합니다. (함수 $h$가 단조 증가한다고 가정합니다.)

$$
E[Y] = \int_{-\infty}^{\infty} y \cdot g(y) \,dy
$$

여기에 우리가 구했던 $g(y)$ 공식을 그대로 대입합니다.

$$
= \int_{-\infty}^{\infty} y \cdot f(h^{-1}(y)) \left| \frac{d}{dy} h^{-1}(y) \right| \,dy
$$

적분 변수를 $y$에서 다시 $x$로 치환적분(Substitution)합니다. $x = h^{-1}(y)$ 이므로 $y = h(x)$ 가 되며, $dx = \frac{d}{dy} h^{-1}(y) \,dy$ 로 깔끔하게 치환됩니다.

$$
E[h(X)] = \int_{-\infty}^{\infty} h(x) f(x) \,dx
$$

이로써 $Y$의 분포 $g(y)$를 몰라도, 원래의 분포 $f(x)$만으로 기댓값을 계산할 수 있다는 LOTUS가 증명되었습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-12 Honors Bonus Results-1" src="https://github.com/user-attachments/assets/31a2a476-cfd7-4e63-b0e6-c1455f0bac2f" />
    <img width="1264" height="1635" alt="1-12 Honors Bonus Results-2" src="https://github.com/user-attachments/assets/4bdda6d0-c129-4608-928c-4939b4cc14b0" />
  </div>
</details>
