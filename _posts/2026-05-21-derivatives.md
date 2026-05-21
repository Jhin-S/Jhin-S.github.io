---
title: "2-1 Derivatives"
date: 2026-05-21 22:30:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, derivative]
math: true
---

## 1. Introduction to Derivatives

### Standard Derivatives
* **Power of $x$:** $(x^r)' = rx^{r-1}$ (for any real value $r$)
* **Exponential function:** $(e^x)' = e^x$
* **Natural logarithm:** $(\ln x)' = \frac{1}{x}$
* **Sine function:** $(\sin x)' = \cos x$
* **Cosine function:** $(\cos x)' = -\sin x$

### Computation Rules
* **Scalar multiplication rule:** $(c \cdot f(x))' = c \cdot f'(x)$ (for any real value $c$)
* **Sum rule:** $(f(x) + g(x))' = f'(x) + g'(x)$
* **Product rule:** $(f(x)g(x))' = f'(x)g(x) + f(x)g'(x)$
* **Chain rule:** $(f(g(x)))' = f'(g(x))g'(x)$

---

## 2. Rate of Change & Derivative of a Function

### Rate of Change (변화율)
The rate of change of function $y = f(x)$ over the interval $[a, b]$ is given by:
$$ \frac{\Delta y}{\Delta x} = \frac{f(b) - f(a)}{b - a} $$

Letting the width $\Delta x$ of the interval $[a, b]$ approach $0$, the rate of change of the function will approach the derivative $f'(a)$ at the point $a$:
$$ f'(a) = \lim_{\Delta x \rightarrow 0} \frac{\Delta y}{\Delta x} = \lim_{b \rightarrow a} \frac{f(b) - f(a)}{b - a} $$

### Derivative of a Function (도함수)
Given a function $f: D \rightarrow \mathbb{R}$ that is differentiable at each point $a$ in $D$, we define the derivative $f': D \rightarrow \mathbb{R}$ as the function that associates the derivative of $f$ at $a$ to each point $a$ in the domain.

---

## 3. Implicit Differentiation (음함수 미분)

Implicit differentiation allows us to compute the slope of a curve without explicitly solving for $y$.
**Example: Equation of the circle**
$$ x^2 + y^2 = 9 \implies x^2 + (y(x))^2 = 9 $$

---

## 4. Derivative of Inverse (Trigonometric) Functions

### Standard Formulas
$$ \frac{d}{dx}\arcsin(x) = \frac{1}{\sqrt{1-x^2}} $$
$$ \frac{d}{dx}\arccos(x) = \frac{-1}{\sqrt{1-x^2}} $$
$$ \frac{d}{dx}\arctan(x) = \frac{1}{1+x^2} $$

### Derivations Using Implicit Differentiation

**1. $y = \arcsin(x)$**
$$ \sin y = x $$
$$ y' \cos y = 1 \implies y' = \frac{1}{\cos y} = \frac{1}{\sqrt{1 - \sin^2 y}} = \frac{1}{\sqrt{1 - x^2}} $$

**2. $y = \arccos(x)$**
$$ \cos y = x $$
$$ -y' \sin y = 1 \implies y' = \frac{-1}{\sin y} = \frac{-1}{\sqrt{1 - \cos^2 y}} = \frac{-1}{\sqrt{1 - x^2}} $$

**3. $y = \arctan(x)$**
$$ \tan y = x $$
Using $\frac{d}{dy}\tan y = \frac{1}{\cos^2 y}$:
$$ y' \frac{1}{\cos^2 y} = 1 \implies y' = \cos^2 y = \frac{1}{1 + \tan^2 y} = \frac{1}{1 + x^2} $$

### Derivative of General Inverse Function
For a general inverse function $y = f^{-1}(x)$:
$$ f(y) = x $$
$$ y' f'(y) = 1 \implies y' = \frac{1}{f'(y)} $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-1" src="https://github.com/user-attachments/assets/030497de-dd54-422c-9e30-aeaf6e934e7c" />
    <img width="1264" height="1635" alt="3-2" src="https://github.com/user-attachments/assets/0113959b-9c6b-4525-b2d1-d0ea6f38d41e" />
    <img width="1264" height="1635" alt="3-3" src="https://github.com/user-attachments/assets/9b9fda14-7ec6-4714-b863-89db691fd570" />
    <img width="1264" height="1635" alt="3-4" src="https://github.com/user-attachments/assets/61e2b69d-bf80-41be-a54c-f3b840f860c9" />
  </div>
</details>
