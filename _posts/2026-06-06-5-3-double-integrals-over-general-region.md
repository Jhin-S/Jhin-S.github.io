---
title: "5-3 Double Integrals Over General Region"
date: 2026-06-06 10:45:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, double-integral, general-region, type-i-region, type-ii-region]
math: true
---

## 1. 일반 영역에서의 이중적분 (Double Integrals over General Regions)

**[KR]** 적분 영역 $D$가 직사각형이 아닐 때는 적분 구간을 상수가 아닌, 다른 변수에 대한 함수로 표현해야 합니다. 가장 대표적인 두 가지 영역 분류는 다음과 같습니다.

**[EN]** When the integration region $D$ is not a rectangle, we must define the integration limits as functions of the other variable. The two most common classifications are:

### Type I 영역 (y-simple region)
**[KR]** $x$는 상숫값 사이($a \le x \le b$)에서 움직이고, $y$는 두 곡선 사이($g_1(x) \le y \le g_2(x)$)에서 움직이는 영역입니다.
**[EN]** A region where $x$ varies between constant values ($a \le x \le b$), while $y$ varies between two functions ($g_1(x) \le y \le g_2(x)$).

$$
\iint_D f(x, y) \,dA = \int_a^b \int_{g_1(x)}^{g_2(x)} f(x, y) \,dy \,dx
$$

---

## 2. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 포물선으로 둘러싸인 영역의 적분
**[KR]** 직선 $y = 6x$ 와 포물선 $y = 2x(6 - x)$ 로 둘러싸인 유한한 영역 $D$에서 $\iint_D x \,dA$ 를 계산합니다.
**[EN]** Calculate $\iint_D x \,dA$ over the finite region $D$ enclosed by the line $y = 6x$ and the parabola $y = 2x(6 - x)$.

먼저 두 그래프의 교점을 찾습니다.
$6x = 12x - 2x^2 \implies 2x^2 - 6x = 0 \implies 2x(x - 3) = 0$
교점은 $x = 0$ 과 $x = 3$ 입니다. 구간 $[0, 3]$ 에서 포물선이 직선 위에 있으므로 적분 식은 다음과 같습니다.

$$
\int_0^3 \int_{6x}^{12x - 2x^2} x \,dy \,dx = \int_0^3 x [y]_{6x}^{12x - 2x^2} \,dx
$$

$$
= \int_0^3 x(12x - 2x^2 - 6x) \,dx = \int_0^3 (6x^2 - 2x^3) \,dx
$$

$$
= \left[ 2x^3 - \frac{1}{2}x^4 \right]_0^3 = 54 - 40.5 = 13.5 = \frac{27}{2}
$$

### Exercise 2: 포물선으로 둘러싸인 영역의 넓이
**[KR]** 두 포물선 $y = \frac{x^2}{2}$ 와 $x = \frac{y^2}{2}$ 로 둘러싸인 영역 $D$의 넓이 $A$를 구합니다.
**[EN]** Find the area $A$ of the region $D$ enclosed by the parabolas $y = \frac{x^2}{2}$ and $x = \frac{y^2}{2}$.

$y = \frac{x^2}{2}$ 이면 $x = \frac{(x^2/2)^2}{2} = \frac{x^4}{8}$ 가 되어 $x^4 - 8x = 0$ 으로부터 $x = 0, 2$를 얻습니다.
넓이는 $\iint_D 1 \,dA$ 이며, $y$ 구간은 $\frac{x^2}{2} \le y \le \sqrt{2x}$ 입니다.

$$
A = \int_0^2 \int_{x^2/2}^{\sqrt{2x}} 1 \,dy \,dx = \int_0^2 (\sqrt{2}x^{1/2} - \frac{1}{2}x^2) \,dx
$$

$$
= \left[ \sqrt{2} \cdot \frac{2}{3}x^{3/2} - \frac{1}{6}x^3 \right]_0^2 = \left( \sqrt{2} \cdot \frac{2}{3} \cdot 2\sqrt{2} \right) - \frac{8}{6} = \frac{8}{3} - \frac{4}{3} = \frac{4}{3}
$$

### Exercise 3: 평균값 계산 (Average Value)
**[KR]** 제 1사분면에서 좌표축과 포물선 $y = 1 - x^2$ 로 둘러싸인 영역 $D$에서 함수 $f(x, y) = 5x \cos(5y)$ 의 평균값을 구합니다. (평균값 공식: $\bar{f} = \frac{1}{\text{Area}(D)} \iint_D f(x, y) \,dA$)
**[EN]** Find the average value of $f(x, y) = 5x \cos(5y)$ over the region $D$ in the first quadrant bounded by the axes and $y = 1 - x^2$.

1. **영역의 넓이:** $\int_0^1 (1 - x^2) \,dx = [x - \frac{1}{3}x^3]_0^1 = \frac{2}{3}$
2. **이중적분:**
   $$\int_0^1 \int_0^{1-x^2} 5x \cos(5y) \,dy \,dx = \int_0^1 x [\sin(5y)]_0^{1-x^2} \,dx = \int_0^1 x \sin(5 - 5x^2) \,dx$$
   $t = 5 - 5x^2$ 로 치환하면 $dt = -10x \,dx$ 이므로 $-\frac{1}{10} \int_5^0 \sin(t) \,dt = \frac{1}{10} [-\cos(t)]_0^5 = \frac{1}{10} (1 - \cos 5)$
3. **평균값:** $\bar{f} = \frac{1}{2/3} \cdot \frac{1}{10} (1 - \cos 5) = \frac{3}{20} (1 - \cos 5)$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-3 Double Integrals Over General Region-1" src="https://github.com/user-attachments/assets/500b6df2-9e24-4dad-9f28-7d34e58a21d1" />
    <img width="1264" height="1635" alt="5-3 Double Integrals Over General Region-2" src="https://github.com/user-attachments/assets/2776385b-9741-4c5d-a448-bf62780a859a" />
    <img width="1264" height="1635" alt="5-3 Double Integrals Over General Region-3" src="https://github.com/user-attachments/assets/5e2773f6-fb49-4d2e-b30a-030befa3dcd6" />
    <img width="1264" height="1635" alt="5-3 Double Integrals Over General Region-4" src="https://github.com/user-attachments/assets/2d88ddd6-94ce-494f-add0-0b7b755e9670" />
  </div>
</details>
