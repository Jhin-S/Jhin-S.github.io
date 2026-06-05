---
title: "혼자 만들고 풀어본 확률 경우의 수 팁과 문제들"
date: 2026-06-05 16:56:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, combinations, permutations, problem-solving]
math: true
---
## 이번에는 Probability and Statistics I을 수강하며 헷갈리는 개념을 정리하고 문제를 제미나이를 통해 만들고 풀어보았습니다.

## 1. 확률과 경우의 수 문제의 기본 (Basics of Probability & Combinatorics)

**[KR]** 복잡한 경우의 수를 계산할 때 가장 유용한 접근법은 동일한 객체라도 일단 서로 다른 것으로 취급하여 나열한 뒤, 중복되는 순서를 팩토리얼($!$)로 나누어 보정하는 것입니다.
* **순열(Permutations, $P$):** 객체들의 순서를 고려하여 일렬로 배열하는 방법의 수입니다.
* **조합(Combinations, $C$):** 순열에서 순서의 구분을 없애기 위해 팩토리얼로 나눈 값입니다. 단순히 객체를 선택하기만 할 때 사용합니다.
* **중복 순열(Permutations with Replacement, $\Pi$):** 선택한 객체를 다시 선택할 수 있는 상태에서 순서를 고려해 배열합니다 (거듭제곱 활용).
* **중복 조합(Combinations with Replacement, $H$):** 순서를 고려하지 않고 중복 선택을 허용합니다. 칸막이 모델(Stars and Bars)을 도입하여, 선택할 개수를 별($\star$)로 두고 항목을 구분하는 선($\vert$)을 나열하는 방식으로 쉽게 계산할 수 있습니다.

**[EN]** A highly effective strategy in combinatorics is to initially treat identical objects as distinct, arrange them, and then correct for the overcounting by dividing by the factorial of the number of identical objects.
* **Permutations ($P$):** The number of ways to arrange objects in a specific sequence.
* **Combinations ($C$):** Selecting objects without regard to order. It is calculated by dividing permutations by factorials to eliminate the sequence order.
* **With Replacement ($\Pi, H$):** Using exponential powers for permutations, and applying the 'Stars and Bars' visual logic for combinations to easily divide categories using dividers.

---

## 2. 개수 제한이 포함된 계산 (Calculations with Constraints)

**[KR]** 특정 요소에 최대 선택 개수 제한이 걸려있다면 문제의 유형에 따라 풀이 전략을 다르게 설정해야 합니다.
* **제한이 있는 중복 조합 ($H$):** 전체 제약 없는 조합의 수에서, 특정 요소가 제한치를 초과하여 뽑히는 경우의 수를 빼주는 여집합(Complement) 전략이 효율적입니다.
* **제한이 있는 중복 순열 ($\Pi$):** 여집합보다는 제한이 걸린 요소가 0번 쓰였을 때, 1번 쓰였을 때 등 구체적인 사용 횟수별로 케이스를 나누어 계산한 뒤 합산하는 것이 훨씬 직관적이고 빠릅니다.

**[EN]** When specific elements have maximum selection limits, your strategy should depend on the type of problem.
* For **Combinations with replacement ($H$)**, it is highly efficient to use the complement approach: calculate the total unconstrained combinations and subtract the cases where the limit is strictly exceeded.
* For **Permutations with replacement ($\Pi$)**, rather than using the complement, it is faster to break the problem into distinct cases based on the exact number of times the restricted item is used.

---

## 3. 경우의 수를 지배하는 핵심 관점 (Core Perspectives for Problem Solving)

**[KR]** 복잡하게 꼬인 조건들을 해결하기 위한 대표적인 시각들입니다.
1.  **묶음 처리 (Grouping):** "반드시 이웃해야 한다"는 조건이 붙으면 해당 요소들을 하나의 커다란 덩어리로 묶어서 계산합니다.
2.  **여집합 활용 (Complementary Set):** "적어도 하나는 포함해야 한다"와 같은 조건은 전체 경우의 수에서 반대되는 상황을 빼서 구합니다.
3.  **빈공간 채우기 (Insertion/Gap Filling):** "절대 이웃하면 안 된다"는 조건이 있다면, 제약이 없는 나머지 요소들을 먼저 나열한 후 그 사이사이의 빈 공간에 제한된 요소들을 끼워 넣습니다.
4.  **칸막이 관점 (Stones and Bars):** 대상을 여러 구역으로 나눌 때 사용하는 중복 조합의 시각입니다.

