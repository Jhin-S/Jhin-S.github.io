---
title: "5-3 Additional"
date: 2026-05-21 22:50:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, integral, taylor_series, approximation]
math: true
---

## 1. Approximating Integrals with Taylor Polynomials

### The Problem with Certain Anti-derivatives
Many important functions, such as $\cos(x^2)$, $\sin(x^2)$, and $e^{x^2}$, do not have anti-derivatives that can be expressed in terms of basic elementary functions. Other anti-derivatives might be theoretically possible but practically too difficult to find (e.g., $\frac{\tan^3(\ln x)}{x}$).

### The Solution: Taylor Polynomials
To bypass this issue, we can approximate the integrand using Taylor polynomials.
**Theorem:** Suppose $T_n(x)$ is the $n$-th order Taylor polynomial of a function $f(x)$. Then:
$$ \int T_n(x) \, dx $$
is the $(n+1)$-th order Taylor polynomial of the anti-derivative $F(x)$.

> **Corollary:** When using Taylor polynomials centered at $x=a$ to approximate the integral of $f(x)$ over an interval $[b, c]$, the entire interval should be reasonably close to the center point $a$ to minimize the error.

---

## 2. Bounding the Approximation Error

### Absolute Value of an Integral
If $f(x)$ is integrable over $[a, b]$, the absolute value of the integral is bounded by the integral of its absolute value:
$$ \left| \int_a^b f(x) \, dx \right| \le \int_a^b |f(x)| \, dx $$

### Taylor's Inequality for Integrals
Let $T_n(x)$ be the Taylor polynomial of $f(x)$ centered at $a$. If $|f^{(n+1)}(x)| \le M$ for all $x$ in the interval $[b, c]$, then the error of the integral approximation is bounded by:
$$ \left| \int_b^c f(x) \, dx - \int_b^c T_n(x) \, dx \right| \le \int_b^c \frac{M}{(n+1)!} |x-a|^{n+1} \, dx $$

---

## 3. Practice Exercises

### Exercise 5.34
Approximate $\int_0^1 e^{x^2} \, dx$ using the 3rd order Taylor polynomial of $f(x) = e^{x^2}$ around $a=0$.
* By substituting $x^2$ into $e^u \approx 1 + u$, we get $T_3(x) = 1 + x^2$.
* Approximation:
  $$ \int_0^1 (1 + x^2) \, dx = \left[ x + \frac{1}{3}x^3 \right]_0^1 = \frac{4}{3} $$
* Error Bound: Given the maximum value of $f^{(4)}(x)$ is $76e$ on $[0, 1]$, the error is bounded by:
  $$ \int_0^1 \frac{76e}{4!} x^4 \, dx = \frac{76e}{24} \cdot \frac{1}{5} = \frac{19}{30}e $$

### Exercise 5.35
Approximate $\int_0^1 \sin(x^3) \, dx$ using the 9th order Taylor polynomial around $a=0$.
* Using $\sin(u) \approx u - \frac{u^3}{3!}$, we substitute $u = x^3$:
  $$ T_9(x) = x^3 - \frac{1}{6}x^9 $$
* Approximation:
  $$ \int_0^1 \left( x^3 - \frac{1}{6}x^9 \right) \, dx = \left[ \frac{1}{4}x^4 - \frac{1}{60}x^{10} \right]_0^1 = \frac{1}{4} - \frac{1}{60} = \frac{14}{60} = \frac{7}{30} $$
* The error bound calculation simplifies to $\le \frac{1}{1920}$.

### Exercise 5.36
Approximate $\int_0^t x(\ln(1+x^2) - e^x) \, dx$ using the 4th order Taylor polynomial around $a=0$.
* Let $f(x) = \ln(1+x^2) \approx x^2$ and $g(x) = e^x \approx 1 + x + \frac{x^2}{2} + \frac{x^3}{6}$.
* Let $h(x) = x(f(x) - g(x)) \approx x \left( -1 - x + \frac{x^2}{2} - \frac{x^3}{6} \right) = -x - x^2 + \frac{x^3}{2} - \frac{x^4}{6}$.
* Approximation:
  $$ \int_0^t \left( -x - x^2 + \frac{x^3}{2} - \frac{x^4}{6} \right) \, dx = -\frac{1}{2}t^2 - \frac{1}{3}t^3 + \frac{1}{8}t^4 - \frac{1}{30}t^5 $$

### Exercise 5.37
Approximate $\int_{-1}^1 e^{-x^2} \, dx$ and estimate the maximum error given $|f^{(5)}(x)| \le 50$.
* The 4th order polynomial for $e^{-x^2}$ is $T_4(x) = 1 - x^2 + \frac{1}{2}x^4$.
* Approximation:
  $$ \int_{-1}^1 \left( 1 - x^2 + \frac{1}{2}x^4 \right) \, dx = 2 \left[ x - \frac{1}{3}x^3 + \frac{1}{10}x^5 \right]_0^1 = 2 \left( 1 - \frac{1}{3} + \frac{1}{10} \right) = \frac{23}{15} $$
* Error Estimation:
  $$ \int_{-1}^1 |f(x) - T_4(x)| \, dx \le \int_{-1}^1 \frac{50}{5!} |x|^5 \, dx = 2 \int_0^1 \frac{50}{120} x^5 \, dx = 2 \left[ \frac{5}{120 \cdot 6} x^6 \right]_0^1 = \frac{5}{36} $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-3 Additional-1" src="https://github.com/user-attachments/assets/570074ec-24cf-49e0-ae2c-3663fd84eea6" />
    <img width="1264" height="1635" alt="5-3 Additional-2" src="https://github.com/user-attachments/assets/26754efd-bb2b-41b7-9ecc-8a7273a88a92" />
    <img width="1264" height="1635" alt="5-3 Additional-3" src="https://github.com/user-attachments/assets/1ae06a0e-17fe-4d25-831e-0a56c2e7c3ba" />
    <img width="1264" height="1635" alt="5-3 Additional-4" src="https://github.com/user-attachments/assets/926e96ef-db85-46a2-b816-9fa241521153" />
    <img width="1264" height="1635" alt="5-3 Additional-5" src="https://github.com/user-attachments/assets/80da461f-9ba4-423b-976e-bca345158d6f" />
    <img width="1264" height="1635" alt="5-3 Additional-6" src="https://github.com/user-attachments/assets/6a3f7490-69b8-49a7-bbd8-2018071d8ea6" />
    <img width="1264" height="1635" alt="5-3 Additional-7" src="https://github.com/user-attachments/assets/825b9bd7-e73f-4b30-bb8f-695e9a8da8c8" />
  </div>
</details>
