---
title: "5-4 Polar coordinate"
date: 2026-06-06 10:47:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, polar-coordinates, double-integral, area, center-of-mass]
math: true
---

## 1. 극좌표계의 정의 (Definition of Polar Coordinates)

**[KR]** 직교 좌표계 $(x, y)$를 거리 $r$과 각도 $\theta$로 변환하면 복잡한 원형 영역의 적분을 훨씬 쉽게 해결할 수 있습니다. 

**[EN]** Transforming Cartesian coordinates $(x, y)$ into polar coordinates defined by radius $r$ and angle $\theta$ often significantly simplifies integrals over circular or curved domains.

* **변환 공식 (Conversion Formulas):**
  $$x = r \cos \theta, \quad y = r \sin \theta, \quad r^2 = x^2 + y^2$$
* **면적 요소 (Area Element):** 극좌표로 변환할 때 넓이 요소 $dA$는 단순한 $dr\,d\theta$가 아니라, 반지름 $r$을 곱해주어야 합니다.
  $$dA = r \,dr \,d\theta$$

---

## 2. 극좌표에서의 이중적분 (Double Integrals in Polar Coordinates)

**[KR]** 영역 $D$가 극좌표계에서 극사각형(Polar rectangle) 형태, 즉 $a \le r \le b$ 이고 $\alpha \le \theta \le \beta$ 로 정의될 때, 이중적분 공식은 다음과 같습니다.

**[EN]** When the region $D$ is a "polar rectangle" defined by $a \le r \le b$ and $\alpha \le \theta \le \beta$, the double integral formula becomes:

$$
\iint_D f(x, y) \,dA = \int_{\alpha}^{\beta} \int_{a}^{b} f(r \cos \theta, r \sin \theta) \,r \,dr \,d\theta
$$

---

## 3. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 특정 영역에서의 이중적분
**[KR]** $D = \{(r, \theta) \mid 2 \le r \le 4, \pi \le \theta \le 2\pi\}$ 영역에서 $\iint_D (3x + y) \,dA$ 를 계산합니다.
**[EN]** Evaluate $\iint_D (3x + y) \,dA$ over the region $D = \{(r, \theta) \mid 2 \le r \le 4, \pi \le \theta \le 2\pi\}$.

적분 식을 극좌표로 변환합니다 ($x = r \cos \theta, y = r \sin \theta, dA = r \,dr \,d\theta$):

$$
\int_{\pi}^{2\pi} \int_{2}^{4} (3r \cos \theta + r \sin \theta) r \,dr \,d\theta = \int_{\pi}^{2\pi} (3 \cos \theta + \sin \theta) \,d\theta \cdot \int_{2}^{4} r^2 \,dr
$$

$$
= [3 \sin \theta - \cos \theta]_{\pi}^{2\pi} \cdot \left[ \frac{1}{3}r^3 \right]_2^4
$$

$$
= (0 - 1 - (0 - (-1))) \cdot \frac{1}{3}(64 - 8) = (-2) \cdot \frac{56}{3} = -\frac{112}{3}
$$

### Exercise 2: 폐곡선 내부의 면적 구하기
**[KR]** 극좌표계에서 $r = 4 \cos \theta + 5$ 로 주어지는 폐곡선 $C$ 내부의 면적을 구합니다. 넓이는 $\iint_D 1 \,dA$ 입니다.
**[EN]** Find the area of the region enclosed by the closed curve $C$ given in polar coordinates by $r = 4 \cos \theta + 5$.

$$
\text{Area} = \int_0^{2\pi} \int_0^{r(\theta)} r \,dr \,d\theta = \int_0^{2\pi} \frac{1}{2} r^2 \,d\theta = \frac{1}{2} \int_0^{2\pi} (4 \cos \theta + 5)^2 \,d\theta
$$

$$
= \frac{1}{2} \int_0^{2\pi} (16 \cos^2 \theta + 40 \cos \theta + 25) \,d\theta
$$

$\cos^2 \theta = \frac{1 + \cos 2\theta}{2}$ 공식을 사용하여 정리하면:
$$
= \frac{1}{2} \int_0^{2\pi} (8(1 + \cos 2\theta) + 40 \cos \theta + 25) \,d\theta = \frac{1}{2} \int_0^{2\pi} (33 + 8 \cos 2\theta + 40 \cos \theta) \,d\theta
$$

모든 삼각함수 항은 $0$에서 $2\pi$까지 적분하면 $0$이 되므로, 상수항만 남습니다.
$$
\text{Area} = \frac{1}{2} [33\theta]_0^{2\pi} = 33\pi
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-4 Polar coordinate-1" src="https://github.com/user-attachments/assets/9bfb1789-d6d9-4444-9896-d03b71ec392f" />
    <img width="1264" height="1635" alt="5-4 Polar coordinate-2" src="https://github.com/user-attachments/assets/49e35c63-583b-4856-942c-eef00f6c1651" />
    <img width="1264" height="1635" alt="5-4 Polar coordinate-3" src="https://github.com/user-attachments/assets/24edbaa5-b0c9-49e4-a461-04f64ee47be6" />
    <img width="1264" height="1635" alt="5-4 Polar coordinate-4" src="https://github.com/user-attachments/assets/0012bd32-5d25-4d1b-9c61-eb4991c0c2a3" />
    <img width="1264" height="1635" alt="5-4 Polar coordinate-5" src="https://github.com/user-attachments/assets/53a8db60-2968-4933-9d3e-1dc14a7da213" />
    <img width="1264" height="1635" alt="5-4 Polar coordinate-6" src="https://github.com/user-attachments/assets/5b975bd0-14d5-45b0-95b7-b83def809e61" />
  </div>
</details>
