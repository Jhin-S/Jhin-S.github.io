---
title: "6-1 Introduction to Differential Equations"
date: 2026-05-21 23:00:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, differential_equation]
math: true
---

## 1. Fundamentals of Differential Equations

### What is a Differential Equation?
An equation is classified as a differential equation if it takes the form:
$$ F(x, y, y', y'', \dots, y^{(n)}) = 0 $$
Here, $y = y(x)$ represents a function dependent on the variable $x$.
* **Order ($n$):** The highest derivative present in the equation.
* **Independent variable:** $x$
* **Dependent variable:** $y$

### Verifying a Potential Solution
If you want to verify whether a particular function $y(x)$ is a valid solution, you should:
1. Calculate the derivatives of $y$ up to the $n$-th order.
2. Substitute $y(x)$ and all its computed derivatives back into the original equation $F$ to see if it perfectly equals $0$.

---

## 2. Types of Solutions and Equations

### General Solution
For a given $n$-th order differential equation, the general solution is expressed as a formula containing $n$ independent arbitrary constants ($C_1, C_2, \dots, C_n$). Any specific solution can be derived by assigning particular values to these constants.

### Initial Value Problem (IVP)
An initial value problem consists of a differential equation combined with specific starting conditions at a certain point $x = a$:
$$ y(a) = y_0, \quad y'(a) = y_1, \quad \dots, \quad y^{(n-1)}(a) = y_{n-1} $$

### Direction Field
For a first-order equation $F(x, y, y') = 0$, a direction field is constructed by drawing short line segments. Each segment at a point $(x, y)$ has a slope $y'$ that satisfies the equation.

### Autonomous Equations & Equilibriums
* **Autonomous Equation:** A differential equation is called autonomous if the independent variable $x$ does not explicitly appear in the equation. It can be written purely in terms of $y$ and its derivatives: $F(y, y', \dots, y^{(n)}) = 0$.
* **Equilibrium Solution:** This is a constant solution where the rate of change is zero, meaning $y'(x) = 0$.
  * *Example:* The cooling model $T' = -(T - 5)$ has an equilibrium state at $T(t) = 5$, which is determined by setting the derivative to zero ($0 = -(T - 5)$).

---

## 3. Practice Exercises

### Exercise 6.1
Identify the correct solutions for the equation $y'' - y = 0$.
* Let's test $y = Ce^{-x}$:
  $$ y' = -Ce^{-x} \implies y'' = Ce^{-x} $$
  Substituting back: $Ce^{-x} - Ce^{-x} = 0$. (Valid)
* Let's test $y = Ce^{x}$:
  $$ y' = Ce^{x} \implies y'' = Ce^{x} $$
  Substituting back: $Ce^{x} - Ce^{x} = 0$. (Valid)
* Therefore, the general solution involves combinations of $e^x$ and $e^{-x}$.

### Exercise 6.2
Determine the order of the following equation:
$$ \left(\frac{dy}{dx}\right)^3 - 2x\left(\frac{dy}{dx}\right) + y = 0 $$
* **Answer:** The highest derivative is the first derivative $\frac{dy}{dx}$, so it is a **1st-order** differential equation.

### Exercise 6.4
Find the equilibrium solution for $\cos\left(\frac{dy}{dx}\right) + y = 2$.
* For an equilibrium solution, the derivative must be zero ($\frac{dy}{dx} = 0$).
* Substituting this into the equation:
  $$ \cos(0) + y = 2 \implies 1 + y = 2 \implies y = 1 $$
* **Answer:** The equilibrium solution is $y = 1$.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-1 Introduction to Differential Equations-1" src="https://github.com/user-attachments/assets/518ba8b0-daf9-491f-8768-e4adb44074d8" />
    <img width="1264" height="1635" alt="6-1 Introduction to Differential Equations-2" src="https://github.com/user-attachments/assets/c08c5285-96ab-4685-848b-a43e23f7ab06" />
    <img width="1264" height="1635" alt="6-1 Introduction to Differential Equations-3" src="https://github.com/user-attachments/assets/08c8bcf5-ccfa-48fb-952e-5dec1fbf7448" />
    <img width="1264" height="1635" alt="6-1 Introduction to Differential Equations-4" src="https://github.com/user-attachments/assets/1fc9acaa-a0a5-494f-a7be-4702338b3a4f" />
  </div>
</details>
