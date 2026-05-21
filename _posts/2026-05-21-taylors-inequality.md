---
title: "3-3 Taylor's Inequality"
date: 2026-05-21 22:20:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, taylor_series, error_bound]
math: true
---

## 1. Taylor's Inequality Overview

### Learning Objectives
* Calculate an upper bound for the approximation error when using Taylor polynomials.
* Determine a suitable upper bound $M$ for the relevant derivative in Taylor's inequality.
* Identify the necessary degree of a Taylor polynomial to meet a specific error tolerance.

### Approximation Error Definition
For a given function $f$ and its Taylor polynomial $T_n$ centered at $a$, the exact approximation error at $x$ is defined as:
$$ R_n(x) = |f(x) - T_n(x)| $$

### Taylor's Inequality Theorem
Assume $f$ is a function with an $n$-th order Taylor polynomial $T_n$ centered at $a$. Let $D$ be an interval containing $a$, and let $M$ be a real number that bounds the $(n+1)$-th derivative of $f$ on $D$. That is:
$$ |f^{(n+1)}(x)| \le M \quad \text{for all } x \in D $$
Then, for any $x \in D$, the error is bounded by:
$$ R_n(x) = |f(x) - T_n(x)| \le \frac{M}{(n+1)!}|x-a|^{n+1} $$

---

## 2. Practice Exercises

### Exercise 3.28: Bounding the error of $e^{2x}$
Consider $f(x) = e^{2x}$. Find its derivatives and the error term $R_3(x)$.
* $f'(x) = 2e^{2x}$
* $f''(x) = 4e^{2x}$
* $f'''(x) = 8e^{2x}$
* $f^{(4)}(x) = 16e^{2x}$

The third-order Taylor polynomial is:
$$ T_3^f(x) = 1 + 2x + \frac{4}{2!}x^2 + \frac{8}{3!}x^3 $$
The remainder term $R_3(x)$ is given by:
$$ R_3(x) = \frac{f^{(4)}(c)}{4!}x^4 = \frac{16e^{2c}}{4!}x^4 $$
*(where $c$ is some number between $0$ and $x$)*

### Exercise 3.29: Required degree for a specific accuracy
Given $f(x) = e^{2x}$, the $n$-th derivative is $f^{(n)}(x) = 2^n e^{2x}$.
For an interval $|x - a| \le b$ (with $a \ge 0, b \ge 0$), the maximum value of $|f^{(n)}(x)|$ is $2^n e^{2(a+b)}$.

If we fix $a = 0$ and $b = \frac{1}{2}$, how many terms are needed to guarantee the error is smaller than $10^{-4}$ on $[-0.5, 0.5]$?
$$ R_n(x) \le \frac{2^{n+1}e^{2c}}{(n+1)!}x^{n+1} \le \frac{e^{2c}}{(n+1)!} \le \frac{e}{(n+1)!} $$
To satisfy the tolerance, we solve for $n$ and find that a fourth-degree Taylor polynomial ($n=4$) provides a sufficiently small error bound.

### Exercise 3.30: Approximating $\sin x$
We want to approximate $\sin x$ on the interval $[-0.5, 0.5]$. The Taylor polynomials centered at $0$ are:
* $T_1(x) = T_2(x) = x$
* $T_3(x) = T_4(x) = x - \frac{x^3}{3!}$
* $T_5(x) = T_6(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!}$

Using Taylor's inequality for $T_5(x)$ and choosing $M = 1$ (since the derivatives of sine are bounded by $1$):
$$ R_5(x) \le \frac{1}{(5+1)!}\left(\frac{1}{2}\right)^6 \approx 2.17 \times 10^{-5} $$
If we evaluated $T_6(x)$ instead, the bound would be $\frac{1}{7!}(0.5)^7 \approx 1.55 \times 10^{-6}$.

### Exercise 3.31: Kinetic Energy in Special Relativity
Define the kinetic energy function $K(x) = mc^2\left(\frac{1}{\sqrt{1-x}} - 1\right)$, where $x = \frac{v^2}{c^2}$ and $v$ is the velocity.
Compute the first-order Taylor polynomial $T_1(x)$ around $0$:
$$ K'(x) = \frac{1}{2}mc^2(1-x)^{-3/2} $$
$$ T_1(x) = \frac{1}{2}mc^2 x $$
Substituting $x = \frac{v^2}{c^2}$:
$$ T_1\left(\frac{v^2}{c^2}\right) = \frac{1}{2}mv^2 \quad \text{(Classical Kinetic Energy formula)} $$

To bound the error $R_1$:
$$ K''(x) = \frac{3}{4}mc^2(1-x)^{-5/2} $$
$$ |R_1| \le \frac{M}{2!}x^2 = \frac{1}{2}\left(\frac{3}{4}mc^2(1-b)^{-5/2}\right)x^2 \approx \frac{3mv^4}{8c^2} $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="Taylors Inequality-1" src="https://github.com/user-attachments/assets/d474ce7f-e99f-44cd-9fab-7fa924ff3a50" />
    <img width="1264" height="1635" alt="Taylors Inequality-2" src="https://github.com/user-attachments/assets/b798e995-453c-4b8b-9309-2805a9e136b6" />
    <img width="1264" height="1635" alt="Taylors Inequality-3" src="https://github.com/user-attachments/assets/9af28c0d-e7ee-45c1-8286-ee14afba4a65" />
    <img width="1264" height="1635" alt="Taylors Inequality-4" src="https://github.com/user-attachments/assets/22a1e030-1160-42f7-95cc-cd95e0291074" />
    <img width="1264" height="1635" alt="Taylors Inequality-5" src="https://github.com/user-attachments/assets/8606d671-9366-4fc3-aae3-efe45d767a47" />
    <img width="1264" height="1635" alt="Taylors Inequality-6" src="https://github.com/user-attachments/assets/a8715a0f-53a1-4a25-9f20-5d6e4a17c8d8" />
  </div>
</details>
