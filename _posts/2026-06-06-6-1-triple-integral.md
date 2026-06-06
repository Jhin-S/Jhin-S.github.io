---
title: "6-1 Triple Integral"
date: 2026-06-06 12:45:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, triple-integral, volume, tetrahedron]
math: true
---

## 1. 삼중적분의 개념과 Z-단순 영역 (Triple Integrals & Z-Simple Regions)

**[KR]** 이중적분이 2차원 평면 영역을 바탕으로 부피를 계산했다면, 삼중적분(Triple Integral)은 3차원 입체 영역 $E$ 전체에 걸쳐 함수 $f(x, y, z)$를 적분하는 방법입니다. 밀도 함수를 삼중적분하여 3차원 물체의 전체 질량을 구하는 등 물리학과 공학에서 매우 중요하게 사용됩니다.

**[EN]** While double integrals compute volume over a 2D planar region, a Triple Integral integrates a function $f(x, y, z)$ over a 3D solid region $E$. This is widely used in physics and engineering, for example, to find the total mass of a 3D object given its density function.

### Type I 영역 (Z-Simple Region)
**[KR]** 3차원 입체 영역 $E$가 $xy$-평면 상의 특정 영역 $D$ 위에 존재하고, $z$축 방향으로는 두 곡면 $u_1(x, y)$와 $u_2(x, y)$ 사이에 갇혀 있는 형태를 의미합니다. 이 경우 $z$에 대해 먼저 적분한 뒤, 나머지 변수들로 이중적분을 수행합니다.

**[EN]** A solid region $E$ is considered Type I (or z-simple) if it lies above a 2D region $D$ in the $xy$-plane and is bounded vertically between two surfaces $u_1(x, y)$ and $u_2(x, y)$. In this case, we integrate with respect to $z$ first, followed by a double integral over $D$.

$$
\iiint_E f(x, y, z) \,dV = \iint_D \left( \int_{u_1(x, y)}^{u_2(x, y)} f(x, y, z) \,dz \right) \,dA
$$

---

## 2. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 직육면체 영역에서의 삼중적분 (Rectangular Box)
**[KR]** 3차원 영역 $E = \{(x, y, z) \mid -1 \le x \le 2, 0 \le y \le 3, 0 \le z \le 1\}$ 위에서 함수 $12xy^2z^3$ 의 삼중적분 값을 계산해 봅시다. 적분 구간이 모두 상수이므로 순서대로 차근차근 적분하면 됩니다.
**[EN]** Evaluate the triple integral of $12xy^2z^3$ over the rectangular box $E$. Since all boundaries are constant limits, we can integrate iteratively in any order.

$$
\int_{-1}^{2} \int_{0}^{3} \int_{0}^{1} 12xy^2z^3 \,dz \,dy \,dx
$$

1. **$z$에 대한 적분:**
   $$\int_{0}^{1} 12xy^2z^3 \,dz = \left[ 3xy^2z^4 \right]_0^1 = 3xy^2$$

2. **$y$에 대한 적분:**
   $$\int_{0}^{3} 3xy^2 \,dy = \left[ xy^3 \right]_0^3 = 27x$$

3. **$x$에 대한 적분:**
   $$\int_{-1}^{2} 27x \,dx = \left[ \frac{27}{2}x^2 \right]_{-1}^2 = \frac{27}{2}(4) - \frac{27}{2}(1) = 54 - \frac{27}{2} = \frac{81}{2}$$

---

### Exercise 2: 구면과 직육면체가 결합된 복합 영역 (Complex Region)
**[KR]** $E = \{(x, y, z) \mid \vert x \vert \le 1, \vert y \vert \le 1, x^2 + y^2 + z^2 \le 16, z \ge 0\}$ 영역에서 $\sqrt{16 - x^2 - y^2}$ 를 삼중적분합니다. $z$의 범위는 $0$부터 구면의 윗부분인 $\sqrt{16 - x^2 - y^2}$ 까지입니다.
**[EN]** Evaluate the integral of $\sqrt{16 - x^2 - y^2}$ over the region $E$. The bounds for $z$ are from $0$ to the upper hemisphere $\sqrt{16 - x^2 - y^2}$.

