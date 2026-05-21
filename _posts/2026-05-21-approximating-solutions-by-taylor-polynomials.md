---
title: "6-7 Approximating solutions by Taylor polynomials"
date: 2026-05-21 23:40:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, differential_equation, taylor_series, approximation]
math: true
---

## 1. Approximation by Taylor Polynomials

When a differential equation is difficult or impossible to solve analytically, we can approximate its solution near a specific point using Taylor polynomials. We achieve this by repeatedly differentiating the equation to find higher-order derivatives at the initial point.

### Introductory Example
Consider the third-order initial value problem: 
$$ y^{(3)}y + xy' = x^2 $$
with initial conditions $y(1) = 2, \quad y'(1) = -1, \quad y''(1) = 2$.

We can build the Taylor polynomials step by step around $a = 1$:
* **1st degree (Linear):** $T_1(x) = y(1) + y'(1)(x-1) = 2 - (x-1)$
* **2nd degree:** $T_2(x) = 2 - (x-1) + \frac{2}{2!}(x-1)^2 = 2 - (x-1) + (x-1)^2$
* **3rd degree:** To find $y^{(3)}(1)$, substitute $x=1$ into the original differential equation:
  $$ y^{(3)}(1) \cdot 2 + 1(-1) = 1^2 \implies 2y^{(3)}(1) - 1 = 1 \implies y^{(3)}(1) = 1 $$
  $$ T_3(x) = 2 - (x-1) + (x-1)^2 + \frac{1}{6}(x-1)^3 $$
* **4th degree:** Differentiate the entire differential equation with respect to $x$:
  $$ y^{(4)}y + y^{(3)}y' + y' + xy'' = 2x $$
  Evaluate at $x=1$:
  $$ y^{(4)}(1) \cdot 2 + 1(-1) + (-1) + 1(2) = 2(1) \implies 2y^{(4)}(1) = 2 \implies y^{(4)}(1) = 1 $$
  $$ T_4(x) = 2 - (x-1) + (x-1)^2 + \frac{1}{6}(x-1)^3 + \frac{1}{24}(x-1)^4 $$

---

## 2. Practice Exercises (Part 1)

### Exercise 6.38
Assume $y(x)$ is the solution to $y' = y^2 + y$ with $y(0) = 2$. Approximate $y(1)$ using a second-order Taylor polynomial $T_2(x)$ around $a=0$.
1. **Find derivatives at $x=0$:**
   $$ y(0) = 2 $$
   $$ y'(0) = 2^2 + 2 = 6 $$
   Differentiating the equation gives $y'' = 2yy' + y'$.
   $$ y''(0) = 2(2)(6) + 6 = 24 + 6 = 30 $$
2. **Construct the polynomials:**
   $$ T_0(x) = 2 $$
   $$ T_1(x) = 2 + 6x $$
   $$ T_2(x) = 2 + 6x + \frac{30}{2}x^2 = 2 + 6x + 15x^2 $$
3. **Approximate $y(1)$:**
   $$ T_2(1) = 2 + 6(1) + 15(1^2) = 23 $$

### Exercise 6.39
Given the initial value problem $y'' + y' + xy = 0$ with $y(3) = 2$ and $y'(3) = 4$. Find the quadratic approximation $T_2(x)$ of the solution.
* Evaluate the equation at $x=3$:
  $$ y''(3) + y'(3) + 3y(3) = 0 \implies y''(3) + 4 + 3(2) = 0 \implies y''(3) = -10 $$
* Construct $T_2(x)$ around $a=3$:
  $$ T_2(x) = y(3) + y'(3)(x-3) + \frac{y''(3)}{2!}(x-3)^2 $$
  $$ T_2(x) = 2 + 4(x-3) - 5(x-3)^2 $$

---

## 3. Practice Exercises (Part 2)

### Exercise 6.40
Given the IVP $y'' + xy' + y = 0$ with $y(1) = 2$ and $y'(1) = 4$. Find the cubic approximation $T_3(x)$ around $a=1$.
* **Find $y''(1)$:**
  $$ y''(1) + 1 \cdot y'(1) + y(1) = 0 \implies y''(1) + 4 + 2 = 0 \implies y''(1) = -6 $$
* **Find $y'''(1)$:**
  Differentiate the original equation: $y''' + y' + xy'' + y' = 0 \implies y''' + xy'' + 2y' = 0$.
  Evaluate at $x=1$:
  $$ y'''(1) + 1(-6) + 2(4) = 0 \implies y'''(1) + 2 = 0 \implies y'''(1) = -2 $$
* **Construct $T_3(x)$:**
  $$ T_3(x) = 2 + 4(x-1) - \frac{6}{2}(x-1)^2 - \frac{2}{6}(x-1)^3 = 2 + 4(x-1) - 3(x-1)^2 - \frac{1}{3}(x-1)^3 $$

### Exercise 6.41
Suppose $y(x)$ solves $y'(x) = y(x)^3 + 2$ with $y(0) = 3$. Approximate $y(0.2)$ to two decimal places using $T_2(x)$ around $a=0$.
* **Find derivatives at $x=0$:**
  $$ y(0) = 3 $$
  $$ y'(0) = 3^3 + 2 = 29 $$
  Differentiate the equation: $y''(x) = 3y(x)^2 y'(x)$.
  $$ y''(0) = 3(3^2)(29) = 27 \times 29 = 783 $$
* **Construct $T_2(x)$:**
  $$ T_2(x) = 3 + 29x + \frac{783}{2}x^2 $$
* **Approximate $y(0.2)$:**
  $$ T_2(0.2) = 3 + 29(0.2) + \frac{783}{2}(0.2)^2 = 3 + 5.8 + \frac{783}{2}(0.04) = 8.8 + 15.66 = 24.46 $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-7 Approximating solutions by Taylor polynomials-1" src="https://github.com/user-attachments/assets/a87d3a36-efec-4b93-a9ab-762696fb99e9" />
    <img width="1264" height="1635" alt="6-7 Approximating solutions by Taylor polynomials-2" src="https://github.com/user-attachments/assets/80467341-4f7c-4d33-a98e-2427e08d91d5" />
    <img width="1264" height="1635" alt="6-7 Approximating solutions by Taylor polynomials-3" src="https://github.com/user-attachments/assets/3326c3e4-a215-4c31-ba1b-fdad451c2dd1" />
  </div>
</details>
