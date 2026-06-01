---
title: "2-6 Counting Techniques: Permutations"
date: 2026-06-01 22:15:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, counting_techniques, permutations, factorial]
---

## 1. 순열의 정의 (Definition of Permutations)

**[KR]** 순열(Permutation)이란 n개의 기호(Symbols)를 특정한 순서대로 배열하는 것을 의미합니다.

* **예제 1:** 숫자 1, 2, 3을 배열하는 방법의 수는 몇 가지일까요? 정답은 6가지입니다 (123, 132, 213, 231, 312, 321).
* **예제 2:** 1부터 n까지의 숫자를 배열하는 방법의 수는 어떻게 될까요? 첫 번째 자리에 올 수 있는 수 n가지, 두 번째는 (n-1)가지와 같은 식으로 계속 곱해 나갑니다. 즉, n * (n-1) * (n-2) * ... * 2 * 1 = **n! (팩토리얼)** 가지가 됩니다.

---

## 2. n개 중 r개를 선택하는 순열 (Taken r-at-a-time)

**[KR]** 서로 다른 n개의 기호 중에서 (각각 최대 한 번만 사용하여) r개를 뽑아 나열하는 경우의 수를 의미합니다.

* **공식:** P(n, r) = n! / (n - r)!
* **참고사항:** 0! = 1 이며, n개 중 n개를 모두 뽑아 나열하는 P(n, n) = n! 입니다.
* **예제:** a, b, c, d 4개의 문자 중 2개를 뽑아 나열하는 방법은? P(4, 2) = 4! / 2! = **12가지**입니다. (ab, ac, ad, ba, bc, bd, ca, cb, cd, da, db, dc)

---

## 3. 순열의 응용 예제: 야구 타순 (Application Examples)

**[KR]** 야구팀의 타순을 정하는 상황을 통해 순열을 응용해 봅니다.

* **문제 1:** 9명의 선수 중 1번부터 4번 타자까지 4명을 배치하는 경우의 수는?
  * n = 9, r = 4 이므로 P(9, 4) = 9! / (9 - 4)! = **3024가지**입니다.
* **문제 2:** 위의 3024가지 경우 중 '스미스(Smith)' 선수가 1번 타자로 나서는 경우는 몇 가지일까요?
  * **방법 1 (직접 계산):** 1번 타자는 스미스로 고정하고, 남은 8명 중 3명을 2, 3, 4번 타자로 배치합니다. 즉, P(8, 3) = 8! / (8 - 3)! = **336가지**입니다.
  * **방법 2 (확률적 접근):** 9명의 선수가 각각 1번 타자가 될 확률은 모두 동일하므로, 전체 경우의 수에서 9를 나눕니다. 3024 / 9 = **336가지**입니다.

---

## 4. 중복을 허용하는 경우 (With or Without Repetitions)

**[KR]** 숫자 1부터 9까지를 사용하여 6자리의 번호판을 만드는 경우를 생각해 봅시다.

* **(a) 중복을 허용하지 않는 경우:** 한 번 쓴 숫자는 다시 쓸 수 없습니다. (예: 123456)
  * P(9, 6) = 9! / 3! = **60480가지**
* **(b) 중복을 허용하는 경우:** 어떤 숫자든 자유롭게 여러 번 쓸 수 있습니다. (예: 193354)
  * 각 자리마다 9가지 숫자가 올 수 있으므로 9^6 = **531441가지**
* **(c) 중복된 숫자가 하나라도 포함된 번호판의 개수:**
  * (전체 경우의 수) - (중복이 없는 경우의 수) = 531441 - 60480 = **470961가지**

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; flex-direction: column; align-items: center; gap: 15px; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-6 Counting Techniques_ Permutations-1" src="https://github.com/user-attachments/assets/bf1eaacd-7218-4fc8-aa7e-94791690af81" />
    <img width="1264" height="1635" alt="2-6 Counting Techniques_ Permutations-2" src="https://github.com/user-attachments/assets/96240827-1de2-4ded-ad2d-c34866e88f59" />
    <img width="1264" height="1635" alt="2-6 Counting Techniques_ Permutations-3" src="https://github.com/user-attachments/assets/3395402a-4002-4598-94bc-66566793958f" />
    <img width="1264" height="1635" alt="2-6 Counting Techniques_ Permutations-4" src="https://github.com/user-attachments/assets/090af3a8-d131-48fc-af39-866ee4042212" />
  </div>
</details>
