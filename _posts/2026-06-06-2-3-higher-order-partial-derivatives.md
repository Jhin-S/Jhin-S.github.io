---
title: "2-3 Higher Order Partial Derivatives"
date: 2026-06-06 09:20:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, partial-derivative, clairaut, laplace, heat-equation]
math: true
---

## 1. 고계 편도함수와 클레로의 정리 (Higher-Order Partial Derivatives & Clairaut's Theorem)

**[KR]** 한 번 편미분한 함수를 다시 한 번 더 편미분하여 얻은 함수를 '고계 편도함수'라고 부릅니다. 이때 $x$로 먼저 미분하고 $y$로 미분하는 것($f_{xy}$)과, $y$로 먼저 미분하고 $x$로 미분하는 것($f_{yx}$)의 결과가 같은지 의문이 생길 수 있습니다. **클레로의 정리(Clairaut's Theorem)**에 따르면, 이계 편도함수가 연속이라는 전제 조건 하에서는 미분하는 순서가 결과에 아무런 영향을 미치지 않습니다.

**[EN]** Taking the partial derivative of an already differentiated function results in a higher-order partial derivative. A natural question arises: does the order of differentiation matter? According to **Clairaut's Theorem**, as long as the second-order partial derivatives are continuous, the order in which you differentiate does not change the final result.

$$
f_{xy} = f_{yx}
$$

* **확장성 (Generalization):** 이 강력한 정리는 3계, 4계 이상의 더 높은 차수나 변수가 3개 이상인 다변수 함수에도 똑같이 적용됩니다. (예: $f_{xyxz} = f_{yxxx} = f_{xxyyx}$)

---

## 2. 기본 편미분 연습 (Basic Calculation Exercises)

### Exercise 1: 다항 함수의 이계 편도함수 (Second-order of a polynomial)
**[KR]** 함수 $f(x, y) = 5x^4 + 8x^2y - 6xy^3$ 에 대하여 $f_{xx}$를 계산해보겠습니다.
**[EN]** Let's find $f_{xx}$ for the function $f(x, y) = 5x^4 + 8x^2y - 6xy^3$.

먼저 $x$에 대해 1차 편미분을 수행합니다. ($y$는 상수 취급)

$$
f_x = 20x^3 + 16xy - 6y^3
$$

구해진 $f_x$를 다시 한 번 $x$에 대해 편미분합니다.

$$
f_{xx} = 60x^2 + 16y
$$

### Exercise 2: 혼합 편도함수와 곱의 미분법 (Mixed partial derivative)
**[KR]** $f(x, y) = \sin(xy)$ 의 혼합 이계 편도함수 $f_{xy}$를 구해보겠습니다.
**[EN]** Calculate the mixed partial derivative $f_{xy}$ for $f(x, y) = \sin(xy)$.

먼저 $x$에 대해 미분합니다 (합성함수 미분법 적용).

$$
f_x = y \cos(xy)
$$

이제 이 결과를 $y$에 대해 미분해야 합니다. 식에 $y$가 두 군데 포함되어 있으므로 곱의 미분법(Product rule)을 적용합니다.

$$
f_{xy} = \frac{\partial}{\partial y}(y \cos(xy)) = 1 \cdot \cos(xy) + y \cdot (-\sin(xy) \cdot x)
$$

$$
f_{xy} = \cos(xy) - xy \sin(xy)
$$

---

## 3. 편미분 방정식 응용 (Applications in PDEs)

### Exercise 3: 라플라스 방정식 (The Laplace Equation)
**[KR]** 2차원 공간에서의 라플라스 연산자(Laplace operator) $\Delta$는 $\Delta u = u_{xx} + u_{yy}$ 로 정의됩니다. 이 값이 0이 되는 $\Delta u = 0$ 을 만족시킬 때, 이를 라플라스 방정식이라고 부릅니다. 
함수 $u(x, y) = e^{2x} \sin(ay)$ 가 이 라플라스 방정식의 해가 되기 위한 양의 상수 $a$를 구해보겠습니다.

**[EN]** The 2D Laplace operator $\Delta$ is defined as $\Delta u = u_{xx} + u_{yy}$. When this equals zero ($\Delta u = 0$), it is called the Laplace equation. Let's find the positive constant $a$ such that $u(x, y) = e^{2x} \sin(ay)$ becomes a valid solution.

$$
u_x = 2e^{2x}\sin(ay) \implies u_{xx} = 4e^{2x}\sin(ay)
$$

$$
u_y = a e^{2x}\cos(ay) \implies u_{yy} = -a^2 e^{2x}\sin(ay)
$$

두 결과를 더하여 0이 되어야 합니다.

$$
\Delta u = 4e^{2x}\sin(ay) - a^2 e^{2x}\sin(ay) = e^{2x}\sin(ay)(4 - a^2) = 0
$$

따라서 $4 - a^2 = 0$ 이어야 하므로 양의 상수 **$a = 2$** 가 됩니다.

### Exercise 4: 열 방정식 (The Heat Equation)
**[KR]** 확산 방정식(Diffusion equation)이라고도 불리는 열 방정식은 $\frac{\partial u}{\partial t} = 4\frac{\partial^2 u}{\partial x^2}$ 의 형태를 가집니다. $u(x, t) = e^{-ct} \sin(5x)$ 가 이 방정식의 올바른 해가 되도록 하는 상수 $c$를 찾습니다.

**[EN]** Given the heat equation (or diffusion equation) $\frac{\partial u}{\partial t} = 4\frac{\partial^2 u}{\partial x^2}$, determine the constant $c$ so that $u(x, t) = e^{-ct} \sin(5x)$ correctly solves the equation.

시간 $t$와 위치 $x$에 대해 각각 미분해 줍니다.

$$
u_t = -c e^{-ct} \sin(5x)
$$

$$
u_x = 5 e^{-ct} \cos(5x) \implies u_{xx} = -25 e^{-ct} \sin(5x)
$$

열 방정식 $u_t = 4 u_{xx}$ 에 각각 대입합니다.

$$
-c e^{-ct} \sin(5x) = 4 \left( -25 e^{-ct} \sin(5x) \right)
$$

$$
-c e^{-ct} \sin(5x) = -100 e^{-ct} \sin(5x)
$$

계수를 비교해보면 정답은 **$c = 100$** 이 도출됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-3 Higher Order Partial Derivatives-1" src="https://github.com/user-attachments/assets/34b0f1b0-ebfd-45f2-beec-6465b8b1f9ed" />
    <img width="1264" height="1635" alt="2-3 Higher Order Partial Derivatives-2" src="https://github.com/user-attachments/assets/5edbc7ea-778f-48b1-a029-759ffac7a1a6" />
    <img width="1264" height="1635" alt="2-3 Higher Order Partial Derivatives-3" src="https://github.com/user-attachments/assets/936d713d-957d-4c47-9faf-d4f289ce4cce" />
    <img width="1264" height="1635" alt="2-3 Higher Order Partial Derivatives-4" src="https://github.com/user-attachments/assets/e5997891-4611-40c9-b13c-ecc1445dbbba" />
  </div>
</details>
