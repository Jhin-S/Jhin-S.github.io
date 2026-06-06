---
title: "3-2 The Gradient"
date: 2026-06-06 10:10:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, gradient, steepest-ascent, tangent-plane, contour-line]
math: true
---

## 1. 최대 상승 방향과 그래디언트 (Steepest Ascent & The Gradient)

**[KR]** 다변수 함수에서 특정 점을 기준으로 어느 방향으로 나아갈 때 함숫값이 가장 가파르게 증가할까요? 바로 **그래디언트 벡터($\nabla f$)가 가리키는 방향**이 함수가 가장 극격하게 커지는 '최대 상승(Steepest ascent)' 방향입니다. 이때 변화율의 최댓값(최대 방향 도함수)은 그래디언트 벡터 자체의 크기와 같습니다.

**[EN]** In a multivariable function, if you want to find the direction in which the function value increases most rapidly from a given point, you must follow the **Gradient vector ($\nabla f$)**. This is known as the direction of steepest ascent. The maximum rate of change (the maximum directional derivative) is exactly equal to the magnitude of the gradient vector.

$$
\text{Max } D_u f(x, y) = \lVert \nabla f(x, y) \rVert
$$

---

## 2. 등위선의 접선과 등위면의 접평면 (Tangent to Level Curves & Surfaces)

**[KR]** 그래디언트 벡터의 또 다른 가장 중요한 기하학적 특징은, **항상 등위선(Level curve)이나 등위면(Level surface)에 수직(Orthogonal)으로 교차**한다는 것입니다. 이 성질을 이용하면 그래디언트를 법선 벡터(Normal vector)로 삼아 접선이나 접평면의 방정식을 아주 쉽게 세울 수 있습니다.

**[EN]** Another fundamental geometric property of the gradient vector is that it is **always orthogonal (perpendicular) to the level curves or level surfaces** of the function. By using the gradient as a normal vector, we can easily construct the equations for tangent lines or tangent planes.

* **등위선의 접선 방정식 (Tangent line to a 2D level curve $f(x, y) = k$):**
  점 $(a, b)$에서의 접선은 다음을 만족합니다.
  
$$
f_x(a, b)(x - a) + f_y(a, b)(y - b) = 0
$$

* **등위면의 접평면 방정식 (Tangent plane to a 3D level surface $f(x, y, z) = C$):**
  점 $(a, b, c)$에서의 접평면은 다음을 만족합니다.
  
$$
f_x(a, b, c)(x - a) + f_y(a, b, c)(y - b) + f_z(a, b, c)(z - c) = 0
$$

---

## 3. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 최대 방향 도함수 구하기
**[KR]** 함수 $f(x, y, z) = xy^2z^3$ 에 대하여 점 $P(1, -1, 1)$에서 방향 도함수가 최대가 되는 단위 벡터 $\hat{u}$를 구합니다. 최대 상승 방향은 그래디언트 방향과 일치하므로, $\nabla f$를 구한 뒤 크기로 나누어 정규화(Normalization)하면 됩니다.
**[EN]** Determine the unit vector $\hat{u}$ that yields the maximal directional derivative for $f(x, y, z) = xy^2z^3$ at the point $P(1, -1, 1)$. The direction of maximal increase is identical to the gradient's direction.

$$
\nabla f = (y^2z^3, 2xyz^3, 3xy^2z^2)
$$

점 $P(1, -1, 1)$을 대입하면 $\nabla f(1, -1, 1) = (1, -2, 3)$ 이 됩니다.
이 벡터의 크기 $\lVert \nabla f \rVert = \sqrt{1^2 + (-2)^2 + 3^2} = \sqrt{14}$ 이므로, 구하고자 하는 단위 벡터는 다음과 같습니다.

$$
\hat{u} = \frac{1}{\sqrt{14}}(1, -2, 3)
$$

---

### Exercise 2: 그래디언트와 방향 도함수의 사잇각
**[KR]** 어떤 점 $P(1, 1)$에서 그래디언트가 $\nabla f(1, 1) = (-2, 2)$ 입니다. 이 점에서 특정 단위 벡터 $\hat{u}$ 방향으로의 방향 도함수 값이 $\sqrt{6}$일 때, $\nabla f$와 $\hat{u}$ 사이의 양의 각도 $\theta$를 구해봅시다.
**[EN]** Suppose $\nabla f(1, 1) = (-2, 2)$ and the directional derivative in the direction of a unit vector $\hat{u}$ is $\sqrt{6}$. Find the positive angle $\theta$ between the gradient and $\hat{u}$.

