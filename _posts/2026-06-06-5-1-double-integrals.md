---
title: "5-1 Double Integrals"
date: 2026-06-06 10:40:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, double-integral, volume, moment-of-inertia, riemann-sum]
math: true
---

## 1. 이중적분의 기하학적 의미 (Geometric Interpretation)

**[KR]** 일변수 함수의 정적분이 2차원 평면에서 곡선 아래의 '넓이(Area)'를 구하는 도구라면, 이변수 함수의 이중적분(Double Integral)은 3차원 공간에서 주어진 영역 $D$ 위에 떠 있는 곡면 $z = f(x, y)$ 아래의 **'부피(Signed volume)'**를 구하는 수학적 도구입니다.

**[EN]** While a single integral calculates the area under a curve in a 2D plane, a double integral computes the **signed volume** under a surface $z = f(x, y)$ over a specified two-dimensional region $D$ in 3D space.

$$
V = \iint_D f(x, y) \,dA
$$

---

## 2. 리만 합과 적분의 존재성 (Riemann Sum & Existence)

**[KR]** 이중적분 역시 밑면의 영역을 아주 작은 직사각형 모양의 격자($\Delta A$)들로 쪼갠 뒤, 각각의 격자 위로 솟아오른 직육면체 기둥들의 부피를 모두 더하는 '리만 합(Riemann Sum)'의 극한으로 정의됩니다.
만약 주어진 함수가 연속(Continuous) 함수라면, 이 극한값은 항상 존재하며 이중적분이 성공적으로 계산된다는 것이 수학적으로 보장되어 있습니다.

**[EN]** The double integral is formally defined as the limit of a Riemann Sum. We divide the base region into infinitesimally small rectangles ($\Delta A$) and sum the volumes of the resulting rectangular pillars. 
A fundamental theorem states that if the function is continuous over the region, this limit always exists, guaranteeing that the double integral can be evaluated.

$$
\iint_R f(x, y) \,dA = \lim_{\Delta A \to 0} \sum \sum f(x_i^*, y_j^*) \Delta A
$$

---

## 3. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 직사각형 영역에서의 이중적분 계산 (Evaluating over a Rectangular Region)
**[KR]** 2차원 평면의 직사각형 영역 $D = [0, 4] \times [2, 3]$ 위에서 함수 $f(x, y) = 5x$ 의 이중적분 값을 계산해 봅시다. 적분 구간이 명확한 상수이므로, 반복 적분(Iterated integral)을 사용하여 안쪽부터 차례대로 계산하면 됩니다.
**[EN]** Evaluate the double integral of $f(x, y) = 5x$ over the rectangular region $D = [0, 4] \times [2, 3]$. Since the boundaries are constants, we can easily set up and compute an iterated integral.

$$
\iint_D 5x \,dA = \int_{2}^{3} \int_{0}^{4} 5x \,dx\,dy
$$

먼저 안쪽의 $x$에 대한 적분을 수행합니다. ($y$는 상수 취급하지만, 여기선 $y$ 항이 없습니다.)
$$
\int_{0}^{4} 5x \,dx = \left[ \frac{5}{2}x^2 \right]_{0}^{4} = \frac{5}{2}(16) - 0 = 40
$$

이제 그 결과를 바깥쪽의 $y$에 대해 적분합니다.
$$
\int_{2}^{3} 40 \,dy = \left[ 40y \right]_{2}^{3} = 40(3) - 40(2) = 40
$$

---

### Exercise 2: 질량 밀도와 관성 모멘트 (Mass Density and Moment of Inertia)
**[KR]** 어떤 얇은 판(Lamina)의 영역 $D$에서 질량 밀도 함수가 $\rho(x, y) = x^2y$ 로 주어졌습니다. 이 판의 전체 질량 $m$과 $y$축을 기준으로 한 관성 모멘트(Moment of inertia) $I_y$를 구할 때, $I_y = \iint_D g(x, y) \,dA$ 라면 피적분 함수 $g(x, y)$는 무엇이 될까요?
**[EN]** Suppose a lamina occupies a region $D$ and has a mass density function $\rho(x, y) = x^2y$. If the moment of inertia about the y-axis is defined as $I_y = \iint_D g(x, y) \,dA$, what is the function $g(x, y)$?

* **전체 질량 (Total Mass):** 밀도를 전체 영역에 대해 적분한 값입니다.
  $$m = \iint_D \rho(x, y) \,dA$$

* **관성 모멘트 (Moment of Inertia):** $y$축을 회전축으로 할 때, 각 지점의 질량에 '$y$축으로부터의 거리의 제곱($x^2$)'을 곱하여 모두 더해주어야 합니다.
  $$I_y = \iint_D x^2 \rho(x, y) \,dA$$

따라서 찾고자 하는 피적분 함수 $g(x, y)$는 다음과 같습니다.
$$
g(x, y) = x^2 \rho(x, y) = x^2 (x^2y) = x^4y
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-1 Double Integrals-1" src="https://github.com/user-attachments/assets/311cffc0-150a-4081-98c9-df138d526ec7" />
    <img width="1264" height="1635" alt="5-1 Double Integrals-2" src="https://github.com/user-attachments/assets/a9d70033-823a-4fc2-a9ed-4a88513f959d" />
  </div>
</details>
