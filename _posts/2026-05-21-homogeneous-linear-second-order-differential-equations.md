---
title: "6-5 Homogeneous Linear Second Order Differential Equations"
date: 2026-05-21 23:15:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, differential_equation, second_order]
math: true
---

## 1. Characteristic Equation and General Solutions

To solve a second-order homogeneous linear differential equation of the form:
$$ ay'' + by' + cy = 0 $$
we use the ansatz (educated guess) $y(x) = e^{rx}$. Substituting this into the differential equation yields the **characteristic equation**:
$$ ar^2 + br + c = 0 $$

The nature of the general solution depends on the discriminant ($D = b^2 - 4ac$) of this quadratic equation.

### Case 1: Two Distinct Real Roots ($D > 0$)
If the characteristic equation has two distinct real roots $r_1$ and $r_2$, the general solution is:
$$ y(x) = c_1 e^{r_1 x} + c_2 e^{r_2 x} $$

### Case 2: One Repeated Real Root ($D = 0$)
If there is exactly one real root $r$, one solution is $y_1(x) = e^{rx}$. To find a second linearly independent solution, we multiply by $x$, giving $y_2(x) = x e^{rx}$.
The general solution is:
$$ y(x) = c_1 e^{rx} + c_2 x e^{rx} $$

### Case 3: Two Complex Roots ($D < 0$)
If the roots are complex conjugates $r = k \pm i\omega$, the solutions involve exponential and trigonometric functions:
$$ y_1 = e^{(k+i\omega)x} = e^{kx}(\cos \omega x + i\sin \omega x) $$
$$ y_2 = e^{(k-i\omega)x} = e^{kx}(\cos \omega x - i\sin \omega x) $$
By taking linear combinations to extract real-valued functions, we obtain the general solution:
$$ y(x) = c_1 e^{kx} \cos(\omega x) + c_2 e^{kx} \sin(\omega x) = e^{kx}(c_1 \cos \omega x + c_2 \sin \omega x) $$

---

## 2. Practice Exercises

### Exercise 6.21
Find the general solution for $y'' - 6y' + 8y = 0$.
* Characteristic equation: $r^2 - 6r + 8 = 0 \implies (r-4)(r-2) = 0$
* Roots: $r = 2, 4$
* General solution: $y = c_1 e^{2x} + c_2 e^{4x}$

### Exercise 6.22
Find the general solution for $y'' + 81y = 0$.
* Characteristic equation: $r^2 + 81 = 0 \implies r^2 = -81$
* Roots: $r = \pm 9i$ (Here, $k=0$ and $\omega=9$)
* General solution: $y = c_1 \cos(9x) + c_2 \sin(9x)$

### Exercise 6.23
Find the general solution for $y'' + 16y' + 64y = 0$.
* Characteristic equation: $r^2 + 16r + 64 = 0 \implies (r+8)^2 = 0$
* Root: $r = -8$ (repeated)
* General solution: $y = c_1 e^{-8x} + c_2 x e^{-8x}$

### Exercise 6.24
For what value of $k$ is $y = e^{kt}(c_1 \sin t + c_2 \cos t)$ a solution to $y'' - 6y' + 10y = 0$?
* Characteristic equation: $r^2 - 6r + 10 = 0$
* Roots: $r = \frac{6 \pm \sqrt{36-40}}{2} = 3 \pm i$
* The exponential part has $k=3$, and the trigonometric part has $\omega=1$.
* **Answer:** $k = 3$

---

## 3. Initial Value Problems

### Exercise 6.25
Solve $y'' - 2y' - 15y = 0$ with $y(0) = 8$ and $y'(0) = 2$.
* Roots: $r^2 - 2r - 15 = 0 \implies r = 5, -3$.
* General solution: $y = c_1 e^{5x} + c_2 e^{-3x}$
* Derivative: $y' = 5c_1 e^{5x} - 3c_2 e^{-3x}$
* Apply initial conditions:
  $y(0) = c_1 + c_2 = 8$
  $y'(0) = 5c_1 - 3c_2 = 2$
