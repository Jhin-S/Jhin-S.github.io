---
title: "6-3 Triple Integrals With Spherical Coordinates"
date: 2026-06-06 14:00:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, triple-integral, spherical-coordinates, volume, moment-of-inertia]
math: true
---

## 1. 구면 좌표계의 수학적 정의 (Spherical Coordinates System)

**[KR]** 구면 좌표계(Spherical Coordinates)는 3차원 공간의 점을 세 가지 요소로 표현하는 좌표계입니다. 원점에서의 거리 $\rho$, $z$축 양의 방향과 이루는 각도 $\phi$, 그리고 $xy$-평면으로의 정사영이 $x$축 양의 방향과 이루는 각도 $\theta$를 사용합니다. 이 좌표계는 구(Sphere)나 원뿔(Cone)과 관련된 삼중적분 계산을 획기적으로 단순화시켜 줍니다.

**[EN]** The spherical coordinate system represents a point in 3D space using three parameters: the radial distance from the origin $\rho$, the polar angle from the positive $z$-axis $\phi$, and the azimuthal angle in the $xy$-plane $\theta$. This system drastically simplifies triple integrals involving spheres and cones.

* **직교 좌표계와의 변환 (Coordinate Conversion):**
  $$x = \rho \sin \phi \cos \theta$$
  $$y = \rho \sin \phi \sin \theta$$
  $$z = \rho \cos \phi$$
  (이때 $r = \rho \sin \phi$ 이며, $x^2 + y^2 + z^2 = \rho^2$ 가 성립합니다.)

* **부피 요소의 변환 (Volume Element):**
  구면 좌표계로 적분할 때는 반드시 자코비안(Jacobian) 행렬식의 결과인 $\rho^2 \sin \phi$ 를 곱해주어야 합니다.
  $$dV = \rho^2 \sin \phi \,d\rho \,d\phi \,d\theta$$

---

## 2. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 구 내부에서의 삼중적분
**[KR]** 중심이 원점이고 반지름이 $R$인 구 $G$의 내부 영역에서 함수 $z^2$ 의 삼중적분을 계산해 봅시다.
**[EN]** Evaluate the triple integral of $z^2$ over the solid sphere $G$ centered at the origin with radius $R$.

구 전체 영역이므로 적분 구간은 $\theta \in [0, 2\pi]$, $\phi \in [0, \pi]$, $\rho \in [0, R]$ 입니다. 피적분 함수 $z^2$는 $(\rho \cos \phi)^2$ 로 변환됩니다.

$$
\iiint_G z^2 \,dV = \int_0^{2\pi} \int_0^\pi \int_0^R (\rho^2 \cos^2 \phi) \cdot (\rho^2 \sin \phi) \,d\rho \,d\phi \,d\theta
$$

$$
= \int_0^{2\pi} \,d\theta \cdot \int_0^\pi \cos^2 \phi \sin \phi \,d\phi \cdot \int_0^R \rho^4 \,d\rho
$$

* $\rho$ 적분: $\left[ \frac{1}{5}\rho^5 \right]_0^R = \frac{R^5}{5}$
* $\theta$ 적분: $2\pi$
* $\phi$ 적분 (치환적분 $t = \cos \phi, dt = -\sin \phi \,d\phi$): $\int_1^{-1} -t^2 \,dt = \int_{-1}^1 t^2 \,dt = \frac{2}{3}$

세 결과를 모두 곱하면 최종 정답은 **$\frac{4\pi R^5}{15}$** 가 됩니다.

---

### Exercise 2: 구와 원뿔이 겹치는 영역
**[KR]** 구 $x^2 + y^2 + z^2 \le R^2$ 의 내부이면서, 동시에 원뿔 $z \ge \sqrt{x^2 + y^2}$ 의 안쪽에 위치하는 영역 $G$에서 함수 $z$를 삼중적분합니다.
**[EN]** Evaluate the integral of $z$ over the region $G$ bounded by the sphere $x^2 + y^2 + z^2 \le R^2$ and the cone $z \ge \sqrt{x^2 + y^2}$.

