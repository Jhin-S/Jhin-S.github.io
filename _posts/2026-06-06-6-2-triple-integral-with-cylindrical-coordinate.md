---
title: "6-2 Triple Integral With Cylindrical Coordinate"
date: 2026-06-06 13:20:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, triple-integral, cylindrical-coordinates, moment-of-inertia]
math: true
---

## 1. 원기둥 좌표계의 정의 (Definition of Cylindrical Coordinates)

**[KR]** 직교 좌표계의 $(x, y, z)$ 중 $x$와 $y$를 극좌표계의 방식인 $r$과 $\theta$로 바꾸고, 높이 $z$는 그대로 유지하는 3차원 좌표계를 **원기둥 좌표계(Cylindrical Coordinates)**라고 부릅니다. 이 좌표계는 적분 영역이 원기둥 형태이거나 $z$축을 중심으로 대칭성을 가질 때 삼중적분을 획기적으로 단순하게 만들어 줍니다.

**[EN]** The Cylindrical Coordinate system is a 3D extension of polar coordinates, where $x$ and $y$ are replaced by $r$ and $\theta$, while the vertical height $z$ remains unchanged. It is extremely useful for evaluating triple integrals when the solid region has an axis of symmetry, such as a cylinder or a cone.

* **변환 공식 (Conversion Formulas):**
  $$x = r \cos \theta, \quad y = r \sin \theta, \quad z = z$$
  (참고: $x^2 + y^2 = r^2$)
* **부피 요소 (Volume Element, $dV$):** 2차원 극좌표계에서 넓이 요소가 $r \,dr \,d\theta$였던 것처럼, 여기에 높이 $dz$가 추가되어 부피 요소는 $r$이 곱해진 형태가 됩니다.
  $$dV = r \,dz \,dr \,d\theta$$

---

## 2. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 포물면 아래의 삼중적분 (Integral under a Paraboloid)
**[KR]** 입체 영역 $G$가 $z = 0$ 평면 위, 그리고 포물면 $z = 16 - x^2 - y^2$ 아래에 놓여있을 때, 이 영역에서 함수 $z$의 삼중적분 $\iiint_G z \,dV$ 를 계산합니다.
**[EN]** Evaluate the triple integral $\iiint_G z \,dV$, where $G$ is the solid region bounded below by the $xy$-plane and above by the paraboloid $z = 16 - x^2 - y^2$.

원기둥 좌표계로 변환하면 $z = 16 - r^2$가 됩니다. 적분 구간은 $0 \le \theta \le 2\pi$, $0 \le r \le 4$, $0 \le z \le 16 - r^2$ 입니다.

$$
\iiint_G z \,dV = \int_0^{2\pi} \int_0^4 \int_0^{16-r^2} z \cdot r \,dz \,dr \,d\theta
$$

1. **$z$에 대한 적분:**
   $$\left[ \frac{1}{2} z^2 r \right]_0^{16-r^2} = \frac{1}{2} (16 - r^2)^2 r$$

2. **$r$과 $\theta$에 대한 적분 (치환적분 활용):**
   $t = 16 - r^2$ 로 치환하면 $dt = -2r \,dr$ 이 됩니다.
   $$\int_0^{2\pi} \int_{16}^0 \frac{1}{2} t^2 \left( -\frac{1}{2} \right) dt \,d\theta = \frac{1}{4} \int_0^{2\pi} \left[ \frac{1}{3}t^3 \right]_0^{16} d\theta$$
   
$$
= \frac{1}{12} \cdot 4096 \cdot 2\pi = \frac{2048}{3}\pi
$$

---

### Exercise 2: 두 평면 사이의 부피 (Volume between Two Planes)
**[KR]** 원기둥 $x^2 + y^2 \le 1$ 내부이면서, 두 평면 $y + z = 3$ 과 $y + z = 5$ 사이에 갇힌 입체의 부피 $V$를 구합니다.
**[EN]** Find the volume $V$ of the solid enclosed by the cylinder $x^2 + y^2 \le 1$ and bounded between the planes $y + z = 3$ and $y + z = 5$.

부피는 피적분함수를 $1$로 두고 적분하여 구합니다. 원기둥 내부이므로 $r$은 $0$부터 $1$까지, $z$는 $3-y$ 부터 $5-y$ 까지입니다.

