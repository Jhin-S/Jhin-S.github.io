---
title: "다변수 테일러 전개 (Multivariable Taylor Series)"
date: 2026-06-06 14:30:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, taylor-series, hessian, tensor-product]
math: true
---

## 1. 다변수 함수의 테일러 전개 (Multivariable Taylor Expansion)

**[KR]** 일변수 함수의 테일러 전개는 다변수 함수 영역으로 확장될 수 있습니다. 다변수 함수 $f(\mathbf{x})$를 점 $\mathbf{a}$ 주변에서 근사할 때, 1차 도함수는 그래디언트(Gradient) 벡터, 2차 도함수는 헤세 행렬(Hessian Matrix), 그리고 3차 이상의 고차 도함수는 텐서(Tensor)의 형태로 나타나게 됩니다. 이를 일반화된 텐서 표기법으로 나타내면 다음과 같습니다.

**[EN]** The Taylor series expansion for single-variable functions can be elegantly extended to multivariable functions. When approximating a function $f(\mathbf{x})$ around a point $\mathbf{a}$, the first derivative becomes the Gradient vector, the second becomes the Hessian matrix, and higher-order derivatives take the form of Tensors. The generalized formula using tensor notation is:

$$
f(\mathbf{x}) = \sum_{k=0}^{n} \frac{1}{k!} \nabla^k f(\mathbf{a}) (\mathbf{x} - \mathbf{a})^{\otimes k}
$$

* **1차 근사 (선형 근사):** 그래디언트 벡터 $\nabla f$와 변위 벡터의 내적(행렬곱)으로 계산됩니다.
* **2차 이상 근사:** $\nabla^k$ 와 같은 고차 미분 연산자는 **텐서곱(Tensor Product, $\otimes$)**을 통해 전개됩니다. 질문하신 내용처럼 1차 미분까지는 단순한 행렬곱(내적)의 형태를 띠지만, 2차 이상의 차원으로 넘어가면 텐서곱을 적용하여 다차원 배열 간의 연산을 수행하는 것이 맞습니다.

---

## 2. 2차 테일러 근사 (Quadratic Approximation)

**[KR]** 2차 테일러 다항식 $T_2$를 구할 때는 그래디언트와 헤세 행렬을 이용합니다.
**[EN]** The second-order Taylor polynomial $T_2$ is constructed using the gradient and the Hessian matrix.

$$
f(\mathbf{x}) \approx f(\mathbf{a}) + \nabla f(\mathbf{a})^T (\mathbf{x} - \mathbf{a}) + \frac{1}{2} (\mathbf{x} - \mathbf{a})^T \nabla^2 f(\mathbf{a}) (\mathbf{x} - \mathbf{a})
$$

### Exercise 1: 다항 함수의 2차 근사
함수 $f(x, y) = x^2y + 3xy^2$ 에 대하여 점 $(1, 1)$에서의 2차 테일러 다항식 $T_2$를 구해봅시다.

1. **함숫값:** $f(1, 1) = 1 + 3 = 4$
2. **그래디언트 (1차 미분):**
   $$f_x = 2xy + 3y^2, \quad f_y = x^2 + 6xy$$
   $$\nabla f(1, 1) = (5, 7)$$
3. **헤세 행렬 (2차 미분):**
   $$f_{xx} = 2y, \quad f_{xy} = f_{yx} = 2x + 6y, \quad f_{yy} = 6x$$
   $$H(1, 1) = \nabla^2 f(1, 1) = \begin{pmatrix} 2 & 8 \\ 8 & 6 \end{pmatrix}$$
4. **텐서 전개식 대입:** 행렬 연산을 통해 2차항을 전개합니다.
   $$(\mathbf{x} - \mathbf{a})^{\otimes 2} \cdot H = 2(x-1)^2 + 6(y-1)^2 + 16(x-1)(y-1)$$

모든 요소를 종합하여 2차 테일러 근사식을 완성합니다. (2차항 앞에는 $\frac{1}{2!}$이 곱해짐에 주의합니다.)

$$
T_2(x, y) = 4 + 5(x-1) + 7(y-1) + (x-1)^2 + 3(y-1)^2 + 8(x-1)(y-1)
$$

---

## 3. 텐서곱을 활용한 고차 근사 (Higher-Order using Tensor Products)

**[KR]** 3차 이상의 근사를 수행하려면 $\nabla^3 f$를 구해야 하며, 이는 3차원 텐서 구조를 가집니다. 각 차수의 변위 벡터들의 텐서곱 $(\mathbf{x} - \mathbf{a})^{\otimes 3}$ 과 결합하여 항을 만들어냅니다.
**[EN]** For third-order approximations, we compute $\nabla^3 f$, which is a 3D tensor. This is contracted with the third tensor power of the displacement vector, $(\mathbf{x} - \mathbf{a})^{\otimes 3}$.

### Exercise 2: 지수함수가 포함된 3차 근사
함수 $f(x, y) = x e^y$ 에 대하여 점 $(1, 0)$에서의 3차 테일러 다항식 $T_3$를 전개해 봅시다.

1. **초기값 및 그래디언트:**
   $$f(1, 0) = 1$$
   $$\nabla f = (e^y, xe^y) \implies \nabla f(1, 0) = (1, 1)$$

2. **2차 텐서 (헤세 행렬) 전개:**
   $$\nabla^2 f = \begin{pmatrix} 0 & e^y \\ e^y & xe^y \end{pmatrix} \implies \nabla^2 f(1, 0) = \begin{pmatrix} 0 & 1 \\ 1 & 1 \end{pmatrix}$$
   이를 변위 벡터 $(x-1, y)$ 의 텐서곱 행렬과 매칭하여 계산하면 2차항 성분은 $2y(x-1) + y^2$ 가 됩니다.

3. **3차 텐서 전개:**
   한 번 더 미분하여 $\nabla^3 f(1, 0)$를 평가하고, $(\mathbf{x}-\mathbf{a})^{\otimes 3}$ 과의 연산을 수행하면 비어있는 $0$ 성분들을 제외하고 $3(x-1)y^2 + y^3$ 이 도출됩니다.

계산된 1차, 2차, 3차 성분들에 각각의 팩토리얼 분모를 나누어 모두 더해주면 3차 테일러 근사식이 완성됩니다.

$$
T_3(x, y) = 1 + (x-1) + y + \frac{1}{2!}\Big(2(x-1)y + y^2\Big) + \frac{1}{3!}\Big(3(x-1)y^2 + y^3\Big)
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="다변수 테일러-1" src="https://github.com/user-attachments/assets/5747d99a-1d10-43fe-9a6c-b3e88425c62e" />
    <img width="1264" height="1635" alt="다변수 테일러-2" src="https://github.com/user-attachments/assets/9cfa0d78-556f-4251-8dd5-2ac42b0b669a" />
    <img width="1264" height="1635" alt="다변수 테일러-3" src="https://github.com/user-attachments/assets/eae9693c-7615-4d8c-8f11-a67f3a7c9ad2" />
  </div>
</details>
