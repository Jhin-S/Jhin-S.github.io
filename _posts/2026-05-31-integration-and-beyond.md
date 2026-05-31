---
title: "1-4 Integration and Beyond [Optional Calculus BootCamp]"
date: 2026-05-31 21:10:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [calculus, integration, taylor_series, lhopitals_rule, double_integration]
---

## 1. 적분과 미적분학의 기본 정리 (Integration)

**[KR]** 확률 밀도 함수 등을 다루기 위해 필수적인 적분의 기본 개념입니다.

* **부정적분 (Antiderivative / Indefinite Integral):** 도함수가 f(x)인 함수 F(x)를 역도함수(Antiderivative)라고 부르며, F(x) = ∫ f(x) dx 로 표기합니다.
* **미적분학의 기본 정리 (Fundamental Theorem of Calculus):** 함수 f(x)가 연속일 때, 구간 [a, b]에서 곡선 아래의 면적(정적분)은 다음과 같이 계산됩니다.
  ∫(a 부터 b까지) f(x) dx ≡ F(x) &#124; (a 부터 b까지) ≡ F(b) - F(a)
* **주요 부정적분 공식 (Well-known indefinite integrals):** * ∫ xⁿ dx = xⁿ⁺¹ / (n+1) + C  (단, n ≠ -1)
  * ∫ (1/x) dx = ln&#124;x&#124; + C
  * ∫ eˣ dx = eˣ + C
  * ∫ cos x dx = sin x + C
  * ∫ 1/(1+x²) dx = arctan x + C

---

## 2. 적분의 주요 성질 및 기법 (Properties & Techniques)

**[KR]** 정적분과 부정적분을 계산할 때 활용되는 핵심 기법들입니다.

* **정적분의 기본 성질:** 구간이 같으면 ∫(a to a) f(x) dx = 0, 구간이 역전되면 ∫(a to b) f(x) dx = -∫(b to a) f(x) dx 이며, 적분 구간을 나눌 수 있습니다 (∫(a to b) = ∫(a to c) + ∫(c to b)).
* **합의 법칙:** ∫ [f(x) + g(x)] dx = ∫ f(x) dx + ∫ g(x) dx
* **부분적분 (Integration by parts):** ∫ f(x)g'(x) dx = f(x)g(x) - ∫ f'(x)g(x) dx
* **치환적분 (Substitution rule):** u = g(x) 로 치환할 때, ∫ f(g(x))g'(x) dx = ∫ f(u) du

---

## 3. 테일러 급수와 수열의 합 (Taylor Series & Sums)

**[KR]** 복잡한 함수를 다항식의 합으로 근사하거나, 이산적인 값들의 합을 구할 때 사용됩니다.

* **테일러 급수 (Taylor Series):** 임의의 차수 k에 대한 도함수를 f^(k)(x)라 할 때, 점 a 주변에서 f(x)의 전개는 다음과 같습니다.
  f(x) = Σ (k=0 부터 ∞까지) { f^(k)(a) / k! } * (x - a)ᵏ
* **매클로린 급수 (Maclaurin Series):** a=0일 때의 테일러 급수입니다.
  * sin(x) = Σ (k=0 부터 ∞까지) { (-1)ᵏ * x^(2k+1) } / (2k+1)!
  * cos(x) = Σ (k=0 부터 ∞까지) { (-1)ᵏ * x^(2k) } / (2k)!
  * eˣ = Σ (k=0 부터 ∞까지) xᵏ / k!
* **필수 수열의 합 (Miscellaneous Sums):**
  * Σ (k=1 부터 n까지) k = n(n+1) / 2
  * Σ (k=1 부터 n까지) k² = n(n+1)(2n+1) / 6
  * 무한 등비급수: Σ (k=0 부터 ∞까지) pᵏ = 1 / (1-p)  (단, -1 < p < 1)

---

## 4. 로피탈의 정리와 이중 적분 (L'Hospital's Rule & Double Integration)

**[KR]** 극한의 부정형을 해결하는 방법과, 다차원 공간에서의 적분 개념입니다.

* **로피탈의 정리 (L'Hospital's Rule):** 극한에서 0 / 0 이나 ∞ / ∞ 형태의 부정형(Indeterminate ratios)이 발생할 때 사용합니다. lim(x→a) f(x)와 lim(x→a) g(x)가 모두 0 이거나 ∞로 향할 때, 다음이 성립합니다.
  lim(x→a) { f(x) / g(x) } = lim(x→a) { f'(x) / g'(x) }
* **이중 적분 (Double Integration):** 단일 적분이 곡선 아래의 '면적(Area)'을 구하는 것이라면, 이중 적분은 3차원 함수 f(x, y) 아래의 '부피(Volume)'를 나타냅니다. 계산 시 적분의 순서(order of integration)를 바꾸어 계산(dxdy ↔ dydx)해도 동일한 결과를 얻을 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-4 Integration and Beyond  Optional Calculus BootCamp-1" src="https://github.com/user-attachments/assets/0dda35fe-d136-445d-a7ff-e7a3b38915d9" />
    <img width="1264" height="1635" alt="1-4 Integration and Beyond  Optional Calculus BootCamp-2" src="https://github.com/user-attachments/assets/4d492556-213a-497b-a813-54d63ee36641" />
    <img width="1264" height="1635" alt="1-4 Integration and Beyond  Optional Calculus BootCamp-3" src="https://github.com/user-attachments/assets/eea08a70-bab9-4ecc-ba01-b2cf135fb317" />
    <img width="1264" height="1635" alt="1-4 Integration and Beyond  Optional Calculus BootCamp-4" src="https://github.com/user-attachments/assets/6f60dd33-c8f6-4822-9eaf-e328569e835d" />
    <img width="1264" height="1635" alt="1-4 Integration and Beyond  Optional Calculus BootCamp-5" src="https://github.com/user-attachments/assets/d81e11bd-280d-46b3-aa80-a9a98ae4a1be" />
    <img width="1264" height="1635" alt="1-4 Integration and Beyond  Optional Calculus BootCamp-6" src="https://github.com/user-attachments/assets/59c9319f-175f-47a6-81e1-8650abff4d4d" />
  </div>
</details>