$$
V = \int_0^{2\pi} \int_0^1 \int_{3-r\sin\theta}^{5-r\sin\theta} 1 \cdot r \,dz \,dr \,d\theta
$$

1. **$z$에 대한 적분:** 위끝에서 아래끝을 빼면 간단한 상수가 됩니다.
   $$(5 - r\sin\theta) - (3 - r\sin\theta) = 2 \implies 2r$$

2. **$r$과 $\theta$에 대한 적분:**
   $$\int_0^{2\pi} \int_0^1 2r \,dr \,d\theta = \int_0^{2\pi} \left[ r^2 \right]_0^1 d\theta = \int_0^{2\pi} 1 \,d\theta = 2\pi$$

---

### Exercise 3: 관통된 구의 관성 모멘트 (Moment of Inertia of a Drilled Sphere)
**[KR]** 반지름이 3인 꽉 찬 구의 중심을 관통하도록 반지름 2인 원기둥 모양의 구멍을 뚫어냈습니다. 남은 입체(밀도 $\rho=1$)의 $z$축을 기준으로 한 관성 모멘트 $I_z$를 계산합니다.
**[EN]** A vertical cylinder of radius 2 is drilled through the center of a solid ball of radius 3. Assuming constant density $\rho=1$, compute the moment of inertia $I_z$ of the remaining object around the $z$-axis.

관성 모멘트 공식은 $I_z = \iiint r^2 \rho \,dV$ 입니다. 남은 입체의 $r$ 범위는 $2$부터 $3$까지이고, $z$ 범위는 구면 방정식 $z^2 = 9 - r^2$ 에 의해 결정됩니다.

$$
I_z = \int_0^{2\pi} \int_2^3 \int_{-\sqrt{9-r^2}}^{\sqrt{9-r^2}} r^2 \cdot r \,dz \,dr \,d\theta
$$

1. **$z$에 대한 적분:**
   $$\int_{-\sqrt{9-r^2}}^{\sqrt{9-r^2}} r^3 \,dz = 2r^3\sqrt{9-r^2}$$

2. **$r$에 대한 적분 (치환적분):** $t = 9 - r^2$ 로 치환하면 $dt = -2r \,dr$ 이고 $r^2 = 9 - t$ 입니다.
   $$\int_5^0 2(9-t)\sqrt{t} \left( -\frac{1}{2} \right) dt = \int_0^5 (9t^{1/2} - t^{3/2}) \,dt$$
   
   $$= \left[ 6t^{3/2} - \frac{2}{5}t^{5/2} \right]_0^5 = 30\sqrt{5} - \frac{2}{5}(25\sqrt{5}) = 20\sqrt{5}$$

3. **$\theta$에 대한 적분:**
   $$\int_0^{2\pi} 20\sqrt{5} \,d\theta = 40\sqrt{5}\pi$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-2 Triple Integral With Cylindrical Coordinate-1" src="https://github.com/user-attachments/assets/fffee5a5-d408-4f14-abc5-ef0764af62d4" />
    <img width="1264" height="1635" alt="6-2 Triple Integral With Cylindrical Coordinate-2" src="https://github.com/user-attachments/assets/88fc5d2c-f948-469b-8934-b148fa44480c" />
    <img width="1264" height="1635" alt="6-2 Triple Integral With Cylindrical Coordinate-3" src="https://github.com/user-attachments/assets/ec7399f6-2611-464d-9096-5b4d1aa4e486" />
    <img width="1264" height="1635" alt="6-2 Triple Integral With Cylindrical Coordinate-4" src="https://github.com/user-attachments/assets/2516148e-ae0d-4549-a13c-e4abaa459248" />
    <img width="1264" height="1635" alt="6-2 Triple Integral With Cylindrical Coordinate-5" src="https://github.com/user-attachments/assets/5adbf6da-e8e9-4be7-9182-35d91e64a9be" />
    <img width="1264" height="1635" alt="6-2 Triple Integral With Cylindrical Coordinate-6" src="https://github.com/user-attachments/assets/f15a41b1-a042-4c57-9c5e-f7c0af640ff5" />
    <img width="1264" height="1635" alt="6-2 Triple Integral With Cylindrical Coordinate-7" src="https://github.com/user-attachments/assets/d4044022-c6fb-44bc-a43c-5a9be439b0cc" />
  </div>
</details>
