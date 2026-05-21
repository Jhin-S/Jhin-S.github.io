---
title: "6-6 Non Homogeneous Linear Second Order Differential Equations"
date: 2026-05-21 23:30:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, differential_equation, non_homogeneous, undetermined_coefficients]
math: true
---

## 1. Method of Undetermined Coefficients (미정계수법)

To solve a non-homogeneous differential equation, we often use the method of undetermined coefficients. The steps are as follows:

1. **Make an ansatz (guess):** Propose a particular solution $y_p$ with a number of undetermined coefficients ($A, B, C, \dots$).
2. **Plug the ansatz into the equation:** Substitute $y_p$, $y_p'$, and $y_p''$ into the original differential equation to obtain a system of equations.
3. **Solve the system:** Determine the exact values of the coefficients.

### Introductory Example
Solve $y'' + 3y' - y = x^2 - 6$.
* **Ansatz:** $y = Ax^2 + Bx + C$
* **Derivatives:** $y' = 2Ax + B$, $y'' = 2A$
* **Substitute:** $2A + 3(2Ax + B) - (Ax^2 + Bx + C) = x^2 - 6$
* By matching the coefficients for $x^2$, $x$, and the constants, we get:
  $A = -1, \quad B = -6, \quad C = -14$

---

## 2. Choosing the Right Ansatz

The choice of the initial guess depends entirely on the right-hand side $F(x)$ of the equation.

### Basic Cases
| Right Hand Side $F(x)$ | Ansatz (Guess) $y_p$ |
| :--- | :--- |
| Polynomial: $c_1x^n + c_2x^{n-1} + \dots + c_n$ | $A_n x^n + A_{n-1}x^{n-1} + \dots + A_0$ |
| Trigonometric: $c_1 \cos(\omega x) + c_2 \sin(\omega x)$ | $A \cos(\omega x) + B \sin(\omega x)$ |
| Exponential: $C e^{kx}$ | $A e^{kx}$ |

### Advanced Cases
* **Products:** If the right-hand side is a product of the basic cases, the ansatz should be the product of the corresponding ansätze.
* **Sums:** If the right-hand side is a sum of the basic cases, the ansatz should be the sum of the corresponding ansätze.

> **Note on Constants (Absorption):**
> Consider $y'' - 3y' + 2y = (2x^2 + x)e^{-x}$. 
> The correct product ansatz is $y = (Ax^2 + Bx + C)(De^{-x})$. 
> We can simplify this to $y = (Ax^2 + Bx + C)e^{-x}$. 
> *Why is $D$ fixed to 1?* We are not fixing $D=1$; rather, the unnecessary constant $D$ is simply absorbed into the arbitrary constants $A, B$, and $C$.

---

## 3. Practice Exercises

### Exercise 6.34
Solve the differential equation $y'' - 7y' = \cos x$.
* **Ansatz:** $y_p = A\sin x + B\cos x$
* $y_p' = A\cos x - B\sin x$
* $y_p'' = -A\sin x - B\cos x$
* Substitute into the equation:
  $(-A + 7B)\sin x + (-7A - B)\cos x = \cos x$
* Matching coefficients:
  $-A + 7B = 0$ and $-7A - B = 1 \implies A = -\frac{7}{50}, B = -\frac{1}{50}$
* **Particular Solution:** $y_p = -\frac{7}{50}\sin x - \frac{1}{50}\cos x$
* **Homogeneous Solution:** $r^2 - 7r = 0 \implies r = 0, 7 \implies y_c = C_1 + C_2 e^{7x}$
* **General Solution:** $y = C_1 + C_2 e^{7x} - \frac{7}{50}\sin x - \frac{1}{50}\cos x$

### Exercise 6.35
Solve $y'' + 6y' = 18x^2$.
* Since $r=0$ is a root of the homogeneous equation ($y_c = C_1 + C_2 e^{-6x}$), we must multiply the standard polynomial ansatz by $x$.
* **Ansatz:** $y_p = x(Ax^2 + Bx + C) = Ax^3 + Bx^2 + Cx$
* Substitute and match coefficients to find $A = 1, B = -\frac{1}{2}, C = \frac{1}{6}$.
* **General Solution:** $y = C_1 + C_2 e^{-6x} + x^3 - \frac{1}{2}x^2 + \frac{1}{6}x$

### Exercise 6.36 (Resonance Concept)
Consider an oscillating system: $y'' + 16y = 6\sin(\omega t)$.
For which angular frequency $\omega$ does resonance occur?
* **Ansatz:** $y_p = A\sin(\omega t) + B\cos(\omega t)$
* Substitute to find:
  $(16A - A\omega^2)\sin(\omega t) + (16B - B\omega^2)\cos(\omega t) = 6\sin(\omega t)$
* Resonance occurs when the system cannot be solved in this form (i.e., division by zero), which happens when $16 - \omega^2 = 0$. 
* **Answer:** Resonance occurs at $\omega = 4$.

### Exercise 6.37
Solve $y'' + 4y = 3\sin(2t)$ with $y(0) = 2$ and $y'(0) = -1$.
* Homogeneous roots: $r^2 + 4 = 0 \implies r = \pm 2i$. 
* Since $\sin(2t)$ is part of the homogeneous solution, we have a resonance case. We must multiply our ansatz by $t$.
* **Ansatz:** $y_p = t(A\sin 2t + B\cos 2t)$
* Substitute and simplify: $4A\cos 2t - 4B\sin 2t = 3\sin 2t \implies A = 0, B = -\frac{3}{4}$
* **General Solution:** $y = c_1\cos 2t + c_2\sin 2t - \frac{3}{4}t\cos 2t$
* **Apply Initial Conditions:**
  $y(0) = c_1 = 2$
  $y'(0) = 2c_2 - \frac{3}{4} = -1 \implies c_2 = -\frac{1}{8}$
* **Final Solution:** $y = 2\cos 2t - \frac{1}{8}\sin 2t - \frac{3}{4}t\cos 2t$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-6 Non Homogeneous Linear Second Order Differential Equations-1" src="https://github.com/user-attachments/assets/982647d5-7f43-4a28-a2e5-202eaf7021dc" />
    <img width="1264" height="1635" alt="6-6 Non Homogeneous Linear Second Order Differential Equations-2" src="https://github.com/user-attachments/assets/22442253-c97f-4f3a-bd71-1367f3d3a82c" />
    <img width="1264" height="1635" alt="6-6 Non Homogeneous Linear Second Order Differential Equations-3" src="https://github.com/user-attachments/assets/dd90c933-3d70-4a7b-a48d-116041f91ab5" />
    <img width="1264" height="1635" alt="6-6 Non Homogeneous Linear Second Order Differential Equations-4" src="https://github.com/user-attachments/assets/a02a323b-3df9-43b3-909c-9e84de1745a5" />
    <img width="1264" height="1635" alt="6-6 Non Homogeneous Linear Second Order Differential Equations-5" src="https://github.com/user-attachments/assets/5715e2fc-a50e-458a-af9b-feb2c9b996f4" />
    <img width="1264" height="1635" alt="6-6 Non Homogeneous Linear Second Order Differential Equations-6" src="https://github.com/user-attachments/assets/d6b1ec8c-7bea-46f4-bc1f-28080d737542" />
  </div>
</details>
