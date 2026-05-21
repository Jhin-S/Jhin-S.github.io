---
title: "6-4 Linear Second Order Differential Equations"
date: 2026-05-21 23:12:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, differential_equation, second_order]
math: true
---

## 1. Introduction to Second Order Equations

### Definition and Standard Form
A second-order linear differential equation is any equation that can be organized into the following standard format:
$$ a(x)y'' + b(x)y' + c(x)y = F(x) $$

### Homogeneous Equations
When the function on the right-hand side, $F(x)$, is exactly equal to zero, the differential equation is classified as **homogeneous**. The simplified form is:
$$ a(x)y'' + b(x)y' + c(x)y = 0 $$

---

## 2. Solutions to Homogeneous Equations

### Linear Combination
**Theorem:** If two specific functions, $y_1$ and $y_2$, are valid solutions to a homogeneous linear second-order differential equation, then any linear combination of these two functions will also be a valid solution.

**Definition:** A linear combination of two functions $y_1$ and $y_2$ is mathematically constructed as:
$$ y = c_1y_1 + c_2y_2 $$
where $c_1$ and $c_2$ represent arbitrary constants.

### Linear Independence
**Definition:** Two functions $y_1$ and $y_2$ are considered **linearly independent** if one is not simply a constant multiple of the other. In mathematical terms, $y_1 \neq \alpha y_2$ and $y_2 \neq \beta y_1$ for any given constants $\alpha$ and $\beta$.

### General Solution (Homogeneous Case)
**Theorem:** If you have found two linearly independent functions $y_1$ and $y_2$ that solve a homogeneous linear second-order differential equation, the comprehensive general solution is formulated as:
$$ y = c_1y_1 + c_2y_2 $$

---

## 3. Solutions to Non-Homogeneous Equations

### Linearity in the Non-Homogeneous Case
**Theorem:** If you discover two distinct solutions, $y_1$ and $y_2$, for a non-homogeneous second-order linear differential equation, their difference:
$$ y = y_2 - y_1 $$
will act as a valid solution to the associated complementary (homogeneous) equation.

### General Solution (Non-Homogeneous Case)
**Theorem:** To construct the complete general solution for a non-homogeneous equation, you need two components:
1. Two linearly independent solutions ($y_1$ and $y_2$) to the complementary homogeneous equation.
2. A single particular solution ($y_p$) that satisfies the non-homogeneous equation.

The final general solution is given by adding these components together:
$$ y = y_p + c_1y_1 + c_2y_2 $$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-4 Linear Second Order Differential Equations-1" src="https://github.com/user-attachments/assets/fc56a490-b9c3-43c9-8aef-e9c282959155" />
    <img width="1264" height="1635" alt="6-4 Linear Second Order Differential Equations-2" src="https://github.com/user-attachments/assets/3414c603-1385-490b-b9db-efd7310fce6d" />
    <img width="1264" height="1635" alt="6-4 Linear Second Order Differential Equations-3" src="https://github.com/user-attachments/assets/3b621b00-37a4-4b75-a1f0-3918d6130804" />
  </div>
</details>
