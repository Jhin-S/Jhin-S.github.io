---
title: "4-1 Horizontal Asymptotes"
date: 2026-05-21 22:25:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, asymptote, limit]
math: true
---

## 1. Introduction to Horizontal Asymptotes

### Learning Objectives
* Identify various types of horizontal asymptotes by analyzing their graphical representations.
* Calculate the exact number of horizontal asymptotes for basic mathematical models.
* Understand the concept of a horizontal asymptote within real-world practical scenarios.
* Recognize why horizontal asymptotes are significant in applied contexts.

### Mathematical Definition
A given function $f(x)$ is said to have a horizontal asymptote at the line $y = a$ provided that:
$$ |f(x) - a| \rightarrow 0 \quad \text{as} \quad x \rightarrow \infty \quad \text{or} \quad x \rightarrow -\infty $$

> **Key Note:** Keep in mind that a single function might possess zero, one, or up to two unique horizontal asymptotic lines.

### Limit Notation
To express this mathematically using limits:
* If the line $y = a$ serves as a horizontal asymptote for $f(x)$ as $x$ approaches positive infinity, it is written as:
  $$ \lim_{x \rightarrow \infty} f(x) = a $$
* Similarly, if $y = a$ is the asymptote as $x$ approaches negative infinity, we represent it as:
  $$ \lim_{x \rightarrow -\infty} f(x) = a $$

---

## 2. Algebraic Manipulation for Asymptotes

Often, we need to rewrite rational functions to easily spot their horizontal asymptotes.

### Example 1
Consider the function $f(x) = \frac{x+2}{1-x}$. We can rearrange the terms as follows:
$$ f(x) = \frac{x+2}{-(x-1)} = -\frac{x+2}{x-1} $$
By splitting the numerator to match the denominator:
$$ f(x) = -\frac{(x-1) + 3}{x-1} = -1 - \frac{3}{x-1} $$
From this form, it is clear that as $x \rightarrow \pm\infty$, the term $\frac{3}{x-1} \rightarrow 0$, leaving a horizontal asymptote at $y = -1$.

### Exercise 4.3
Analyze the function $f(x) = \frac{x+2}{x+1}$.
Using a similar algebraic decomposition:
$$ f(x) = \frac{(x+1) + 1}{x+1} = 1 + \frac{1}{x+1} $$
As $x$ grows infinitely large, the fraction approaches zero, resulting in a horizontal asymptote at $y = 1$.

---

## 3. Applications of Asymptotes & Growth Rates

### Learning Objectives
* Order and rank different functions based on their relative growth rates.
* Explain why analyzing the growth rate is mathematically and practically relevant.
* Connect the concept of an equilibrium state to the mathematical definition of a horizontal asymptote.

### Defining Growth Rates
Let us analyze two diverging functions, $f_A(x)$ and $f_B(x)$, as $x$ gets increasingly larger. We can determine their relative growth behavior by evaluating the limit of their ratio:

1. **Higher Growth Rate:**
   If the ratio approaches zero, meaning the denominator grows much faster than the numerator:
   $$ \lim_{x \rightarrow \infty} \frac{f_A(x)}{f_B(x)} = 0 $$
   Then we conclude that $f_B(x)$ has a **higher growth rate** compared to $f_A(x)$.

2. **Equal Growth Rate:**
   If the limit converges to a non-zero constant $c$:
   $$ \lim_{x \rightarrow \infty} \frac{f_A(x)}{f_B(x)} = c $$
   This indicates that both $f_A(x)$ and $f_B(x)$ possess the **same growth rate**.

3. **Dominant Growth Rate:**
   If the ratio $\frac{f_A(x)}{f_B(x)}$ keeps increasing toward infinity, it implies that $f_A(x)$ strongly outpaces $f_B(x)$, giving it a **higher growth rate**.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-1 Horizontal Asymptotes-1" src="https://github.com/user-attachments/assets/abbde545-0aca-43b2-8268-9fa2c506ba11" />
    <img width="1264" height="1635" alt="4-1 Horizontal Asymptotes-2" src="https://github.com/user-attachments/assets/dc521127-fc9f-4d84-a861-733c06b0016a" />
    <img width="1264" height="1635" alt="4-1 Horizontal Asymptotes-3" src="https://github.com/user-attachments/assets/d53c1abb-6ca7-4a68-9b04-8a03028790e8" />
  </div>
</details>
