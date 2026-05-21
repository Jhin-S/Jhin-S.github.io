---
title: "5-4 Integrating over unbounded domains"
date: 2026-05-21 22:55:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, improper_integral, convergence]
math: true
---

## 1. Introduction to Improper Integrals

### The Comparison Rule for Integrals
Evaluating integrals over unbounded intervals (intervals that extend to infinity) can be tricky. However, an integral over an infinite domain will converge to a finite number if the integrand approaches zero at a sufficiently fast rate. 

Therefore, a practical way to determine convergence without fully evaluating the integral is to compare it with a known reference function whose convergence properties are already established.

### Reference Examples for Convergence
It is highly useful to memorize a few standard functions and their convergence behaviors:

1. **Exponential Decay:** The function $e^{-x}$ decays rapidly enough.
   $$ \int_0^\infty e^{-x} \, dx = \lim_{b \to \infty} \left[ -e^{-x} \right]_0^b = 1 $$
2. **Power Functions (p-test):** * When $p > 1$, the function $\frac{1}{x^p}$ decays quickly enough to converge:
     $$ \int_1^\infty \frac{1}{x^p} \, dx = \lim_{b \to \infty} \left[ \frac{x^{1-p}}{1-p} \right]_1^b = \frac{1}{p-1} $$
   * When $p < 1$, it does not decay fast enough and diverges:
     $$ \int_1^\infty \frac{1}{x^p} \, dx = \lim_{b \to \infty} \left[ \frac{x^{1-p}}{1-p} \right]_1^b = \infty $$
   * When $p = 1$, the integral also diverges:
     $$ \int_1^\infty \frac{1}{x} \, dx = \lim_{b \to \infty} [\ln x]_1^b = \infty $$

---

## 2. Formal Definitions

### Intervals $[a, \infty)$ and $(-\infty, b]$
The integral of a function $f(x)$ extending to positive infinity is defined as a limit:
$$ \int_a^\infty f(x) \, dx = \lim_{b \to \infty} \int_a^b f(x) \, dx $$

Similarly, for negative infinity:
$$ \int_{-\infty}^b f(x) \, dx = \lim_{a \to -\infty} \int_a^b f(x) \, dx $$

> **Note:** The improper integral converges if this limit results in a finite number, and diverges otherwise.

### The Interval $(-\infty, \infty)$
For integrals extending over the entire real line, we split the interval at an arbitrary constant $c$:
$$ \int_{-\infty}^\infty f(x) \, dx = \int_{-\infty}^c f(x) \, dx + \int_c^\infty f(x) \, dx $$
The entire integral converges only if **both** separated integrals converge.

---

## 3. Practice Exercises

### Exercise 5.38: Convergence Test
Determine whether $\int_0^\infty \frac{x^2}{x^5 + 1} \, dx$ converges or diverges.
* Notice that for large $x$, $\frac{x^2}{x^5 + 1} < \frac{x^2}{x^5} = \frac{1}{x^3}$.
* The integral over $[0, 1]$ is finite.
* For the interval $[1, \infty)$, we know $\int_1^\infty \frac{1}{x^3} \, dx$ converges (since $p=3 > 1$). 
* By the comparison rule, the original integral **converges**.

### Exercise 5.39: Exponential Integral
Evaluate $\int_n^\infty e^{-x/n} \, dx$.
$$ \lim_{b \to \infty} \int_n^b e^{-x/n} \, dx = \lim_{b \to \infty} \left[ -n e^{-x/n} \right]_n^b = \lim_{b \to \infty} \left( -n e^{-b/n} + n e^{-1} \right) = \frac{n}{e} $$

### Exercise 5.40: Logarithmic Substitution
Evaluate $\int_e^\infty \frac{1}{x(\ln x)^7} \, dx$.
Let $t = \ln x$, then $dt = \frac{1}{x} dx$. The bounds change from $[e, \infty)$ to $[1, \infty)$.
$$ \int_1^\infty \frac{1}{t^7} \, dt = \lim_{b \to \infty} \left[ -\frac{1}{6t^6} \right]_1^b = 0 - \left( -\frac{1}{6} \right) = \frac{1}{6} $$

### Exercise 5.41: Arctangent Substitution
Evaluate $\int_0^\infty \frac{\arctan x}{1+x^2} \, dx$.
Let $\theta = \arctan x$. The derivative is $d\theta = \frac{1}{1+x^2} dx$.
The boundaries shift from $x=0 \to \theta=0$ and $x \to \infty \to \theta=\frac{\pi}{2}$.
$$ \int_0^{\pi/2} \theta \, d\theta = \left[ \frac{1}{2}\theta^2 \right]_0^{\pi/2} = \frac{1}{2}\left(\frac{\pi}{2}\right)^2 = \frac{\pi^2}{8} $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 (클릭)</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-4 Integrating over unbounded domains-1" src="https://github.com/user-attachments/assets/5336be73-2049-4bb9-9133-bdf5fa6c1b5a" />
    <img width="1264" height="1635" alt="5-4 Integrating over unbounded domains-2" src="https://github.com/user-attachments/assets/4856ea16-c9c9-4ae5-93ec-b277faa4ef15" />
    <img width="1264" height="1635" alt="5-4 Integrating over unbounded domains-3" src="https://github.com/user-attachments/assets/6b72b6b8-0740-4f15-9239-33b45ee9a5c4" />
  </div>
</details>
