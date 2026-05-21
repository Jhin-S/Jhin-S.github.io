---
title: "6-3 Solving Linear First Order Differential Equation"
date: 2026-05-21 23:10:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, differential_equation, integrating_factor]
math: true
---

## 1. First-Order Linear Differential Equations

### Definition and Standard Form
A first-order linear differential equation is any equation that can be algebraically manipulated into the **standard form**:
$$ \frac{dy}{dx} + p(x)y = Q(x) $$

### The Integrating Factor
To solve equations in this form, we use a technique involving an **Integrating Factor**, denoted as $I(x)$. It is defined by the formula:
$$ I(x) = e^{\int p(x) \, dx} $$
*(Note: You can omit the integration constant $C$ when finding the integrating factor.)*

**Step-by-Step Solving Process:**
1. Rewrite the equation into the standard form.
2. Compute the integrating factor $I(x)$.
3. Multiply the entire standard form equation by $I(x)$.
4. Rewrite the left side as the derivative of a product: $[I(x)y]' = I(x)Q(x)$.
5. Integrate both sides with respect to $x$.
6. Divide by $I(x)$ to isolate $y$.

---

## 2. Examples and Practice Exercises

### Example 1
Solve $xy' + 2y = x^5$.
1. **Standard form:** $y' + \frac{2}{x}y = x^4 \implies p(x) = \frac{2}{x}$
2. **Integrating factor:** $I(x) = e^{\int \frac{2}{x} dx} = e^{2\ln x} = x^2$
3. **Multiply & Rewrite:** $x^2 y' + 2xy = x^6 \implies (x^2 y)' = x^6$
4. **Integrate:** $x^2 y = \frac{1}{7}x^7 + C$
5. **Solve for y:** $y = \frac{1}{7}x^5 + \frac{C}{x^2}$

### Exercise 6.11
Solve $y' + 9y = -2e^{7x}$.
* $p(x) = 9 \implies I(x) = e^{\int 9 dx} = e^{9x}$
* $(e^{9x}y)' = -2e^{16x}$
* $e^{9x}y = \int -2e^{16x} dx = -\frac{1}{8}e^{16x} + C$
* $y = -\frac{1}{8}e^{7x} + C e^{-9x}$

### Exercise 6.12
Solve the IVP: $y' + 6ty = 2t$ with $y(0) = -2$.
* $p(t) = 6t \implies I(t) = e^{3t^2}$
* $(e^{3t^2}y)' = 2t e^{3t^2}$
* $e^{3t^2}y = \frac{1}{3}e^{3t^2} + C$
* Apply $y(0) = -2 \implies -2 = \frac{1}{3} + C \implies C = -\frac{7}{3}$
* $y = \frac{1}{3} - \frac{7}{3}e^{-3t^2}$

### Additional IVP 1
Solve $y' - 4y = -4t$ with $y(0) = -2$.
* $I(t) = e^{-4t}$
* $(e^{-4t}y)' = -4t e^{-4t}$
* Integrate by parts: $e^{-4t}y = t e^{-4t} + \frac{1}{4}e^{-4t} + C$
* Apply $y(0) = -2 \implies -2 = \frac{1}{4} + C \implies C = -\frac{9}{4}$
* $y = t + \frac{1}{4} - \frac{9}{4}e^{4t}$

### Additional IVP 2
Solve $ty' = 3y + 5t^2$ with $y(1) = 3$.
* Standard form: $y' - \frac{3}{t}y = 5t$
* $I(t) = e^{-3\ln t} = t^{-3}$
* $(t^{-3}y)' = 5t^{-2} \implies t^{-3}y = -5t^{-1} + C$
* Apply $y(1) = 3 \implies 3 = -5 + C \implies C = 8$
* $y = -5t^2 + 8t^3$

### Exercise 6.14
Find the general solution for $y' + 16xy = 6x$.
* $I(x) = e^{8x^2}$
* $(e^{8x^2}y)' = 6x e^{8x^2}$
* $e^{8x^2}y = \frac{3}{8}e^{8x^2} + C \implies y = \frac{3}{8} + Ce^{-8x^2}$

Solve the IVP: $ty' + 6y = 8t^{-3}$ with $y(1) = 0$.
* Standard form: $y' + \frac{6}{t}y = 8t^{-4} \implies I(t) = t^6$
* $(t^6 y)' = 8t^2 \implies t^6 y = \frac{8}{3}t^3 + C$
* Apply $y(1) = 0 \implies 0 = \frac{8}{3} + C \implies C = -\frac{8}{3}$
* $y = \frac{8}{3}(t^3 - 1)t^{-6}$

### Exercise 6.15
Solve the IVP: $(\ln x)y' + \frac{1}{x}y = 3x^6$ with $y(e) = 3$.
* Standard form: $y' + \frac{1}{x \ln x}y = \frac{3x^6}{\ln x}$
* $I(x) = e^{\int \frac{1}{x \ln x} dx} = e^{\ln(\ln x)} = \ln x$
* $(y \ln x)' = 3x^6 \implies y \ln x = \frac{3}{7}x^7 + C$
* Apply $y(e) = 3 \implies 3(1) = \frac{3}{7}e^7 + C \implies C = 3 - \frac{3}{7}e^7$
* $y = \frac{1}{\ln x} \left( \frac{3}{7}x^7 + 3 - \frac{3}{7}e^7 \right)$

### Exercise 6.16
Find the general solution for $y' + 6xy = 5x^8 e^{-3x^2}$.
* $I(x) = e^{3x^2}$
* $(e^{3x^2}y)' = 5x^8$
* $e^{3x^2}y = \frac{5}{9}x^9 + C$
* $y = \left(\frac{5}{9}x^9 + C\right)e^{-3x^2}$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-3 Solving Linear First Order Differential Equation-1" src="https://github.com/user-attachments/assets/0c128aea-c8d8-4012-83c4-70e8b2d3a1a2" />
    <img width="1264" height="1635" alt="6-3 Solving Linear First Order Differential Equation-2" src="https://github.com/user-attachments/assets/5b6050b3-0cb0-49f1-97eb-b27d8ba0f83a" />
    <img width="1264" height="1635" alt="6-3 Solving Linear First Order Differential Equation-3" src="https://github.com/user-attachments/assets/1bc2cdae-33aa-4d6f-8ed9-a2e3cab04a33" />
    <img width="1264" height="1635" alt="6-3 Solving Linear First Order Differential Equation-4" src="https://github.com/user-attachments/assets/34c40fcb-73b6-4c90-bad1-d2a767d93fca" />
    <img width="1264" height="1635" alt="6-3 Solving Linear First Order Differential Equation-5" src="https://github.com/user-attachments/assets/6cfdd293-4212-44e4-a690-e1c62e9564ad" />
  </div>
</details>
