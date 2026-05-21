---
title: "1-1 Introduction to Functions"
date: 2026-05-21 21:00:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, function]
math: true
---

## 1. Function (함수)

### Definition
A function $f$ associates exactly one real number $f(x)$ to any real number $x$ in the domain $D$. 
A function $f: \mathbb{R} \rightarrow \mathbb{R}$ associates to each number $x$ in its domain exactly one number $f(x)$.

**Example: Falling Object (낙하하는 물체)**
We find that $H(t)$ equals $h$ minus one half times $g$ times $t$ squared, where $g$ is gravitational acceleration.
$$ H(t) = h - \frac{1}{2}gt^2 $$

---

## 2. Graph & Vertical Line Test

### Graph Definition
The graph of a function is given by drawing a curve through the points with coordinates $x$ and $f(x)$ in the plane. The graph of a function $f: \mathbb{R} \rightarrow \mathbb{R}$ is the curve going through all the points $(x, f(x))$ for $x$ in the domain of $f$.

### Vertical Line Test Theorem
A curve in the plane is the graph of a function over a certain domain if every vertical line at $x$-values in that domain intersects the curve exactly once.

---

## 3. Domain and Range of a Function (정의역과 치역)

In the previous lesson, we saw that a function is an association of certain specific numbers to other specific numbers. An essential part of the information of a function is therefore contained in which numbers we are considering exactly. This information is contained in the domain and range of a function.

### Definition
For a function $f: A \rightarrow B$:
* The set $A$ of possible input values is called the **domain** (정의역).
* The set $B$ is called the **co-domain** (공역) of the function.
* The **range** $R$ (치역) of a function $f: A \rightarrow B$ is the set of all possible values of $f(x)$ as $x$ varies throughout the domain $A$.

**Example:**
For example, the function $f(x) = \frac{1}{x^2}$ has as maximal domain the set of all non-zero real numbers $\mathbb{R}$ excluding 0 ($\{x \in \mathbb{R} \mid x \neq 0\}$), because $\frac{1}{x^2}$ is defined for all non-zero numbers $x$.

---

## 4. Composition of Functions (합성 함수)

### Product of Functions
Given functions $f(x)$ and $g(x)$, we can form their product $(f \cdot g)$:
$$ (f \cdot g)(x) = f(x)g(x) $$

**Example:**
* $f(x) = \sqrt{x}$ (Domain: $[0, \infty)$)
* $g(x) = x + 2$ (Domain: $\mathbb{R}$)
* Product: $(f \cdot g)(x) = (x+2)\sqrt{x}$ (Domain: $[0, \infty)$)

### Composite Function
If $f$ and $g$ are two functions, the composite function $f \circ g$ is defined by:
$$ (f \circ g)(x) = f(g(x)) $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1" src="https://github.com/user-attachments/assets/acdc66e9-c30e-4f92-9d54-26fcb6dc9e54" />
    <img width="1264" height="1635" alt="1-2" src="https://github.com/user-attachments/assets/3a36f450-e53c-42da-b42e-778bc629f894" />
    <img width="1264" height="1635" alt="1-3" src="https://github.com/user-attachments/assets/5bcd7168-63c6-47fc-ae01-8319f5fbe458" />
    <img width="1264" height="1635" alt="1-4" src="https://github.com/user-attachments/assets/632ad889-556d-482c-8da0-7a4a8793708f" />
  </div>
</details>
