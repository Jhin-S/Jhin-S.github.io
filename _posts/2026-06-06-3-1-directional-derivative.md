---
title: "3-1 Directional Derivative"
date: 2026-06-06 10:00:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, directional-derivative, gradient, vector]
math: true
---

## 1. 방향 도함수 (Directional Derivative)

**[KR]** 앞서 배운 편미분($f_x, f_y$)은 오직 $x$축이나 $y$축과 평행한 방향으로의 변화율만을 측정합니다. 하지만 공간상의 어떤 점에서 대각선 등 임의의 특정 방향으로 이동할 때 함수가 얼마나 가파르게 변하는지 알고 싶다면 **방향 도함수(Directional Derivative)**를 사용해야 합니다. 
이때 방향을 나타내는 벡터는 반드시 크기가 1인 **단위 벡터(Unit vector, $\hat{u} = (u_1, u_2)$)**여야 합니다.

**[EN]** Standard partial derivatives ($f_x, f_y$) only measure the rate of change parallel to the coordinate axes. If we want to determine how steeply a function changes as we move in any arbitrary direction, we use the **Directional Derivative**. 
It is crucial that the direction is defined by a **unit vector** ($\hat{u} = (u_1, u_2)$) with a magnitude of exactly 1.

* **극한을 이용한 정의 (Definition by limit):**
  
$$
D_u f(a, b) = \lim_{h \to 0} \frac{f(a + u_1h, b + u_2h) - f(a, b)}{h}
$$

* **편미분과의 관계 (Relation with partial derivatives):**
  미분 가능한 함수에 대하여, 방향 도함수는 각 편미분 계수와 단위 벡터 성분들의 단순한 선형 결합으로 쉽게 계산할 수 있습니다.
  
$$
D_u f(a, b) = f_x(a, b)u_1 + f_y(a, b)u_2
$$

---

## 2. 그래디언트 벡터 (Gradient Vector)

**[KR]** 다변수 함수의 모든 1계 편미분 결과들을 모아서 하나의 벡터로 만든 것을 **그래디언트(Gradient)**라고 부르며, 역삼각형 기호인 나블라($\nabla$)를 사용하여 표기합니다. 

**[EN]** The **Gradient** is a vector that gathers all the first-order partial derivatives of a multivariable function into a single mathematical object. It is denoted by the nabla symbol ($\nabla$).

$$
\nabla f(a_1, \dots, a_n) = (f_{x_1}(a_1, \dots, a_n), \dots, f_{x_n}(a_1, \dots, a_n))
$$

### 방향 도함수와 그래디언트의 내적 (Dot Product Relationship)
**[KR]** 앞서 살펴본 방향 도함수의 계산식($f_x u_1 + f_y u_2$)은 사실 **그래디언트 벡터와 방향 단위 벡터의 내적(Dot product)**과 완벽하게 동일합니다.

**[EN]** The formula for the directional derivative is fundamentally the **dot product between the gradient vector and the unit direction vector**.

$$
D_u f(a_1, \dots, a_n) = \nabla f(a_1, \dots, a_n) \cdot \hat{u}
$$

---

## 3. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 다항 함수의 방향 도함수 (Polynomials)
**[KR]** 함수 $f(x, y) = 5xy^2 - 4x^3y$ 에 대하여 점 $(1, 2)$에서 방향 단위 벡터 $\vec{u} = (\frac{5}{13}, \frac{12}{13})$ 로의 방향 도함수를 구해보겠습니다.
**[EN]** Find the directional derivative of $f(x, y) = 5xy^2 - 4x^3y$ at the point $(1, 2)$ in the direction of the unit vector $\vec{u} = (\frac{5}{13}, \frac{12}{13})$.

먼저 편미분을 통해 그래디언트 벡터를 구합니다.
* $f_x = 5y^2 - 12x^2y$
* $f_y = 10xy - 4x^3$

점 $(1, 2)$를 대입하여 $\nabla f(1, 2)$를 찾습니다.
* $f_x(1, 2) = 5(4) - 12(1)(2) = 20 - 24 = -4$
* $f_y(1, 2) = 10(1)(2) - 4(1) = 20 - 4 = 16$
* $\nabla f = (-4, 16)$

마지막으로 그래디언트와 방향 벡터를 내적합니다.

$$
D_u f(1, 2) = (-4, 16) \cdot \left(\frac{5}{13}, \frac{12}{13}\right) = -\frac{20}{13} + \frac{192}{13} = \frac{172}{13}
$$

---

### Exercise 2: 역삼각함수와 벡터의 정규화 (Inverse Trig & Normalization)
**[KR]** 함수 $f(x, y) = \arctan(xy^2)$ 에 대하여 점 $P(1, -1)$에서 벡터 $\vec{v} = (-1, 2)$ 방향으로의 변화율을 구합니다. 주어진 벡터가 단위 벡터가 아니므로, 먼저 크기로 나누어 **정규화(Normalization)**를 해야 합니다.
**[EN]** Evaluate the rate of change of $f(x, y) = \arctan(xy^2)$ at $P(1, -1)$ in the direction of $\vec{v} = (-1, 2)$. Since the given vector is not a unit vector, we must first **normalize** it by dividing by its magnitude.

* 벡터의 크기: $\lVert \vec{v} \rVert = \sqrt{(-1)^2 + 2^2} = \sqrt{5}$
* 단위 벡터: $\hat{u} = \frac{1}{\sqrt{5}}(-1, 2)$

연쇄 법칙을 사용하여 편미분을 구합니다. ($\frac{d}{du}\arctan(u) = \frac{1}{1+u^2}$)
* $f_x = \frac{1}{1 + (xy^2)^2} \cdot y^2 = \frac{y^2}{1 + x^2y^4}$
* $f_y = \frac{1}{1 + (xy^2)^2} \cdot 2xy = \frac{2xy}{1 + x^2y^4}$

점 $(1, -1)$을 대입합니다. 분모는 $1 + (1)^2(-1)^4 = 2$가 됩니다.
* $f_x(1, -1) = \frac{1}{2}$
* $f_y(1, -1) = \frac{-2}{2} = -1$
* $\nabla f = \left(\frac{1}{2}, -1\right)$

내적을 통해 최종 값을 계산합니다.

$$
D_u f(1, -1) = \left(\frac{1}{2}, -1\right) \cdot \left(-\frac{1}{\sqrt{5}}, \frac{2}{\sqrt{5}}\right) = -\frac{1}{2\sqrt{5}} - \frac{2}{\sqrt{5}} = -\frac{5}{2\sqrt{5}} = -\frac{\sqrt{5}}{2}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-1 Directional Derivative-1" src="https://github.com/user-attachments/assets/7ec68613-fad1-45df-a2be-63ad4d4f3e1f" />
    <img width="1264" height="1635" alt="3-1 Directional Derivative-2" src="https://github.com/user-attachments/assets/0f30001f-530c-4dc4-ab91-0b378e2bf73a" />
    <img width="1264" height="1635" alt="3-1 Directional Derivative-3" src="https://github.com/user-attachments/assets/1273ac5d-5be9-4ee9-be78-ea08314ad60f" />
  </div>
</details>