방향 도함수는 내적으로 표현되며, 내적은 두 벡터의 크기와 코사인의 곱과 같습니다.

$$
D_u f = \nabla f \cdot \hat{u} = \lVert \nabla f \rVert \lVert \hat{u} \rVert \cos\theta = \sqrt{6}
$$

$\lVert \nabla f \rVert = \sqrt{(-2)^2 + 2^2} = \sqrt{8} = 2\sqrt{2}$ 이고, $\hat{u}$는 단위 벡터이므로 $\lVert \hat{u} \rVert = 1$ 입니다.

$$
2\sqrt{2} \cdot 1 \cdot \cos\theta = \sqrt{6} \implies \cos\theta = \frac{\sqrt{6}}{2\sqrt{2}} = \frac{\sqrt{3}}{2}
$$

따라서 두 벡터 사이의 각도는 **$\theta = \frac{\pi}{6}$ (또는 $30^\circ$)** 가 됩니다.

---

### Exercise 3: 등위선의 접선과 변화율 계산
**[KR]** 함수 $f(x, y) = x^2y - 2y^3$ 에 대하여 점 $P(2, 1)$에서의 등위선 접선 방정식을 구하고, $\vec{v} = (3, 4)$ 방향으로의 변화율을 계산합니다.
**[EN]** For $f(x, y) = x^2y - 2y^3$ at $P(2, 1)$, find the equation of the tangent line to the contour curve, and calculate the directional derivative in the direction of $\vec{v} = (3, 4)$.

먼저 편미분을 통해 $\nabla f$를 계산합니다.
$$
\nabla f = (2xy, x^2 - 6y^2) \implies \nabla f(2, 1) = (4, -2)
$$

**1) 등위선의 접선 방정식:** 그래디언트 $(4, -2)$를 법선 벡터로 사용합니다.
$$
4(x - 2) - 2(y - 1) = 0 \implies 4x - 8 - 2y + 2 = 0 \implies 2x - y = 3
$$

**2) 방향 도함수 계산:** $\vec{v} = (3, 4)$를 단위 벡터로 변환하면 $\hat{u} = \frac{1}{5}(3, 4)$ 입니다.
$$
D_u f(2, 1) = (4, -2) \cdot \left(\frac{3}{5}, \frac{4}{5}\right) = \frac{12}{5} - \frac{8}{5} = \frac{4}{5}
$$

---

### Exercise 4: 등위면의 접평면 계산
**[KR]** 삼변수 함수 $f(x, y, z) = xy^2z^2$ 의 점 $P(2, 1, 1)$에서의 접평면 $W$의 방정식을 도출합니다.
**[EN]** Determine the equation of the tangent plane $W$ to the level surface of $f(x, y, z) = xy^2z^2$ at the point $P(2, 1, 1)$.

$$
\nabla f = (y^2z^2, 2xyz^2, 2xy^2z) \implies \nabla f(2, 1, 1) = (1, 4, 4)
$$

점 $P(2, 1, 1)$을 지나며 $(1, 4, 4)$에 수직인 평면의 방정식을 세웁니다.

$$
1(x - 2) + 4(y - 1) + 4(z - 1) = 0
$$

$$
x + 4y + 4z = 10
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-2 The Gradient-1" src="https://github.com/user-attachments/assets/3edb5e29-bcf6-446d-b4db-5e9f26612e10" />
    <img width="1264" height="1635" alt="3-2 The Gradient-2" src="https://github.com/user-attachments/assets/9186f441-b6f5-40b1-8805-ca84760d96a4" />
    <img width="1264" height="1635" alt="3-2 The Gradient-3" src="https://github.com/user-attachments/assets/d01065f7-cfaf-427f-a53c-32c3d390e388" />
    <img width="1264" height="1635" alt="3-2 The Gradient-4" src="https://github.com/user-attachments/assets/38363849-6816-44cd-81f4-44a77e2c899c" />
    <img width="1264" height="1635" alt="3-2 The Gradient-5" src="https://github.com/user-attachments/assets/caaba824-a2d0-42f7-a2d2-94d74f50dc40" />
    <img width="1264" height="1635" alt="3-2 The Gradient-6" src="https://github.com/user-attachments/assets/eed10693-99e4-40d5-af3e-c525ab23a82a" />
  </div>
</details>
