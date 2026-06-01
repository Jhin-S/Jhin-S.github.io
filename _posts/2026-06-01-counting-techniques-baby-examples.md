---
title: "2-5 Counting Techniques: Baby Examples"
date: 2026-06-01 23:45:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, counting_techniques, addition_rule, multiplication_rule]
---

## 1. 카운팅 기법 개요 (Counting Techniques)

**[KR]** 앞으로의 몇 가지 레슨에서는 단순 표본 공간(SSS)에서 특정 사건의 확률을 효율적으로 계산하기 위해, 사건에 포함된 원소의 개수를 세는(Counting) 방법들을 다룹니다. 이를 위해 다음의 유용한 규칙과 기법들을 순차적으로 살펴볼 예정입니다.

1. 직관적인 기초 예제들 (Intuitive baby examples - 이번 포스팅)
2. 순열 (Permutations)
3. 조합 (Combinations)

---

## 2. 직관적인 기초 예제 1: 합의 법칙 (Addition Rule)

**[KR]** 선택지 A를 고르는 방법이 n_A 가지 있고, 선택지 B를 고르는 방법이 n_B 가지 있다고 가정해 봅시다. 만약 **둘 중 오직 하나의 선택지만** 고를 수 있다면, 전체 선택 가능한 경우의 수는 **n_A + n_B** 가지가 됩니다.

* **스타벅스 예제:** 스타벅스에 가서 머핀(블루베리 또는 오트밀 -> 2가지) 혹은 베이글(참깨, 플레인, 소금, 갈릭 -> 4가지) 중 **하나만** 골라서 먹는다고 가정해 봅시다. 둘 다 먹을 수는 없습니다.
* **결과:** 머핀을 고르는 2가지 방법과 베이글을 고르는 4가지 방법을 더하여, 총 **2 + 4 = 6가지**의 선택지가 존재합니다.

---

## 3. 직관적인 기초 예제 2: 곱의 법칙 (Multiplication Rule)

**[KR]** 두 가지 이상의 단계나 사건이 **연달아(또는 동시에)** 일어날 때 적용되는 규칙입니다.

* **경로 찾기 예제:** 도시 A에서 도시 B로 가는 방법이 3가지(도보, 자동차, 버스)이고, 도시 B에서 도시 C로 가는 방법이 4가지(자동차, 버스, 기차, 비행기)라고 가정해 봅시다.
* **결과:** 도시 A에서 출발하여 도시 B를 거쳐 도시 C로 가는 전체 경로의 수는 각 단계의 경우의 수를 곱하여 **3 × 4 = 12가지**(itineraries)가 됩니다.

* **주사위 2개 굴리기 예제:** 공정한 주사위 2개를 굴릴 때, 나올 수 있는 전체 결과의 수는 몇 개일까요? (단, 첫 번째 주사위가 3, 두 번째가 2인 것과 첫 번째가 2, 두 번째가 3인 것은 서로 다른 결과로 취급합니다.)
* **결과:** 첫 번째 주사위에서 나올 수 있는 경우 6가지, 두 번째 주사위에서 나올 수 있는 경우 6가지를 곱하여 **6 × 6 = 36가지**의 결과가 나옵니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="100%" style="max-width: 600px; border-radius: 6px;" alt="2-5 Counting Techniques Baby Examples 1" src="이미지_링크를_여기에_넣어주세요_1" />
  </div>
</details>
