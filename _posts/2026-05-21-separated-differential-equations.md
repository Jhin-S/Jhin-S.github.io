---
title: "6-2 Separated Differential Equations"
date: 2026-05-21 23:05:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, differential_equation, separable]
math: true
---

## 1. Concept of Separable Differential Equations

### An Introductory Example
Consider the simple differential equation $y' = 2y$. Let's test a few potential functions:
* $y(x) = x^2$ (Not a solution)
* $y(x) = e^{2x}$ (A valid solution!)
* $y(x) = e^x + 5$ (Not a solution)
* $y(x) = Ce^{2x}$ (This represents the **General Solution**, where $C \in \mathbb{R}$)

### Mathematical Definition
A first-order differential equation is classified as "separable" if its derivative term $\frac{dy}{dx}$ can be expressed strictly as the product of a function of $x$ and a function of $y$. 
Mathematically, this is written as:
$$ \frac{dy}{dx} = f(x)g(y) = \frac{f(x)}{h(y)} \quad \text{where } h(y) = \frac{1}{g(y)} $$
By separating the variables, we obtain the differential form:
$$ h(y)dy = f(x)dx $$
From here, we can simply integrate both sides to find the solution.

---

## 2. Solving Initial Value Problems

### Exercise 6.6
Find the solution for the initial-value problem $\frac{dy}{dt} = t^2y^2 - 2y^2$ with $y(1) = 1$.
* Factor the right side: $\frac{dy}{dt} = (t^2 - 2)y^2$
* Separate the variables: $\frac{1}{y^2} dy = (t^2 - 2) dt$
* Integrate both sides:
  $$ -y^{-1} = \frac{1}{3}t^3 - 2t + C $$
* Apply the initial condition $y(1) = 1$:
  $$ -1 = \frac{1}{3}(1) - 2(1) + C \implies -1 = -\frac{5}{3} + C \implies C = \frac{2}{3} $$
* Final solution:
  $$ y = \frac{1}{-\frac{1}{3}t^3 + 2t - \frac{2}{3}} $$

### Exercise 6.7
Evaluate the differential equation $y' = \frac{e^{3x}}{3y^2+1}$ given the initial value $y(0) = -2$.
* Separate variables: $(3y^2+1)dy = e^{3x}dx$
* Integrate:
  $$ y^3 + y = \frac{1}{3}e^{3x} + C $$
* Substitute $y(0) = -2$:
  $$ (-2)^3 + (-2) = \frac{1}{3}e^0 + C \implies -10 = \frac{1}{3} + C \implies C = -\frac{31}{3} $$
* Implicit solution:
  $$ y^3 + y = \frac{1}{3}e^{3x} - \frac{31}{3} $$

---

## 3. Additional Practice Exercises

### Exercise 6.8
Examine the equation $y' = (t+1)y(2y-4)$.
**1. Find all constant solutions:**
Constant solutions occur when $y' = 0$.
$$ y(2y-4) = 0 \implies y = 0 \quad \text{or} \quad y = 2 $$

**2. General integration using partial fractions:**
$$ \frac{dy}{(2y^2-4y)} = (t+1)dt \implies \frac{1}{2y(y-2)}dy = (t+1)dt $$
Decompose the fraction:
$$ \frac{A}{y} + \frac{B}{y-2} = \frac{1}{2y(y-2)} \implies A = -\frac{1}{4}, \quad B = \frac{1}{4} $$
Integration yields:
$$ -\frac{1}{4}\ln|y| + \frac{1}{4}\ln|y-2| = \frac{1}{2}t^2 + t + C $$

### Exercise 6.9
Solve the equation $y' = \cos(3t)(y^2+1)$ with $y(0) = \sqrt{3}$.
* Separate variables: $\frac{1}{y^2+1}dy = \cos(3t)dt$
* Integrate (using trigonometric substitution or standard integral):
  $$ \arctan y = \frac{1}{3}\sin(3t) + C $$
* Apply initial condition $y(0) = \sqrt{3}$:
  $$ \arctan(\sqrt{3}) = C \implies C = \frac{\pi}{3} $$
* Final solution:
  $$ y = \tan\left(\frac{1}{3}\sin(3t) + \frac{\pi}{3}\right) $$

### Exercise 6.10
Analyze the draining tank problem modeled by $y' = -k\sqrt{y}$ with $y(0) = H$.
* Separate and integrate:
  $$ y^{-1/2}dy = -k dt \implies 2y^{1/2} = -kt + C $$
* Apply the initial condition $y(0) = H$:
  $$ C = 2\sqrt{H} $$
* The exact equation becomes $2\sqrt{y} = -kt + 2\sqrt{H}$. (If $T$ is the total time to empty, we can also deduce $k = \frac{2\sqrt{H}}{T}$).

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-2 Separated Differential Equations-1" src="https://github.com/user-attachments/assets/998739bc-d9f5-4200-93d5-da705cbc2276" />
    <img width="1264" height="1635" alt="6-2 Separated Differential Equations-2" src="https://github.com/user-attachments/assets/1bdf61aa-53a7-42d0-9beb-cf5bf95098e7" />
    <img width="1264" height="1635" alt="6-2 Separated Differential Equations-3" src="https://github.com/user-attachments/assets/eb78c4ba-f9cc-4d92-a791-5c1fe85053c5" />
    <img width="1264" height="1635" alt="6-2 Separated Differential Equations-4" src="https://github.com/user-attachments/assets/643d8e1c-9f41-4cc8-be0c-0691e572042c" />
    <img width="1264" height="1635" alt="6-2 Separated Differential Equations-5" src="https://github.com/user-attachments/assets/285ff911-0b98-481d-8500-fc640ae658da" />
  </div>
</details>
