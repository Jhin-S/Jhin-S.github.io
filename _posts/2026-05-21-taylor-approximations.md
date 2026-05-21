---
title: "3-2 Taylor Approximations"
date: 2026-05-21 22:15:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, taylor_series, approximation]
math: true
---

## 1. Taylor Polynomials (테일러 다항식)

### Definition
The $n$-th order Taylor polynomial $T_n(x)$ of a function $f(x)$ centered at $x=a$ is defined as:
$$ T_n(x) = \sum_{p=0}^{n} \frac{f^{(p)}(a)}{p!}(x-a)^p $$

---

## 2. Computation Rules

When generating Taylor polynomials, we can use existing polynomials to find new ones efficiently without computing all derivatives.

### Sum Rule
If $f(x) = g(x) + h(x)$, then the $n$-th order Taylor polynomial of $f$ is the sum of the $n$-th order polynomials of $g$ and $h$:
$$ T_n^f(x) = T_n^g(x) + T_n^h(x) $$
*(Note: All polynomials must be centered at the same point $x=a$.)*

### Product Rule
If $f(x) = (x-a)^k g(x)$, then the $(n+k)$-th order Taylor polynomial of $f$ centered at $x=a$ is:
$$ T_{n+k}^f(x) = (x-a)^k T_n^g(x) $$

### Substitution Rule
If we consider the composition $f(x) = g((x-a)^k)$, the $(n \cdot k)$-th order Taylor polynomial is given by substituting $(x-a)^k$ into the Taylor polynomial of $g$:
$$ T_{nk}^f(x) = \sum_{p=0}^{n} \frac{g^{(p)}(a)}{p!}(x-a)^{kp} $$

---

## 3. Examples & Exercises

### Example: Approximating $\sqrt{4.05}$
Use a second-order polynomial to approximate the value $\sqrt{4.05}$.
Let $f(x) = \sqrt{x} = x^{1/2}$ centered at $a=4$:
1. $f(4) = 2$
2. $f'(x) = \frac{1}{2}x^{-1/2} \implies f'(4) = \frac{1}{4}$
3. $f''(x) = -\frac{1}{4}x^{-3/2} \implies f''(4) = -\frac{1}{32}$

The second-order Taylor polynomial is:
$$ T_2(x) = 2 + \frac{1}{4}(x-4) - \frac{1}{64}(x-4)^2 $$
$$ \sqrt{4.05} \approx T_2(4.05) = 2 + \frac{1}{4}(0.05) - \frac{1}{64}(0.05)^2 = 2.0124609375 $$

### Exercise 3.19: $\sin x$ around $a = \frac{\pi}{3}$
$$ \sin x \approx \frac{\sqrt{3}}{2} + \frac{1}{2}\left(x-\frac{\pi}{3}\right) - \frac{\sqrt{3}}{4}\left(x-\frac{\pi}{3}\right)^2 - \frac{1}{12}\left(x-\frac{\pi}{3}\right)^3 $$

### Exercise 3.20: $e^x$ around $a = 5$
$$ T_3(x) = e^5 + e^5(x-5) + \frac{e^5}{2}(x-5)^2 + \frac{e^5}{6}(x-5)^3 $$

### Exercise 3.22: $7\ln(x)$ around $a = 1$
$$ f'(x) = \frac{7}{x}, \quad f''(x) = -\frac{7}{x^2}, \quad f'''(x) = \frac{14}{x^3} $$
$$ T_3(x) = 7(x-1) - \frac{7}{2}(x-1)^2 + \frac{7}{3}(x-1)^3 $$

### Exercise 3.26: Solve $e^x = 1.5$ using Taylor polynomials
Method: Use the 2nd order Taylor polynomial of $h(x) = e^x$ centered at $a=0$.
$$ T_2^h(x) = 1 + x + \frac{x^2}{2} = 1.5 $$
$$ x^2 + 2x - 1 = 0 \implies x = \frac{-2 \pm \sqrt{4 - 4(1)(-1)}}{2} = -1 \pm \sqrt{2} $$
Since $T_2^h$ is centered at $0$, the solution closer to $0$ is $x \approx 0.414$.

### Exercise 3.27: Find 8th order Taylor polynomial for $f(x) = 3 + x\cos(x^2)$ around $x=0$
Using computation rules:
$$ \cos(u) \approx 1 - \frac{u^2}{2} + \frac{u^4}{24} $$
Substitute $u = x^2$:
$$ \cos(x^2) \approx 1 - \frac{x^4}{2} + \frac{x^8}{24} $$
Multiply by $x$ and add $3$:
$$ T_8^f(x) = 3 + x - \frac{x^5}{2} $$
*(Note: The $x^9$ term exceeds the 8th order, so it is truncated.)*

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-1" src="https://github.com/user-attachments/assets/4f7c7672-42b6-495c-b81f-74b4bfd2d271" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-2" src="https://github.com/user-attachments/assets/ac9d09ad-a32c-4816-9c0f-ca35224b005a" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-3" src="https://github.com/user-attachments/assets/6ed40db8-e84e-4d07-b9be-d5d5cb5ec405" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-4" src="https://github.com/user-attachments/assets/5e716ffa-deb8-438e-be66-f7f5cfa247b6" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-5" src="https://github.com/user-attachments/assets/b7ec6053-b327-4db2-8d2e-5e1acf2c16bf" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-6" src="https://github.com/user-attachments/assets/f7246b1b-82a8-4ec8-8591-e4014f90b30a" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-7" src="https://github.com/user-attachments/assets/15ee177b-a544-46e4-b728-fec632129faf" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-8" src="https://github.com/user-attachments/assets/5d288721-0bef-4084-b6e1-07fd3a7c6aaf" />
    <img width="1264" height="1635" alt="3-2 Taylor Approximations-9" src="https://github.com/user-attachments/assets/d3cbd444-6886-4b4d-a840-819d4d0fdfea" />
  </div>
</details>
