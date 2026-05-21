---
title: "3-1 Introduction to Approximations"
date: 2026-05-21 22:05:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, approximation, differential]
math: true
---

## 1. Overview of Approximations

### Topics covered this week:
* Defining approximations
* Understanding absolute and relative approximation errors
* Techniques for linearization
* Working with differentials
* Taylor polynomials and their applications
* Utilizing Taylor's inequality for error bounding

> **Note:** The primary focus will be on the application of Taylor polynomials.

### Obstacles in Computation
When calculating the decimal expansion of a function value, we face two main issues:
1. Certain decimal expansions lack repeating patterns.
2. The calculation process can consume significant time or resources.

---

## 2. Approximating Function Values & Errors

### Approximation Concept
Given a function $f(x)$, an approximation of the value $f(a)$ is a real number $A(a)$ that is reasonably close to $f(a)$.
This relationship is denoted as:
$$A(a) \approx f(a)$$

### Calculating Approximation Errors
Assuming $A(a) \approx f(a)$, we define the **absolute approximation error** $E$ as:
$$E = |f(a) - A(a)|$$

Likewise, the **relative approximation error** denoted by $\eta$ (eta) is:
$$\eta = \left| \frac{f(a) - A(a)}{f(a)} \right|$$

---

## 3. Linearization

Linearization provides a way to approximate values using the tangent line of a function.

For a given function $y = f(x)$, the tangent line touching the graph at $x = a$ is formulated as:
* **Tangent line equation:** $y = f(a) + f'(a)(x - a)$
* **Linearization function:** $L(x) = f(a) + f'(a)(x - a)$

---

## 4. Differentials

Differentials are highly useful for approximating changes and mathematical errors.

### Approximating Change
Let $\Delta x = x - x_0$.
The exact change in the function output is:
$$\Delta y = \Delta f = f(x) - f(x_0)$$
The estimated change derived via linearization is:
$$dy = \Delta L = L(x) - L(x_0) = f'(x_0)\Delta x$$

### Definition of a Differential
For a function $y = f(x)$, the differential $dy$ (or $df$) is defined as:
$$dy = df = f'(x)dx$$

> **Note:** By setting $x = x_0$ and $dx = \Delta x$, we get the approximation formula:
> $$\Delta y = f(x_0 + \Delta x) - f(x_0) \approx dy$$

---

## 5. Differential Example & Error Analysis

**Example Case:** $f(x) = x^3 + 2x^2$
Determine the derivative and its differential:
$$f'(x) = 3x^2 + 4x \implies df = (3x^2 + 4x)dx$$

Approximating the change $\Delta f = f(-0.8) - f(-1) = -0.232$:
Using $x_0 = -1$ and $dx = \Delta x = 0.2$:
$$df = (3(-1)^2 + 4(-1))(0.2) = -0.2$$
* **Calculated Error:** $E = |\Delta f - df| = |-0.232 - (-0.2)| = 0.032$

### Estimating Errors
For a function $f(x)$ with a measurement error $dx$ in the input $x$:
* **Estimated absolute error:** $df = f'(x)dx$
* **Estimated relative error:** $\frac{df}{f(x)} = \frac{f'(x)}{f(x)}dx$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="Introduction to Approximations-1" src="https://github.com/user-attachments/assets/d4353c96-0453-4eb9-a9c5-5f53a9da5cc9" />
    <img width="1264" height="1635" alt="Introduction to Approximations-2" src="https://github.com/user-attachments/assets/598ddf4b-dd83-40ad-ae17-1ea3f594c297" />
    <img width="1264" height="1635" alt="Introduction to Approximations-3" src="https://github.com/user-attachments/assets/d065bfe6-0f77-4275-bf19-becf82a361c6" />
    <img width="1264" height="1635" alt="Introduction to Approximations-4" src="https://github.com/user-attachments/assets/7b515e41-0488-46c7-bdde-6c3f89d140c2" />
    <img width="1264" height="1635" alt="Introduction to Approximations-5" src="https://github.com/user-attachments/assets/e7ac7386-ec73-423b-817a-4bfb75cead82" />
  </div>
</details>
