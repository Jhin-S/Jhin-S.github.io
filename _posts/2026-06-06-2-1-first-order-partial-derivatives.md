---
title: "2-1 First Order Partial Derivatives"
date: 2026-06-06 08:42:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, partial-derivative, limit]
math: true
---

## 1. 일계 편도함수의 정의 (Definition of First Order Partial Derivatives)

**[KR]** 다변수 함수의 편미분은 오직 한 가지 특정 변수만의 변화율을 측정하는 수학적 기법입니다. 예를 들어, 이변수 함수 $f(x, y)$를 $x$에 대해 편미분할 때, 나머지 변수인 $y$는 변화하지 않는 고정된 '상수'로 취급합니다. 이는 본질적으로 공간상의 곡면을 특정한 단면으로 잘라내어 일변수 함수의 미분과 동일하게 접근하는 것을 의미하며, 극한을 활용한 공식적인 정의는 다음과 같습니다.

**[EN]** Partial differentiation measures the rate of change of a multivariable function with respect to one specific variable while holding all other variables entirely constant. For instance, when differentiating $f(x, y)$ with respect to $x$, we treat $y$ as a fixed numerical value. This effectively reduces the process to standard single-variable calculus along a specific slice of the function. The formal limit definitions at a point $(x_0, y_0)$ are:

* **$x$에 대한 편미분 (Partial derivative with respect to $x$):**
  
$$
f_x(x_0, y_0) = \lim_{h \to 0} \frac{f(x_0 + h, y_0) - f(x_0, y_0)}{h}
$$

* **$y$에 대한 편미분 (Partial derivative with respect to $y$):**
  
$$
f_y(x_0, y_0) = \lim_{h \to 0} \frac{f(x_0, y_0 + h) - f(x_0, y_0)}{h}
$$

---

## 2. 편미분 계산 연습 (Practice Exercises)

### Exercise 1: 다항 함수의 편미분 (Polynomial Functions)
**[KR]** $f(x, y) = x^2y + xy^3$ 가 주어졌을 때, 점 $(-3, -4)$에서의 편미분 계수를 구해보겠습니다.
**[EN]** Given $f(x, y) = x^2y + xy^3$, let's evaluate the partial derivatives at the point $(-3, -4)$.

* **$f_x$ 계산:** $y$를 상수로 보고 $x$에 대해 미분합니다.
  
$$
f_x(x, y) = 2xy + y^3
$$

$$
f_x(-3, -4) = 2(-3)(-4) + (-4)^3 = 24 - 64 = -40
$$

* **$f_y$ 계산:** $x$를 상수로 보고 $y$에 대해 미분합니다.
  
$$
f_y(x, y) = x^2 + 3xy^2
$$

$$
f_y(-3, -4) = (-3)^2 + 3(-3)(-4)^2 = 9 - 144 = -135
$$

---

### Exercise 2: 무리 함수와 연쇄 법칙 (Square Roots and Chain Rule)
**[KR]** $f(x, y) = \sqrt{4x + y^2}$ 에 대하여 점 $(1, 5)$에서의 편미분 계수를 구합니다. $\frac{1}{2}$제곱 형태로 바꾸어 연쇄 법칙(Chain rule)을 적용하는 것이 핵심입니다.
**[EN]** Let $f(x, y) = \sqrt{4x + y^2} = (4x + y^2)^{1/2}$. We apply the chain rule to evaluate the derivatives at $(1, 5)$.

* **$f_x$ 계산:**
  
$$
f_x(x, y) = \frac{1}{2}(4x + y^2)^{-1/2} \cdot 4 = \frac{2}{\sqrt{4x + y^2}}
$$

$$
f_x(1, 5) = \frac{2}{\sqrt{4(1) + 5^2}} = \frac{2}{\sqrt{29}}
$$

* **$f_y$ 계산:**
  
$$
f_y(x, y) = \frac{1}{2}(4x + y^2)^{-1/2} \cdot 2y = \frac{y}{\sqrt{4x + y^2}}
$$

$$
f_y(1, 5) = \frac{5}{\sqrt{4(1) + 5^2}} = \frac{5}{\sqrt{29}}
$$

---

### Exercise 3: 역삼각함수가 포함된 삼변수 함수 (Functions with Inverse Trigonometry)
**[KR]** $f(x, y, z) = \frac{x \arctan(xy)}{1 + z^2}$ 가 주어졌을 때, $y$에 대한 편미분 $\frac{\partial f}{\partial y}$ (또는 $f_y$)를 구해보겠습니다. $y$에 대해 미분하므로 $x$와 $z$가 포함된 항들은 모두 단순한 상수 덩어리로 간주할 수 있습니다.
**[EN]** Given a three-variable function $f(x, y, z) = \frac{x \arctan(xy)}{1 + z^2}$, we want to find $\frac{\partial f}{\partial y}$. Since we are differentiating with respect to $y$, any terms consisting entirely of $x$ and $z$ are treated as constant multipliers.

오직 $\arctan(xy)$ 부분만 $y$에 의해 변화합니다. 역탄젠트 함수의 미분 공식 $\frac{d}{du}\arctan(u) = \frac{1}{1+u^2}$ 과 연쇄 법칙을 적용합니다.

$$
\frac{\partial}{\partial y} \arctan(xy) = \frac{1}{1 + (xy)^2} \cdot x = \frac{x}{1 + x^2y^2}
$$

이제 원래 함수에 있던 상수 부분들을 그대로 다시 곱해줍니다.

$$
f_y = \left( \frac{x}{1 + z^2} \right) \cdot \left( \frac{x}{1 + x^2y^2} \right) = \frac{x^2}{(1 + z^2)(1 + x^2y^2)}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-1 First Order Partial Derivativespdf-1" src="https://github.com/user-attachments/assets/8b381c8e-942c-4fa7-98ed-7356c92523d4" />
    <img width="1264" height="1635" alt="2-1 First Order Partial Derivativespdf-2" src="https://github.com/user-attachments/assets/08397ddb-d446-4573-8236-40355010ec88" />
    <img width="1264" height="1635" alt="2-1 First Order Partial Derivativespdf-3" src="https://github.com/user-attachments/assets/301e673f-cb2c-4753-86cc-b5bb7cea8026" />
  </div>
</details>
