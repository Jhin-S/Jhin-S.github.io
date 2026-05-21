---
title: "1-2 Inverse Functions"
date: 2026-05-21 21:45:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, inverse_function]
math: true
---

## 1. Inverse Functions (역함수)

### Definition
Suppose $f$ is a function with domain $D$ and range $R$. A function $g$ is the inverse of $f$ if for all $x$ in $D$ and $y$ in $R$, the following holds:
$$ f(x) = y \iff x = g(y) $$

### Invertibility & Horizontal Line Test
* **Invertibility (가역성):** A function $f$ is invertible (meaning an inverse function exists) precisely if it is one-to-one, meaning:
  $$ f(x_1) \neq f(x_2) \quad \text{whenever} \quad x_1 \neq x_2 $$
* **Horizontal Line Test (수평선 판별법):** A function is invertible if and only if all horizontal lines intersect the graph of the function in at most 1 place.

### Graph of the Inverse
Suppose $f$ is a function with inverse $f^{-1}$. You get the graph of $f^{-1}$ by reflecting the graph of $f$ across the line $y = x$.

---

## 2. Inverse Trigonometric Functions (역삼각함수)

| Function | Domain (정의역) | Range (치역) |
| :--- | :--- | :--- |
| $y = \arcsin(x)$ | $[-1, 1]$ | $[-\frac{\pi}{2}, \frac{\pi}{2}]$ |
| $y = \arccos(x)$ | $[-1, 1]$ | $[0, \pi]$ |
| $y = \arctan(x)$ | $\mathbb{R}$ | $(-\frac{\pi}{2}, \frac{\pi}{2})$ |

---

## 3. Composition of (Inverse) Trigonometric Functions

### Method 1: Using Trigonometric Identities
**Example:** Compute $\sin(\arccos(x))$
We know the identity: $\sin^2(\theta) + \cos^2(\theta) = 1$
Let $\theta = \arccos(x)$, then:
$$ \sin^2(\arccos(x)) + \cos^2(\arccos(x)) = 1 $$
$$ \sin^2(\arccos(x)) + x^2 = 1 $$
$$ \sin(\arccos(x)) = \sqrt{1 - x^2} $$

### Method 2: Using Right-Angled Triangles
**Example:** Compute $\cos(\arctan(x))$
Let $\arctan(x) = \theta \implies \tan(\theta) = x = \frac{x}{1}$
By drawing a right-angled triangle with opposite side $x$ and adjacent side $1$, the hypotenuse becomes $\sqrt{1 + x^2}$.
Therefore:
$$ \cos(\arctan(x)) = \frac{1}{\sqrt{1 + x^2}} $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1" src="https://github.com/user-attachments/assets/e6258125-e2b1-4632-838b-4d8fd6f2a125" />
    <img width="1264" height="1635" alt="1-2" src="https://github.com/user-attachments/assets/b98ff3d0-327e-49bf-bb3a-dcfc42efb6f4" />
    <img width="1264" height="1635" alt="1-3" src="https://github.com/user-attachments/assets/c2830277-7e73-4ca9-9f5b-1a4605108ee0" />
    <img width="1264" height="1635" alt="1-4" src="https://github.com/user-attachments/assets/14bd51fe-4b95-48d7-af66-6a706765c3d6" />
    <img width="1264" height="1635" alt="1-5" src="https://github.com/user-attachments/assets/5fdd7548-f909-4e14-bc14-244af846e863" />
  </div>
</details>