원뿔의 방정식을 구면 좌표계로 변환하면 $\rho \cos \phi \ge \rho \sin \phi$ 가 되어 $\cos \phi \ge \sin \phi$ 를 만족해야 합니다. 따라서 $\phi$ 의 범위는 $0 \le \phi \le \frac{\pi}{4}$ 로 제한됩니다.

$$
\iiint_G z \,dV = \int_0^{2\pi} \int_0^{\pi/4} \int_0^R (\rho \cos \phi) \cdot (\rho^2 \sin \phi) \,d\rho \,d\phi \,d\theta
$$

각 변수에 대해 독립적으로 적분을 수행하여 모두 곱해주면 최종 결과는 **$\frac{\pi R^4}{8}$** 로 도출됩니다.

---

### Exercise 3: 평행이동된 구와 관성 모멘트
**[KR]** 밀도가 $\delta = 4$ 로 일정한 입체가 있습니다. 이 입체는 평행이동된 구 $x^2 + y^2 + (z - 2)^2 \le 4$ 내부이자 원뿔 $z \ge \sqrt{x^2 + y^2}$ 내부에 위치합니다. 이 입체의 $z$축 기준 관성 모멘트 $I_z$를 구해봅시다.
**[EN]** Consider a solid with a constant density of 4, enclosed by the shifted sphere $x^2 + y^2 + (z - 2)^2 \le 4$ and the cone $z \ge \sqrt{x^2 + y^2}$. Find its moment of inertia $I_z$ about the $z$-axis.

1. **구의 방정식 변환:** 전개하면 $x^2 + y^2 + z^2 \le 4z$ 가 됩니다. 이를 구면 좌표계로 바꾸면 $\rho^2 \le 4\rho \cos \phi$ 이므로 $\rho$ 의 상한선은 $4\cos \phi$ 입니다.
2. **적분 식 세우기:** 관성 모멘트 $I_z = \iiint r^2 \delta \,dV$ 이며, 여기서 $r^2 = (\rho \sin \phi)^2$ 입니다.

$$
I_z = \int_0^{2\pi} \int_0^{\pi/4} \int_0^{4\cos \phi} 4 (\rho^2 \sin^2 \phi) \cdot (\rho^2 \sin \phi) \,d\rho \,d\phi \,d\theta
$$

* $\rho$ 적분: $\int_0^{4\cos \phi} 4\rho^4 \sin^3 \phi \,d\rho = \frac{4}{5} (4\cos \phi)^5 \sin^3 \phi$
* 위 결과를 바탕으로 삼각함수 치환적분을 꼼꼼하게 수행하면, 최종적으로 **$\frac{1024\pi}{15}$** 라는 결괏값을 얻을 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-3 Triple Integrals With Spherical Coordinates-1" src="https://github.com/user-attachments/assets/76861c20-2040-4910-9443-88892574932e" />
    <img width="1264" height="1635" alt="6-3 Triple Integrals With Spherical Coordinates-2" src="https://github.com/user-attachments/assets/6ce62e16-f1f1-4785-819e-47ffb823bd84" />
    <img width="1264" height="1635" alt="6-3 Triple Integrals With Spherical Coordinates-3" src="https://github.com/user-attachments/assets/0705f709-a0fc-4be2-8fe0-2b9544e47882" />
    <img width="1264" height="1635" alt="6-3 Triple Integrals With Spherical Coordinates-4" src="https://github.com/user-attachments/assets/58bd6952-b28c-4603-825f-4c2c8f410090" />
    <img width="1264" height="1635" alt="6-3 Triple Integrals With Spherical Coordinates-5" src="https://github.com/user-attachments/assets/632bcbca-7b27-4492-93a6-44d888ba0be9" />
    <img width="1264" height="1635" alt="6-3 Triple Integrals With Spherical Coordinates-6" src="https://github.com/user-attachments/assets/ede3e482-fbe2-4ad7-827e-5764f4c8f5d5" />
  </div>
</details>
