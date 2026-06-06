---
title: "5-2 Double Integrals over rectangles"
date: 2026-06-06 10:41:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, double-integral, fubinis-theorem, iterated-integral]
math: true
---

## 1. 이중적분에서 반복적분으로 (From Double Integral to Iterated Integral)

**[KR]** 영역 $R$이 직사각형 영역 $[a, b] \times [c, d]$로 정의될 때, 이중적분을 계산하는 가장 효과적인 방법은 **푸비니의 정리(Fubini's Theorem)**를 사용하여 반복적분(Iterated integral)으로 변환하는 것입니다. 이는 3차원 입체의 부피를 구할 때, 마치 식빵을 얇게 썰어 단면적을 먼저 구하고 이를 다시 쌓아 올리는(적분하는) 것과 같은 원리입니다.

**[EN]** When the region $R$ is a rectangular area defined by $[a, b] \times [c, d]$, the most efficient way to compute a double integral is to transform it into an iterated integral using **Fubini's Theorem**. This is mathematically analogous to finding the volume of a 3D solid by first calculating the area of a cross-sectional slice and then integrating these slices across the entire domain.

$$
\iint_R f(x, y) \,dA = \int_a^b \int_c^d f(x, y) \,dy \,dx = \int_c^d \int_a^b f(x, y) \,dx \,dy
$$

---

## 2. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 다항 함수의 반복적분
**[KR]** 직사각형 영역 $[0, 2] \times [0, 1]$ 위에서 함수 $f(x, y) = 2x + y$ 의 반복적분을 수행합니다.
**[EN]** Evaluate the iterated integral of $f(x, y) = 2x + y$ over the rectangular region $[0, 2] \times [0, 1]$.

$$
\int_0^1 \int_0^2 (2x + y) \,dx \,dy
$$

안쪽 $x$에 대해 먼저 적분합니다.
$$
\int_0^2 (2x + y) \,dx = [x^2 + xy]_0^2 = (4 + 2y) - 0 = 4 + 2y
$$

이제 바깥쪽 $y$에 대해 적분합니다.
$$
\int_0^1 (4 + 2y) \,dy = [4y + y^2]_0^1 = (4 + 1) - 0 = 5
$$

### Exercise 2: 복합 함수 형태의 적분
**[KR]** 함수 $f(x, y) = (x + y)^2$ 를 영역 $[0, 1] \times [0, 1]$ 에서 적분합니다.
**[EN]** Integrate the function $f(x, y) = (x + y)^2$ over the region $[0, 1] \times [0, 1]$.

$$
\int_0^1 \int_0^1 (x + y)^2 \,dx \,dy = \int_0^1 \left[ \frac{1}{3}(x + y)^3 \right]_0^1 \,dy
$$

$$
= \frac{1}{3} \int_0^1 ((1 + y)^3 - y^3) \,dy
$$

$$
= \frac{1}{3} \left[ \frac{1}{4}(1 + y)^4 - \frac{1}{4}y^4 \right]_0^1 = \frac{1}{12} (2^4 - 1^4 - (1^4 - 0)) = \frac{1}{12} (16 - 1 - 1) = \frac{14}{12} = \frac{7}{6}
$$

### Exercise 3: 지수함수가 포함된 적분
**[KR]** 영역 $[0, 1] \times [0, 2]$ 에서 $f(x, y) = e^{x + 3y}$ 를 적분합니다.
**[EN]** Evaluate the integral of $f(x, y) = e^{x + 3y}$ over $[0, 1] \times [0, 2]$.

$$
\int_0^2 \int_0^1 e^x \cdot e^{3y} \,dx \,dy = \int_0^2 e^{3y} \left[ e^x \right]_0^1 \,dy
$$

$$
= (e - 1) \int_0^2 e^{3y} \,dy = (e - 1) \left[ \frac{1}{3} e^{3y} \right]_0^2 = \frac{e-1}{3} (e^6 - 1)
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-2 Double Integrals over rectangles-1" src="https://github.com/user-attachments/assets/4094dd9c-5d9d-48c5-92a8-de4338dbba8e" />
    <img width="1264" height="1635" alt="5-2 Double Integrals over rectangles-2" src="https://github.com/user-attachments/assets/5e54e95f-d68d-4d5c-8deb-7e6c9cdabbba" />
    <img width="1264" height="1635" alt="5-2 Double Integrals over rectangles-3" src="https://github.com/user-attachments/assets/52ded4c6-73a3-4317-8ff7-120b14120026" />
    <img width="1264" height="1635" alt="5-2 Double Integrals over rectangles-4" src="https://github.com/user-attachments/assets/5077a6ff-e179-478e-b461-b9ab2cc65697" />
  </div>
</details>