**[EN]** These are standard perspectives to resolve complex combinatorial conditions:
1.  **Grouping:** Treat items that "must be adjacent" as a single unified block.
2.  **Complement:** For conditions like "at least one," calculate the total possibilities and subtract the scenario where none exist.
3.  **Insertion:** For items that "must NOT be adjacent," first arrange the unrestricted items, then insert the restricted items into the gaps between them.
4.  **Stones and Bars:** The standard perspective for dividing indistinguishable items into distinct groups.

---

## 4. 실전 자작 문제 풀이 (Custom Practice Problems)

### 🔴 문제 1: 완벽한 장전의 예술
**[KR]** 빨간 철갑탄 3발, 파란 마법탄 2발, 초록 명중탄 2발(총 7발, 같은 색은 구분 불가)을 일렬로 장전합니다. 파란 마법탄 2발은 서로 이웃하면 폭발합니다. 안전하게 장전하는 경우의 수는?
**[EN]** Arrange 3 Red, 2 Blue, and 2 Green bullets (7 total, identical by color). Blue bullets will explode if they are adjacent. Find the number of safe arrangements.

* 제약이 없는 빨간/초록 총알 먼저 배열 (Arrange safe bullets): $\frac{5!}{3!2!} = 10$
* 생성된 6개의 틈새에 파란 총알 2개 삽입 (Insert 2 Blues into 6 gaps): $\binom{6}{2} = 15$
* **Total:** $10 \times 15 = 150$

### 🔒 문제 2: SCP 재단 제 19기지 격리 작전
**[KR]** 8개의 방에 SCP-999 3개체(구분 불가), SCP-049 3개체(구분 불가), 서로 다른 MTF 요원 2명을 배치합니다. MTF 요원끼리는 반드시 붙어 있어야 하고, SCP-049 3개체는 서로 떨어져 있어야 합니다.
**[EN]** Arrange 3 identical SCP-999s, 3 identical SCP-049s, and 2 distinct MTF agents in 8 rooms. The MTF agents must be adjacent, while the SCP-049s must not be adjacent to each other.

* MTF 요원을 한 덩어리로 묶어 내부 순서 고려($2!$) 후 SCP-999와 배열 (Group MTFs and arrange with SCP-999s): $\frac{4!}{3!} \times 2! = 8$
* 생성된 5개의 빈 공간에 SCP-049 삽입 (Insert SCP-049s into 5 gaps): $\binom{5}{3} = 10$
* **Total:** $8 \times 10 = 80$

### 🎇 문제 3: 피날레 무대 연출
**[KR]** 9개의 자리에 연꽃 함정 4개(구분 불가), 마법공학 수류탄 3개(구분 불가), 서로 다른 챔피언 가렌과 럭스를 배치합니다. 챔피언 둘은 무조건 이웃해야 하며, 수류탄 3개는 서로 이웃하면 안 됩니다.
**[EN]** Arrange 4 identical Lotus traps, 3 identical Hextech grenades, and distinct champions Garen and Lux in 9 seats. Garen and Lux must sit together, but the 3 grenades must be separated.

* 챔피언들을 묶어 내부 순서 고려($2!$) 후 연꽃 함정과 배열 (Group Champions and arrange with Lotus): $\frac{5!}{4!} \times 2! = 10$
* 생성된 6개의 틈새 중 3곳에 수류탄 삽입 (Insert 3 grenades into 6 gaps): $\binom{6}{3} = 20$
* **Total:** $10 \times 20 = 200$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="혼자 만들고 풀어본 확률 경우의 수 팁과 문제들-1" src="https://github.com/user-attachments/assets/eb1cdb00-5163-4d71-94e6-e5ba19219754" />
    <img width="1264" height="1635" alt="혼자 만들고 풀어본 확률 경우의 수 팁과 문제들-2" src="https://github.com/user-attachments/assets/98e7702c-f891-49b5-8847-d8b8fe13c64e" />
    <img width="1264" height="1635" alt="혼자 만들고 풀어본 확률 경우의 수 팁과 문제들-3" src="https://github.com/user-attachments/assets/9d937ec6-261c-4f59-84a3-e08ec48203b2" />
    <img width="1264" height="1635" alt="혼자 만들고 풀어본 확률 경우의 수 팁과 문제들-4" src="https://github.com/user-attachments/assets/a3e46ded-0bf6-4ecb-9966-6ca7c7582ff4" />
    <img width="1264" height="1635" alt="혼자 만들고 풀어본 확률 경우의 수 팁과 문제들-5" src="https://github.com/user-attachments/assets/1c48aed8-74da-4dd7-b327-ae48076b6421" />
    <img width="1264" height="1635" alt="혼자 만들고 풀어본 확률 경우의 수 팁과 문제들-6" src="https://github.com/user-attachments/assets/749695c0-f464-4462-aded-159555e0e491" />
  </div>
</details>
