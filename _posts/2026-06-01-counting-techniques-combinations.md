---
title: "2-7 Counting Techniques: Combinations"
date: 2026-06-01 23:55:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, combinations, counting_techniques, binomial_theorem]
---

## 1. 조합의 정의와 순열과의 차이 (Combinations vs Permutations)

**[KR]** 조합(Combination)은 순서를 고려하지 않고 n개의 객체 중 r개를 선택하는 방법의 수를 의미합니다. 이는 n개의 객체로 이루어진 집합에서 정확히 r개의 원소를 가지는 부분집합의 개수를 구하는 것과 같습니다.

* **예제:** {1, 2, 3}에서 정확히 2개의 원소를 포함하는 부분집합은 {1, 2}, {1, 3}, {2, 3} 으로 총 3개입니다 (순서는 중요하지 않습니다).
* **기호:** nCr 또는 C(n, r) (읽을 때는 "n choose r")로 표기하며, 이를 이항 계수(Binomial coefficients)라고도 부릅니다.
* **순열과의 차이:**
  * **조합:** 순서를 따지지 않습니다. 즉, {a, b, c}와 {b, a, c}는 같은 것으로 취급합니다.
  * **순열:** 순서를 따집니다. 즉, (a, b, c)와 (b, a, c)는 서로 다른 것으로 취급합니다.

---

## 2. 조합의 공식과 직관적인 성질 (Formula & Intuitive Results)

**[KR]** 순열을 선택하는 과정은, 먼저 조합을 선택한 뒤 그 원소들을 순서대로 나열하는 것과 같습니다. 따라서 순열 공식 n! / (n-r)! 은 조합의 수에 나열하는 경우의 수 r! 을 곱한 것과 같으므로, 여기서 조합의 공식이 자연스럽게 도출됩니다.

* **조합 공식:** C(n, r) = n! / { r! * (n-r)! }
* **직관적인 성질들:** 다음의 결과들은 직관적으로 쉽게 이해할 수 있습니다.
  * C(n, r) = C(n, n-r)
  * C(n, 0) = C(n, n) = 1
  * C(n, 1) = C(n, n-1) = n

---

## 3. 이항 정리와 활용 (Binomial Theorem & Corollary)

**[KR]** 이항 정리(Binomial Theorem)는 파스칼의 삼각형(Pascal's Triangle)과 밀접하게 연관된 매우 중요한 수학적 결과입니다.

* **이항 정리:** (x + y)ⁿ = Σ (k=0 부터 n까지) C(n, k) * xᵏ * yⁿ⁻ᵏ
* **따름정리 (Corollary):** Σ (k=0 부터 n까지) C(n, k) = 2ⁿ
  * **증명:** 이항 정리 수식에서 x=1, y=1을 대입하면 2ⁿ = (1 + 1)ⁿ = Σ C(n, k) * 1ᵏ * 1ⁿ⁻ᵏ 가 되어 간단히 증명됩니다.

---

## 4. 조합의 응용 예제 (Application Examples)

**[KR]** 농구팀 스타팅 멤버를 뽑거나 사물을 배치하는 상황을 통해 조합의 계산법을 연습해 봅니다.

* **예제 1 (농구팀 선발):** 12명의 선수가 있는 NBA 팀에서 코치가 스타팅 멤버 5명을 고르는 방법의 수는? (순서 무관)
  * C(12, 5) = 12! / (5! * 7!) = **792가지**
* **예제 2 (특정 선수 고정 포함):** 위 예제에서 '스미스(Smith)'라는 선수가 반드시 스타팅 라인업에 포함되어야 한다면 몇 가지 경우가 가능할까요?
  * 스미스는 이미 한 자리를 자동으로 차지했다고 생각하면 됩니다. 남은 11명의 선수 중에서 4자리만 마저 채우면 되므로 C(11, 4) = 11! / (4! * 7!) = **330가지**입니다.
* **예제 3 (신발 배치):** 7개의 빨간 신발과 5개의 파란 신발이 있을 때, 이를 12개의 일렬로 된 빈 슬롯에 배치하는 방법의 수는?
  * 12개의 슬롯 중 빨간 신발이 들어갈 7자리를 고르는 것과 같으므로 **C(12, 7)** 입니다. 반대로 파란 신발이 들어갈 5자리를 고르는 관점인 C(12, 5)로 접근해도 정답은 완전히 동일합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-7 Counting Techniques_ Combinations-1" src="https://github.com/user-attachments/assets/2a8ba6b3-dd1b-490a-913f-2aa38420b1e8" />
    <img width="1264" height="1635" alt="2-7 Counting Techniques_ Combinations-2" src="https://github.com/user-attachments/assets/51b9a0cd-a423-41ce-b0a3-80f834805fe7" />
    <img width="1264" height="1635" alt="2-7 Counting Techniques_ Combinations-3" src="https://github.com/user-attachments/assets/7ac58799-8606-49f7-9cc2-4e74f3aaceca" />
    <img width="1264" height="1635" alt="2-7 Counting Techniques_ Combinations-4" src="https://github.com/user-attachments/assets/51e03865-6db0-4ce3-a3fc-cb0d19e1f4d9" />
  </div>
</details>