$$
\int_{-1}^{1} \int_{-1}^{1} \int_{0}^{\sqrt{16-x^2-y^2}} \sqrt{16-x^2-y^2} \,dz \,dy \,dx
$$

1. **$z$에 대한 적분:** 피적분함수에는 $z$가 없으므로 상수로 취급합니다.
   $$\left[ z \sqrt{16-x^2-y^2} \right]_0^{\sqrt{16-x^2-y^2}} = 16 - x^2 - y^2$$

2. **$y$에 대한 적분:**
   $$\int_{-1}^{1} (16 - x^2 - y^2) \,dy = \left[ 16y - x^2y - \frac{1}{3}y^3 \right]_{-1}^1 = 2 \left( 16 - x^2 - \frac{1}{3} \right) = 32 - 2x^2 - \frac{2}{3}$$

3. **$x$에 대한 적분:**
   $$\int_{-1}^{1} \left( \frac{94}{3} - 2x^2 \right) \,dx = \left[ \frac{94}{3}x - \frac{2}{3}x^3 \right]_{-1}^1 = 2 \left( \frac{94}{3} - \frac{2}{3} \right) = \frac{184}{3}$$

---

### Exercise 3: 사면체 영역에서의 적분 (Tetrahedron)
**[KR]** 좌표평면들과 평면 $4x + y + z = 4$ 로 둘러싸인 제 1팔분면의 사면체 영역 $R$에서 함수 $6z$를 삼중적분합니다.
**[EN]** Integrate $6z$ over the tetrahedron $R$ bounded by the coordinate planes ($x \ge 0, y \ge 0, z \ge 0$) and the plane $4x + y + z \le 4$.

적분 구간을 설정합니다: $x \in [0, 1]$, $y \in [0, -4x + 4]$, $z \in [0, -4x - y + 4]$.

$$
\int_{0}^{1} \int_{0}^{-4x+4} \int_{0}^{-4x-y+4} 6z \,dz \,dy \,dx
$$

1. **$z$에 대한 적분:**
   $$\int_{0}^{-4x-y+4} 6z \,dz = \left[ 3z^2 \right]_0^{-4x-y+4} = 3(-4x - y + 4)^2 = 3(4x + y - 4)^2$$

2. **$y$에 대한 적분:** $(4x - 4)$를 하나의 상수로 보고 적분합니다.
   $$\int_{0}^{-4x+4} 3(y + 4x - 4)^2 \,dy = \left[ (y + 4x - 4)^3 \right]_0^{-4x+4} = 0 - (4x - 4)^3 = -64(x - 1)^3$$

3. **$x$에 대한 적분:**
   $$\int_{0}^{1} -64(x - 1)^3 \,dx = -64 \left[ \frac{1}{4}(x - 1)^4 \right]_0^1 = -16 (0 - 1) = 16$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-1 Triple Integral-1" src="https://github.com/user-attachments/assets/d89d674f-4f1d-4dc2-a919-54fed90d2072" />
    <img width="1264" height="1635" alt="6-1 Triple Integral-2" src="https://github.com/user-attachments/assets/3a281e27-8791-4be9-9e00-1c0366a12979" />
    <img width="1264" height="1635" alt="6-1 Triple Integral-3" src="https://github.com/user-attachments/assets/4d9a025c-9a8c-4553-91e7-503904a499bf" />
    <img width="1264" height="1635" alt="6-1 Triple Integral-4" src="https://github.com/user-attachments/assets/9c1b926d-69d5-453f-89e3-4ae830b8975b" />
    <img width="1264" height="1635" alt="6-1 Triple Integral-5" src="https://github.com/user-attachments/assets/07fd2ae1-d278-4791-b88b-424e359269a1" />
    <img width="1264" height="1635" alt="6-1 Triple Integral-6" src="https://github.com/user-attachments/assets/d2b89d8a-c387-441c-a996-4f64fd3a11b9" />
    <img width="1264" height="1635" alt="6-1 Triple Integral-7" src="https://github.com/user-attachments/assets/b9453790-34e3-48d4-99af-4430bc270fae" />
    <img width="1264" height="1635" alt="6-1 Triple Integral-8" src="https://github.com/user-attachments/assets/6f5d0659-3d0f-4822-9af5-598b8d6a1e55" />
  </div>
</details>
