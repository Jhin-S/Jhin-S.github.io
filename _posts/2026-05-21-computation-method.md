---
title: "4-2 Computation Method"
date: 2026-05-21 22:35:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, limit, squeeze_theorem]
math: true
---

## 1. Computation Rules and Standard Limits

### Learning Objectives
* Review and apply fundamental computation rules and standard limits.
* Compute complex limits by decomposing functions and applying these established rules.

### Computation Rules for Limits
Suppose that $\lim_{x \to \infty} f(x) = a$ and $\lim_{x \to \infty} g(x) = b$. Then the following properties hold true:
* **Sum Rule:**
  $$ \lim_{x \to \infty} [f(x) + g(x)] = \lim_{x \to \infty} f(x) + \lim_{x \to \infty} g(x) = a + b $$
* **Scalar Multiple Rule:**
  $$ \lim_{x \to \infty} [c \cdot f(x)] = c \lim_{x \to \infty} f(x) = c \cdot a $$
* **Product Rule:**
  $$ \lim_{x \to \infty} [f(x) \cdot g(x)] = \left(\lim_{x \to \infty} f(x)\right) \left(\lim_{x \to \infty} g(x)\right) = a \cdot b $$
* **Quotient Rule:**
  $$ \lim_{x \to \infty} \frac{f(x)}{g(x)} = \frac{\lim_{x \to \infty} f(x)}{\lim_{x \to \infty} g(x)} = \frac{a}{b} \quad \text{(provided } b \neq 0\text{)} $$

### Standard Limits with Composition
Suppose $\lim_{x \to \infty} f(x) = a$ and the outer function $h(x)$ is continuous (does not have a jump) at $x = a$. Then:
$$ \lim_{x \to \infty} h(f(x)) = h\left( \lim_{x \to \infty} f(x) \right) = h(a) $$

---

## 2. Advanced Evaluation Techniques

### Division by the Dominant Term
When dealing with rational functions, dividing the numerator and the denominator by the highest power of $x$ (the dominant term) is an effective strategy.
**Example:**
$$ \lim_{x \to \infty} \frac{2x^2 + 5x + 1}{3x^2 + 2} = \frac{2}{3} $$

### The Squeeze Theorem
The Squeeze Theorem helps determine limits of functions that are bounded by two other functions with known limits.

**Objectives:**
* Understand how to utilize the Squeeze Theorem to find horizontal asymptotes.
* Identify suitable envelope functions to bound a given function.

**Theorem Statement:**
Suppose $f(x)$, $g(x)$, and $h(x)$ are three functions such that:
$$ g(x) \le f(x) \le h(x) $$
for all $x$ greater than some value $M$. If both bounding functions approach the same limit $a$:
$$ \lim_{x \to \infty} g(x) = a = \lim_{x \to \infty} h(x) $$
Then the function squeezed in between must also approach that same limit:
$$ \lim_{x \to \infty} f(x) = a $$

---

## 3. Practice Exercises

### Exercise 4.22
Evaluate the following limit:
$$ \lim_{x \to \infty} \arctan\left(1 + \frac{1}{x} \cos^2 x\right) $$

**Solution:**
As $x$ approaches infinity, the term $\frac{1}{x}$ approaches $0$. Since $\cos^2 x$ is always bounded between $0$ and $1$, the product $\frac{1}{x} \cos^2 x$ gets squeezed to $0$.
Therefore, the inner expression converges to $1$:
$$ \lim_{x \to \infty} \left(1 + \frac{1}{x} \cos^2 x\right) = 1 $$
Using the composition rule, we evaluate the outer continuous function:
$$ \arctan(1) = \frac{\pi}{4} $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-2 Computation Method-1" src="https://github.com/user-attachments/assets/af8f55c2-ef17-4a27-9e2d-c0b29d8ee97e" />
    <img width="1264" height="1635" alt="4-2 Computation Method-2" src="https://github.com/user-attachments/assets/bde6673c-ee64-46a3-b64b-3f9f41a95953" />
    <img width="1264" height="1635" alt="4-2 Computation Method-3" src="https://github.com/user-attachments/assets/1fc48dc1-6772-4f48-9b38-84ab4e263451" />
  </div>
</details>