* Solving the system yields $c_1 = \frac{13}{4}$ and $c_2 = \frac{19}{4}$.
* **Solution:** $y = \frac{13}{4}e^{5x} + \frac{19}{4}e^{-3x}$

### Exercise 6.26
Solve $y'' + 3y = 0$ with $y(0) = 4$ and $y'(0) = -8$.
* Roots: $r^2 + 3 = 0 \implies r = \pm \sqrt{3}i$.
* General solution: $y = c_1 \cos(\sqrt{3}x) + c_2 \sin(\sqrt{3}x)$
* Derivative: $y' = -\sqrt{3}c_1 \sin(\sqrt{3}x) + \sqrt{3}c_2 \cos(\sqrt{3}x)$
* Apply initial conditions:
  $y(0) = c_1 = 4$
  $y'(0) = \sqrt{3}c_2 = -8 \implies c_2 = -\frac{8}{\sqrt{3}}$
* **Solution:** $y = 4\cos(\sqrt{3}x) - \frac{8}{\sqrt{3}}\sin(\sqrt{3}x)$

### Exercise 6.29
Solve $y'' - 16y' + 64y = 0$ with $y(0) = 2$ and $y'(0) = 5$.
* Roots: $(r-8)^2 = 0 \implies r = 8$.
* General solution: $y = c_1 e^{8x} + c_2 x e^{8x}$
* Derivative: $y' = 8c_1 e^{8x} + c_2(e^{8x} + 8x e^{8x})$
* Apply initial conditions:
  $y(0) = c_1 = 2$
  $y'(0) = 8c_1 + c_2 = 16 + c_2 = 5 \implies c_2 = -11$
* **Solution:** $y = 2e^{8x} - 11xe^{8x}$

### Exercise 6.28
Analyze $0.1y'' + 2y' + 100y = 0 \implies y'' + 20y' + 1000y = 0$.
* Characteristic equation: $r^2 + 20r + 1000 = 0$
* Roots: $r = \frac{-20 \pm \sqrt{-3600}}{2} = -10 \pm 30i$
* General solution: $y = e^{-10t}(c_1 \cos(30t) + c_2 \sin(30t))$
* Using conditions $y(0)=D$ and $y'(0)=0$, we can deduce the constants:
  $c_1 = D$ and $c_2 = \frac{1}{3}D$.
* **Solution:** $y = D e^{-10t}\left(\cos(30t) + \frac{1}{3}\sin(30t)\right)$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-5 Homogeneous Linear Second Order Differential Equations-1" src="https://github.com/user-attachments/assets/4e9f24ed-dd5a-4a90-af2d-bdd733f39b25" />
    <img width="1264" height="1635" alt="6-5 Homogeneous Linear Second Order Differential Equations-2" src="https://github.com/user-attachments/assets/6b3b0237-2b30-417e-9ce2-b1cc93e945e5" />
    <img width="1264" height="1635" alt="6-5 Homogeneous Linear Second Order Differential Equations-3" src="https://github.com/user-attachments/assets/25311f27-0ea3-4b58-9edc-733b88f6dbc3" />
    <img width="1264" height="1635" alt="6-5 Homogeneous Linear Second Order Differential Equations-4" src="https://github.com/user-attachments/assets/89c0bb05-0ff2-4d6a-b5b8-f83028cd9b6b" />
    <img width="1264" height="1635" alt="6-5 Homogeneous Linear Second Order Differential Equations-5" src="https://github.com/user-attachments/assets/2fb74647-755b-435d-a4c7-f87bf1226e1b" />
    <img width="1264" height="1635" alt="6-5 Homogeneous Linear Second Order Differential Equations-6" src="https://github.com/user-attachments/assets/24306d3c-89bf-4988-8bfc-b53737177c7c" />
    <img width="1264" height="1635" alt="6-5 Homogeneous Linear Second Order Differential Equations-7" src="https://github.com/user-attachments/assets/c5ff9fd4-a610-42e4-a2e6-708deefad2be" />
  </div>
</details>
