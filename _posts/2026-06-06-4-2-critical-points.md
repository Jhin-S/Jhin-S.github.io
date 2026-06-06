---
title: "4-2 Critical Points"
date: 2026-06-06 10:30:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, critical-point, hessian-matrix, saddle-point, eigenvalue]
math: true
---

## 1. 임계점과 페르마의 정리 (Critical Points & Fermat's Theorem)

**[KR]** 다변수 함수에서 특정 방향으로의 변화율(방향 도함수)이 0이 되거나, 아예 미분이 불가능하여 변화율이 존재하지 않는 지점을 **임계점(Critical Point)**이라고 부릅니다. 
페르마의 정리(Fermat's Theorem)에 따르면, 함수가 어떤 지점에서 지역 최댓값이나 지역 최솟값을 가진다면 그 지점은 반드시 임계점이어야 합니다. 하지만 그 역은 성립하지 않습니다. 임계점이긴 하지만 최댓값도 최솟값도 아닌 독특한 지점을 우리는 **안장점(Saddle Point)**이라고 부릅니다.

**[EN]** A point in the domain of a function is called a **Critical Point** if the directional derivative is zero in all directions (i.e., the gradient is a zero vector), or if the derivative fails to exist. 
According to Fermat's Theorem, if a function attains a local maximum or minimum at a point, that point must inevitably be a critical point. However, a critical point does not guarantee an extremum; a point that is critical but neither a maximum nor a minimum is known as a **Saddle Point**.

---

## 2. 이계 편도함수 판정법 (Second Derivatives Test for Two Variables)

**[KR]** 1변수 함수에서 한 번 더 미분하여 극대/극소를 찾았듯이, 2변수 함수에서도 이계 편도함수들을 조합하여 극값을 판별할 수 있습니다. 판별식 $D$를 다음과 같이 정의합니다.

**[EN]** Just as we used the second derivative to classify extrema in single-variable calculus, we can combine second-order partial derivatives to classify critical points for functions of two variables. We define the discriminant $D$ as:

$$
D(a, b) = f_{xx}(a, b) \cdot f_{yy}(a, b) - [f_{xy}(a, b)]^2
$$

이 판별식 $D$의 부호와 $f_{xx}$의 부호에 따라 임계점의 성질이 결정됩니다.
* $D > 0$ 이고 $f_{xx} < 0$ 이면 $\implies$ **지역 최댓값 (Local Maximum)**
* $D > 0$ 이고 $f_{xx} > 0$ 이면 $\implies$ **지역 최솟값 (Local Minimum)**
* $D < 0$ 이면 $\implies$ **안장점 (Saddle Point)**
* $D = 0$ 이면 $\implies$ **판별 불가 (Inconclusive)**

---

## 3. 헤세 행렬과 고윳값 판정법 (Hessian Matrix & Eigenvalues)

**[KR]** 변수가 3개 이상으로 늘어나면 판별식 $D$를 직관적으로 쓰기 어렵습니다. 이때는 모든 2계 편도함수들을 행렬 형태로 모아놓은 **헤세 행렬(Hessian Matrix)**을 사용합니다. 이 행렬의 **고윳값(Eigenvalues, $\lambda$)**을 구하면 임계점의 종류를 완벽하게 분류할 수 있습니다.

**[EN]** When dealing with functions of three or more variables, calculating a simple discriminant $D$ becomes impractical. Instead, we construct the **Hessian Matrix**, which contains all possible second-order partial derivatives. By evaluating the **Eigenvalues ($\lambda$)** of this matrix, we can cleanly classify the critical point.

1. 모든 고윳값이 양수 ($\lambda_i > 0$) $\implies$ **지역 최솟값 (Local Minimum)**
2. 모든 고윳값이 음수 ($\lambda_i < 0$) $\implies$ **지역 최댓값 (Local Maximum)**
3. 양수와 음수 고윳값이 섞여 있음 $\implies$ **안장점 (Saddle Point)**
4. 고윳값 중 0이 존재함 $\implies$ **판별 불가 (Inconclusive)**

---

## 4. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 임계점 분류하기 (Classifying Critical Points)
**[KR]** 함수 $f(x, y) = -3x^2 + 6xy + 3y^2 - 2y^3$ 의 임계점을 찾고, 그 성질을 분류해 봅시다.
**[EN]** Find the critical points of the function $f(x, y) = -3x^2 + 6xy + 3y^2 - 2y^3$ and classify them.

먼저 1계 편도함수를 구하여 0이 되는 지점을 찾습니다.
* $f_x = -6x + 6y = 0 \implies x = y$
* $f_y = 6x + 6y - 6y^2 = 0$

위에서 얻은 $x = y$를 두 번째 식에 대입하면 $12y - 6y^2 = 0$ 이 되어 $y = 0$ 또는 $y = 2$ 가 도출됩니다. 따라서 두 개의 임계점 $P_1(0, 0)$과 $P_2(2, 2)$를 얻습니다.

이제 2계 편도함수를 구하여 판별식 $D$를 만듭니다.
* $f_{xx} = -6$
* $f_{yy} = 6 - 12y$
* $f_{xy} = 6$
* $D = (-6)(6 - 12y) - 6^2 = 72y - 72$

**[점 판별]**
1. **$P_1(0, 0)$ 대입:** $D = -72 < 0$. 따라서 $P_1$은 **안장점(Saddle Point)**입니다.
2. **$P_2(2, 2)$ 대입:** $D = 144 - 72 = 72 > 0$. 그리고 $f_{xx} = -6 < 0$ 이므로, $P_2$는 **지역 최댓값(Local Maximum)**입니다.

---

### Exercise 2: 극솟값을 가지는 분수 형태의 다변수 함수 (Fractional Multivariable Function)
**[KR]** 함수 $f(x, y) = x + y + \frac{1}{xy}$ 에 대하여 임계점을 찾고 분류합니다. ($x, y \neq 0$)
**[EN]** Find and classify the critical points for the function $f(x, y) = x + y + \frac{1}{xy}$.

* $f_x = 1 - \frac{1}{x^2y} = 0 \implies x^2y = 1$
* $f_y = 1 - \frac{1}{xy^2} = 0 \implies xy^2 = 1$

두 식을 연립하여 풀면 $x^3 = 1$ 이 되어 유일한 실수해 $x = 1$, $y = 1$ 을 얻습니다. 임계점은 $(1, 1)$ 하나뿐입니다.

이계 편도함수와 판별식을 구합니다.
* $f_{xx} = \frac{2}{x^3y}$, $f_{yy} = \frac{2}{xy^3}$, $f_{xy} = \frac{1}{x^2y^2}$
* 점 $(1, 1)$에서 $f_{xx} = 2$, $f_{yy} = 2$, $f_{xy} = 1$ 입니다.
* $D = (2)(2) - 1^2 = 3 > 0$ 이고, $f_{xx} = 2 > 0$ 이므로 이 지점은 **지역 최솟값(Local Minimum)**입니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-2 Critical Points-01" src="https://github.com/user-attachments/assets/f894ca12-3a32-4c31-aacf-1e65631047f9" />
    <img width="1264" height="1635" alt="4-2 Critical Points-02" src="https://github.com/user-attachments/assets/2550e2ea-acee-4ca0-bd83-396363638903" />
    <img width="1264" height="1635" alt="4-2 Critical Points-03" src="https://github.com/user-attachments/assets/87c79f67-bce1-4d4c-9ffc-b4a223de0c49" />
    <img width="1264" height="1635" alt="4-2 Critical Points-04" src="https://github.com/user-attachments/assets/6aface1c-7145-41df-bcc0-03688080b10b" />
    <img width="1264" height="1635" alt="4-2 Critical Points-05" src="https://github.com/user-attachments/assets/7c3ef329-611e-421f-a12b-4994402f96b6" />
    <img width="1264" height="1635" alt="4-2 Critical Points-06" src="https://github.com/user-attachments/assets/5c746324-5507-4c87-a418-8a01f76d32b1" />
    <img width="1264" height="1635" alt="4-2 Critical Points-07" src="https://github.com/user-attachments/assets/107a451b-7dd2-4171-8c71-45e43a06986e" />
    <img width="1264" height="1635" alt="4-2 Critical Points-08" src="https://github.com/user-attachments/assets/4a08609e-fb74-457f-9f16-d758047c191e" />
    <img width="1264" height="1635" alt="4-2 Critical Points-09" src="https://github.com/user-attachments/assets/e179e8eb-b4ca-40de-a9d1-04a9ff1c2129" />
    <img width="1264" height="1635" alt="4-2 Critical Points-10" src="https://github.com/user-attachments/assets/0e5f8a36-6d75-4ef7-a666-fbfdd6b9d672" />
  </div>
</details>
