---
title: "1-2 The Joy of Sets [Optional Calculus BootCamp]"
date: 2026-05-31 20:59:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, sets, discrete_math, cardinality, demorgans_law, calculus_bootcamp]
---

## 1. 집합의 기본 개념 및 기호 (Basic Definitions & Notations)

**[KR]** 집합(Set)은 객체들의 모임이며, 집합에 속한 객체들을 원소(Elements)라고 부릅니다. 확률론을 이해하기 위한 가장 기초적인 언어입니다.

* **표기법 (Notation):** 집합은 대문자(A, B, C)로 표기하고, 집합 안의 원소는 소문자(a, b, c)로 표기합니다.
* **소속 관계 (Membership):** 특정 원소가 집합에 속할 때는 ∈ 기호를(예: x ∈ A), 속하지 않을 때는 ∉ 기호를 사용합니다.
* **전체 집합과 공집합:** 다루는 모든 대상을 포함하는 전체 집합(Universal set)은 U로, 아무런 원소가 없는 공집합(Empty set)은 ∅으로 표기합니다.

---

## 2. 집합의 관계와 연산 (Set Operations & Relationships)

**[KR]** 여러 집합 간의 관계를 나타내고 새로운 집합을 만들어내는 주요 연산입니다.

* **부분집합 (Subset) 및 상등:** 집합 A의 모든 원소가 집합 B의 원소일 때, A는 B의 부분집합(A ⊆ B)이 됩니다. 만약 A ⊆ B 이면서 동시에 B ⊆ A 라면 두 집합은 같습니다(A = B).
* **여집합 (Complement):** 전체 집합 U에 속하면서 A에는 속하지 않는 원소들의 집합을 Aᶜ로 표기합니다. *(※ 웹 환경 호환성을 위해 윗줄 대신 ᶜ 기호로 표기했습니다)*
* **교집합(Intersection)과 합집합(Union):** 두 집합에 공통으로 속하는 원소의 집합은 A ∩ B이며, 적어도 한 집합에 속하는 원소의 집합은 A ∪ B입니다. 만약 공통 원소가 하나도 없다면(A ∩ B = ∅), 두 집합은 서로소(Disjoint 혹은 Mutually exclusive)라고 부릅니다.
* **차집합 (Difference):** A에는 속하지만 B에는 속하지 않는 집합으로, A - B ≡ A ∩ Bᶜ 로 정의됩니다.
* **대칭 차집합 (Symmetric Difference / XOR):** 두 집합 중 어느 한 쪽에만 속하는 원소들의 집합으로, A Δ B ≡ (A - B) ∪ (B - A) = (A ∪ B) - (A ∩ B) 로 정의됩니다.

---

## 3. 집합의 크기 (Cardinality)

**[KR]** 집합 A의 크기(Cardinality)는 &#124;A&#124;로 표기하며, 집합에 포함된 원소의 개수를 의미합니다.

* **유한 집합 (Finite Set):** 원소의 개수가 유한한 집합입니다 (&#124;A&#124; < ∞). 예를 들어 A = {3, 4}일 때 &#124;A&#124; = 2 입니다.
* **가산 무한 집합 (Countably Infinite):** 자연수 집합처럼 하나씩 셀 수 있게 무한한 경우로, 이 크기를 알레프 제로(ℵ₀)로 표기합니다. (예: B = {1, 2, 3, ...})
* **비가산 무한 집합 (Uncountably Infinite):** 실수 구간 [0, 1] 내의 모든 수처럼 셀 수 없이 촘촘하게 무한한 경우로, 이 크기를 알레프 원(ℵ₁)으로 표기합니다.

---

## 4. 집합의 연산 법칙 (Laws of Operation)

**[KR]** 확률론의 수식 전개에서 매우 빈번하게 사용되는 핵심 수학 법칙들입니다.

1. **여집합의 법칙 (Complement Laws):** A ∪ Aᶜ = U, A ∩ Aᶜ = ∅, (Aᶜ)ᶜ = A
2. **교환 법칙 (Commutative):** A ∪ B = B ∪ A, A ∩ B = B ∩ A
3. **결합 법칙 (Associative):** A ∪ (B ∪ C) = (A ∪ B) ∪ C, A ∩ (B ∩ C) = (A ∩ B) ∩ C
4. **분배 법칙 (Distributive):** A ∪ (B ∩ C) = (A ∪ B) ∩ (A ∪ C), A ∩ (B ∪ C) = (A ∩ B) ∪ (A ∩ C)
5. **드 모르간의 법칙 (DeMorgan's Laws):** (A ∪ B)ᶜ = Aᶜ ∩ Bᶜ, (A ∩ B)ᶜ = Aᶜ ∪ Bᶜ

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-2 The Joy of Sets 1" src="https://github.com/user-attachments/assets/1b375125-0ff3-481d-a7ed-c0b45d6b633c" />
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-2 The Joy of Sets 2" src="https://github.com/user-attachments/assets/603307a2-12bd-4b74-ac64-c1229584d890" />
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-2 The Joy of Sets 3" src="https://github.com/user-attachments/assets/0a70eeb2-9d7e-4e22-a4c6-42f05a85fb81" />
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="1-2 The Joy of Sets 4" src="https://github.com/user-attachments/assets/94086242-6742-443c-a212-b33f6feb7c98" />
  </div>
</details>
