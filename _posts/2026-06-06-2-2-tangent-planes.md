---
title: "2-2 Tangent Planes"
date: 2026-06-06 08:56:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, tangent-plane, linearization, differential]
math: true
---

## 1. 접평면 (Tangent Planes)

**[KR]** 일변수 함수에서 곡선 위의 한 점을 스치듯 지나는 선을 '접선(Tangent line)'이라고 하듯, 이변수 함수가 그리는 3차원 공간의 곡면($z = f(x, y)$) 위에서 특정 점을 스치며 지나가는 평평한 면을 **접평면(Tangent Plane)**이라고 합니다. 점 $(x_0, y_0)$에서의 접평면 방정식은 편미분 계수를 기울기로 사용하여 다음과 같이 정의됩니다.

**[EN]** Just as a tangent line barely touches a curve at a single point in single-variable calculus, a **Tangent Plane** lightly touches a 3D surface $z = f(x, y)$ at a specific point. The equation of the tangent plane at $(x_0, y_0)$ uses partial derivatives as its slopes and is defined as follows:

$$
z - z_0 = f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0)
$$

---

## 2. 선형 근사 (Linearization)

**[KR]** 곡면 위의 한 점 근처를 아주 크게 확대해보면, 곡면은 거의 평면처럼 보이게 됩니다. 즉, 특정 점 주변에서는 복잡한 원래 함수 대신 '접평면의 방정식'을 사용하여 함숫값을 쉽게 어림잡아 계산할 수 있는데, 이를 **선형 근사(Linearization)**라고 부르며 기호로는 $L(x, y)$를 사용합니다.

**[EN]** If you zoom in closely enough on a smooth surface at a specific point, it looks almost completely flat. Therefore, near that point, we can use the equation of the tangent plane to approximate the complex original function. This approximation is called **Linearization**, denoted by $L(x, y)$.

$$
L(x, y) = f(x_0, y_0) + f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0)
$$

* **확장 (Generalization):** $n$개의 변수를 가진 함수로도 쉽게 확장할 수 있으며, 이 경우 모든 변수에 대한 편미분 값들을 더해주면 됩니다.

---

## 3. 전미분 (Differentials)

**[KR]** 입력값 $x$와 $y$가 각각 아주 미세하게 $dx$, $dy$만큼 변했을 때, 출력값 $z$가 얼마나 변하는지($dz$)를 추정하는 공식입니다. 실제 함숫값의 변화량인 $\Delta z$를 구하는 것은 복잡하지만, 전미분 $dz$를 구하면 선형 근사를 통해 오차가 거의 없이 변화량을 추정($\Delta z \approx dz$)할 수 있습니다.

**[EN]** The total differential $dz$ estimates how much the output $z$ changes when the inputs $x$ and $y$ change by infinitesimally small amounts $dx$ and $dy$. While calculating the exact change $\Delta z$ is often complicated, the differential provides a highly accurate linear approximation ($\Delta z \approx dz$).

$$
dz = df = f_x(x, y)dx + f_y(x, y)dy
$$

---

## 4. 예제 풀이 (Practice Exercises)

### Exercise 1: 수평 접평면 찾기 (Horizontal Tangent Plane)
**[KR]** 곡면 $z = x^2 - 2xy + 3y^2 + 8x + 5$의 접평면이 완벽한 '수평'이 되는 점 $P(a, b)$를 찾습니다. 수평 평면은 $x$방향 기울기와 $y$방향 기울기가 모두 0이어야 하므로, 두 편미분 값이 동시에 0이 되는 지점을 찾으면 됩니다.
**[EN]** Find the point $P(a, b)$ where the tangent plane to the surface $z = x^2 - 2xy + 3y^2 + 8x + 5$ is perfectly horizontal. A horizontal plane implies that the slopes in both the $x$ and $y$ directions are zero.

$$
f_x = 2x - 2y + 8 = 0
$$

$$
f_y = -2x + 6y = 0
$$

위 연립방정식을 풀면 $4y + 8 = 0$ 이 되어 $y = -2$ 이고, 대입하면 $x = -6$ 이 됩니다. 
이때의 $z$값을 구하기 위해 원래 함수에 대입하면:
$f(-6, -2) = 36 - 24 + 12 - 48 + 5 = -19$
**정답:** 수평 접평면의 방정식은 $z = -19$ 입니다.

### Exercise 2: 특정 점에서의 선형 근사식 구하기 (Finding Linearization)
**[KR]** 함수 $f(x, y) = y \cdot e^{xy}$ 에 대하여 점 $(0, 5)$에서의 선형 근사 $L(x, y)$를 구합니다. 연쇄 법칙(Chain rule)과 곱의 미분법을 주의해서 사용해야 합니다.
**[EN]** Determine the linearization $L(x, y)$ of the function $f(x, y) = y \cdot e^{xy}$ at the point $(0, 5)$. We must carefully apply the chain rule and product rule.

* $f_x = y^2 e^{xy} \implies f_x(0, 5) = 25 \cdot 1 = 25$
* $f_y = e^{xy} + xye^{xy} \implies f_y(0, 5) = 1 + 0 = 1$
* 원래 함숫값: $f(0, 5) = 5 \cdot 1 = 5$

선형 근사 공식에 대입하면 다음과 같습니다.

$$
L(x, y) = 5 + 25(x - 0) + 1(y - 5) = 25x + y
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-2 Tangent Planes-1" src="https://github.com/user-attachments/assets/8298995b-632a-42de-be93-248fb2b70d69" />
    <img width="1264" height="1635" alt="2-2 Tangent Planes-2" src="https://github.com/user-attachments/assets/719a2b88-ed16-4296-92af-2e64db53ca2b" />
    <img width="1264" height="1635" alt="2-2 Tangent Planes-3" src="https://github.com/user-attachments/assets/f6a3b1f3-95ed-4008-8275-63f166e704e6" />
    <img width="1264" height="1635" alt="2-2 Tangent Planes-4" src="https://github.com/user-attachments/assets/e38c5ad3-509d-4059-a00b-1e4b2dd18578" />
    <img width="1264" height="1635" alt="2-2 Tangent Planes-5" src="https://github.com/user-attachments/assets/b0432770-cd3d-442a-856b-4957e6694265" />
    <img width="1264" height="1635" alt="2-2 Tangent Planes-6" src="https://github.com/user-attachments/assets/1720b147-80be-415f-8d25-9161486d0e86" />
    <img width="1264" height="1635" alt="2-2 Tangent Planes-7" src="https://github.com/user-attachments/assets/ddd7bb34-3990-4a72-8622-bdf59e079cb2" />
    <img width="1264" height="1635" alt="2-2 Tangent Planes-8" src="https://github.com/user-attachments/assets/3f16ac21-bdec-4aa7-b636-fa35f5414629" />
  </div>
</details>
