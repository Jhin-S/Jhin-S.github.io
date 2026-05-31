---
title: "1-3 derivatives [Optional Calculus BootCamp]"
date: 2026-05-31 21:00:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [calculus, derivatives, continuous_function, optimization, chain_rule]
---

## 1. 함수, 연속성 그리고 역함수 (Functions, Continuity, and Inverses)

**[KR]** 확률론과 통계를 다루기 위해 필요한 기초 미적분학(Calculus) 개념입니다.

* **함수 (Function):** 함수 f(x)는 특정 정의역(Domain, X)의 x 값들을 특정 공역(Range, Y)으로 매핑(Mapping)하는 역할을 하며, 표기법으로는 f: X → Y로 나타냅니다. (예: f(x) = x²는 실수 전체 ℝ을 음이 아닌 실수 구간으로 매핑합니다.)
* **연속성 (Continuous Function):** 함수 f(x)가 임의의 x₀에서 lim(x→x₀) f(x) = f(x₀)를 만족할 때, 즉 극한값과 함숫값이 일치할 때 연속이라고 합니다. 반면 내림 함수인 f(x) = ⌊x⌋와 같은 경우는 정수 지점에서 불연속적인 '점프(Jump)'가 발생합니다.
* **역함수 (Inverse Function):** f: X → Y의 역방향 매핑 g: Y → X를 의미하며, f(g(y)) = y 이고 g(f(x)) = x를 만족해야 합니다. 기호로는 f⁻¹로 표기하며, 함수가 순증가 혹은 순감소할 때 유용합니다. (예: f(x) = x³ 이면 f⁻¹(y) = y^(1/3), h(x) = eˣ 이면 h⁻¹(y) = ln(y))

---

## 2. 미분의 정의와 기본 공식 (Definition & Basic Derivatives)

**[KR]** 함수 f(x)가 연속이라면 미분 가능할(Differentiable) 수 있습니다. 미분은 함수의 '기울기(Slope)'를 의미합니다.

**미분의 정의 (Limit Definition):**
d/dx f(x) ≡ f'(x) ≡ lim(h→0) {f(x+h) - f(x)} / h

**잘 알려진 기본 미분 공식 (Well-known derivatives):**
* [xⁿ]' = n · x^(n-1)
* [eˣ]' = eˣ
* [sin x]' = cos x
* [cos x]' = -sin x
* [ln x]' = 1 / x
* [arctan x]' = 1 / (1 + x²)

---

## 3. 미분의 주요 연산 법칙 (Properties of Derivatives)

**[KR]** 복잡한 함수를 미분할 때 사용되는 핵심 정리(Theorem)들입니다.

* **선형성:** [a·f(x) + b]' = a·f'(x)
* **합의 미분:** [f(x) + g(x)]' = f'(x) + g'(x)
* **곱의 미분 (Product Rule):** [f(x)g(x)]' = f'(x)g(x) + f(x)g'(x)
* **몫의 미분 (Quotient Rule):** [f(x) / g(x)]' = {f'(x)g(x) - f(x)g'(x)} / {g(x)}²
* **연쇄 법칙 (Chain Rule):** [f(g(x))]' = f'(g(x)) · g'(x)

---

## 4. 이계도함수와 최적화 (Second Derivative & Optimization)

**[KR]** 이계도함수(Second derivative)는 f''(x) ≡ d/dx f'(x)로 정의되며, '기울기의 기울기'를 의미합니다. 물리학적 관점에서 f(x)를 '위치(Position)'라고 한다면, f'(x)는 '속도(Velocity)', f''(x)는 '가속도(Acceleration)'로 간주할 수 있습니다.

**최대/최소 찾기 (Min/Max):**
함수 f(x)의 최솟값이나 최댓값은 함수의 기울기가 0이 되는 임계점(Critical point)인 **f'(x) = 0** 인 지점(x₀)에서 발생합니다. (단, 관심 구간의 양 끝점(endpoints)도 함께 확인해야 합니다.)

* f''(x₀) < 0 이면, 극댓값 (Maximum)을 가집니다.
* f''(x₀) > 0 이면, 극솟값 (Minimum)을 가집니다.
* f''(x₀) = 0 이면, 변곡점 (Point of inflection)이 됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-3 derivatives 1" src="https://github.com/user-attachments/assets/e742332b-0943-4bb6-b8e2-ccbd060dc5a9" />
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-3 derivatives 2" src="https://github.com/user-attachments/assets/d685d5b4-5e64-4433-b62f-0d1b6129d4f5" />
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-3 derivatives 3" src="https://github.com/user-attachments/assets/ef4fa11b-5d5c-4edb-ab44-a04aa16cba18" />
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-3 derivatives 4" src="https://github.com/user-attachments/assets/007537c0-920a-4053-8f77-b2b5fe4c4c8f" />
  </div>
</details>
