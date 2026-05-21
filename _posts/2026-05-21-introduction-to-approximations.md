---
title: "3-1 Introduction to Approximations"
date: 2026-05-21 22:05:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, approximation, differential]
math: true
---

## 1. Overview of Approximations

### What you will encounter in this week:
* [cite_start]Definition of approximation [cite: 196]
* [cite_start]Concept of (relative) approximation error [cite: 197]
* [cite_start]Linearization [cite: 198]
* [cite_start]Differentials [cite: 199]
* [cite_start]Taylor polynomials [cite: 200]
* [cite_start]Taylor's inequality for the approximation error [cite: 201]

> [cite_start]**Note:** There will be an emphasis on the application of Taylor polynomials. [cite: 202]

### Obstacles in Computation
[cite_start]When trying to find the decimal expansion of a function value we can run into two major obstacles: [cite: 210]
1. [cite_start]Some decimal expansions have no repeating patterns. [cite: 211]
2. [cite_start]Computation can cost a lot of time or other resources. [cite: 211]

---

## 2. Approximating Function Values & Errors

### Approximation
[cite_start]**Definition:** Given a function $f(x)$, an approximation of a function value $f(a)$ is a real number $A(a)$ that is close to $f(a)$. [cite: 214, 215]
We denote this as:
[cite_start]$$ A(a) \approx f(a) $$ [cite: 216]

### Approximation Error
**Definition:** Suppose $A(a) \approx f(a)$. [cite_start]The **approximation error** $E$ is defined as: [cite: 219, 220]
$$ E = |f(a) - A(a)| [cite_start]$$ [cite: 221]

[cite_start]Similarly, the **relative approximation error** $\eta$ (eta) is defined as: [cite: 222, 223]
$$ \eta = \left| \frac{f(a) - A(a)}{f(a)} \right| [cite_start]$$ [cite: 223]

---

## 3. Linearization

[cite_start]Linearization allows us to compute approximations using the tangent line of a relevant function. [cite: 227]

[cite_start]**Definition:** Given a function $y = f(x)$, the tangent line to the graph of $f$ at the point $x = a$ is given by the equation: [cite: 230]
* [cite_start]**Tangent line:** $y = f(a) + f'(a)(x - a)$ [cite: 231]
* [cite_start]**Linearization:** $L(x) = f(a) + f'(a)(x - a)$ [cite: 231]

---

## 4. Differentials

[cite_start]We can approximate changes and errors using differentials. [cite: 236]

### Change - Approximation
[cite_start]Let $\Delta x = x - x_0$. [cite: 240]
The actual change in the function is:
[cite_start]$$ \Delta y = \Delta f = f(x) - f(x_0) $$ [cite: 240]
The approximated change using linearization is:
[cite_start]$$ dy = \Delta L = L(x) - L(x_0) = f'(x_0)\Delta x $$ [cite: 240]

### Differential Definition
[cite_start]Given a function $y = f(x)$, the differential $dy = df$ of $f$ is given by: [cite: 244]
[cite_start]$$ dy = df = f'(x)dx $$ [cite: 245]

> [cite_start]**Note:** If we set $x = x_0$ and $dx = \Delta x$, we obtain the approximation: [cite: 246]
> [cite_start]$$ \Delta y = f(x_0 + \Delta x) - f(x_0) \approx dy $$ [cite: 246]

---

## 5. Differential Example & Error Approximations

[cite_start]**Example:** $f(x) = x^3 + 2x^2$ [cite: 247]
First, find the derivative and differential:
[cite_start]$$ f'(x) = 3x^2 + 4x \implies df = (3x^2 + 4x)dx $$ [cite: 248]

[cite_start]Approximate $\Delta f = f(-0.8) - f(-1) = -0.232$: [cite: 249]
[cite_start]Given $x_0 = -1$ and $dx = \Delta x = 0.2$: [cite: 249]
[cite_start]$$ df = (3(-1)^2 + 4(-1))(0.2) = -0.2 $$ [cite: 249]
* **Error:** $E = |\Delta f - df| = |-0.232 - (-0.2)| [cite_start]= 0.032$ [cite: 252]

### Approximating Errors
[cite_start]Consider a function $f(x)$ and an error $dx$ in the input value $x$: [cite: 253]
* [cite_start]**Approximate absolute error:** $df = f'(x)dx$ [cite: 254, 255]
* [cite_start]**Approximate relative error:** $\frac{df}{f(x)} = \frac{f'(x)}{f(x)}dx$ [cite: 256, 257]

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="Introduction to Approximations-1" src="https://github.com/user-attachments/assets/e209963e-1e2a-4254-beab-09834ace908d" />
    <img width="1264" height="1635" alt="Introduction to Approximations-2" src="https://github.com/user-attachments/assets/f8413ac4-19dc-4cd4-9e71-2cf3531cf20c" />
    <img width="1264" height="1635" alt="Introduction to Approximations-3" src="https://github.com/user-attachments/assets/3105087f-c998-42f7-97af-58b82d7fa65c" />
    <img width="1264" height="1635" alt="Introduction to Approximations-4" src="https://github.com/user-attachments/assets/5ea9bba6-9135-48bd-a35b-39dd2b14fa86" />
    <img width="1264" height="1635" alt="Introduction to Approximations-5" src="https://github.com/user-attachments/assets/3dca2ee1-b58c-400b-85c2-69179c8d8a4e" />
  </div>
</details>
