---
title: "5-2 Computation by anti-derivative"
date: 2026-05-21 22:45:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus I: From Functions to Differential Equations"]
tags: [calculus, tudelft, math, integral, anti-derivative]
math: true
---

## 1. The Fundamental Theorem & Anti-derivatives

### Anti-derivative
A function $F(x)$ is defined as the anti-derivative of $f(x)$ if its derivative equals $f(x)$:
$$ F'(x) = f(x) $$

### Fundamental Theorem of Calculus
The fundamental theorem connects the concepts of differentiation and integration. It allows us to evaluate definite integrals easily using anti-derivatives:
$$ \int_{a}^{b} f(x) \, dx = F(b) - F(a) $$

---

## 2. Integration Techniques

### Integration by Substitution
When an integral contains a composite function multiplied by its inner derivative, we can simplify it by substituting $u = g(x)$. Consequently, $du = g'(x)dx$.
For definite integrals, the boundaries must also change accordingly:
$$ \int_{a}^{b} f(g(x))g'(x) \, dx = \int_{g(a)}^{g(b)} f(u) \, du $$

### Integration by Parts
This powerful technique originates from the product rule for differentiation:
$$ (fg)'(x) = f'(x)g(x) + f(x)g'(x) $$
By rearranging the terms and integrating both sides, we obtain the standard formula for integration by parts:
$$ \int f(x)g'(x) \, dx = f(x)g(x) - \int f'(x)g(x) \, dx $$

*(Note: Alternatively, if we let $F'(x) = f(x)$, it can be expressed as $\int f(x)g(x) \, dx = F(x)g(x) - \int F(x)g'(x) \, dx$)*

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-2 Computation by anti-derivative-1" src="https://github.com/user-attachments/assets/a6df771d-3f80-41a1-a47b-82181b240e1a" />
  </div>
</details>
