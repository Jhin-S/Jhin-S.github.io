---
title: "2-15 Partitions and the Law of Total Probability"
date: 2026-06-05 16:28:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, partition, law-of-total-probability]
math: true
---

## 1. 표본 공간의 분할 (Partition of a Sample Space)

**[KR]** 표본 공간(Sample Space)을 서로 겹치지 않으면서(서로소), 전체를 완벽하게 포괄하는 부분집합들로 쪼개는 것을 '분할(Partition)'이라고 합니다. 어떤 실험을 수행했을 때, 분할된 사건들($A_1, A_2, \dots, A_n$) 중 정확히 단 하나만 발생하게 됩니다.
사건 $A_1, A_2, \dots, A_n$이 표본 공간 $S$의 분할이 되려면 다음 세 가지 조건을 만족해야 합니다.

**[EN]** A partition of a sample space splits it into disjoint, yet all-encompassing subsets. When an experiment is performed, exactly one of the $A_i$'s occurs. The events $A_1, A_2, \dots, A_n$ form a partition of sample space $S$ if:

1. $A_1, A_2, \dots, A_n$ are disjoint (서로소, 교집합이 없음).
2. $\bigcup_{i=1}^{n} A_i = S$ (모두 합치면 전체 표본 공간이 됨).
3. $P(A_i) > 0$ for all $i$ (모든 사건의 발생 확률은 0보다 큼).

* **Examples:**
  * 사건 $A$와 그 여사건 $\bar{A}$ (Events $A$ and $\bar{A}$ form a partition)
  * 알파벳의 '모음(Vowels)'과 '자음(Consonants)'

---

## 2. 전체 확률의 법칙 (The Law of Total Probability)

**[KR]** $A_1, A_2, \dots, A_n$이 표본 공간 $S$의 분할이라고 가정해 봅시다. 이때 임의의 사건 $B$가 발생할 확률은, 사건 $B$를 분할된 조각($A_i$)들과의 교집합으로 각각 쪼갠 뒤 모두 더하여 구할 수 있습니다. 여기에 조건부 확률의 공식을 적용하면 **전체 확률의 법칙**이 도출됩니다.

**[EN]** Suppose $A_1, A_2, \dots, A_n$ form a partition of $S$, and $B$ is some arbitrary event. We can decompose $B$ into pieces of the $A_i$'s. Using the conditional probability formula, we derive the **Law of Total Probability**.

먼저, 사건 $B$를 분할된 영역들로 나눕니다 (Decompose $B$):

$$
B = \bigcup_{i=1}^{n} (A_i \cap B)
$$

$A_i$들이 서로소이므로, 교집합들의 확률을 단순히 더할 수 있습니다:

$$
P(B) = \sum_{i=1}^{n} P(A_i \cap B)
$$

조건부 확률 $P(A_i \cap B) = P(A_i)P(B \vert A_i)$를 대입합니다:

$$
P(B) = \sum_{i=1}^{n} P(A_i)P(B \vert A_i)
$$

---

## 3. 예제 풀이 (Example)

**[KR]** 조지아 공대(GT) 학생 10명과 조지아 대학교(UGA) 학생 20명이 시험을 봅니다. GT 학생이 시험에 통과할 확률은 95%이고, UGA 학생이 통과할 확률은 50%입니다. 무작위로 학생 한 명을 뽑았을 때, 그 학생이 시험에 통과할 확률은 얼마일까요?

**[EN]** Suppose we have 10 Georgia Tech (GT) students and 20 University of Georgia (UGA) students taking a test. GT students have a 95% chance of passing, but UGA students have a 50% chance. Pick a student at random, and determine the probability that he/she passes.

* $P(\text{GT}) = \frac{10}{30} = \frac{1}{3}$
* $P(\text{UGA}) = \frac{20}{30} = \frac{2}{3}$
* $P(\text{passes} \vert \text{GT}) = 0.95$
* $P(\text{passes} \vert \text{UGA}) = 0.50$

전체 확률의 법칙(Law of Total Probability)에 의해:

$$
P(\text{passes}) = P(\text{GT})P(\text{passes} \vert \text{GT}) + P(\text{UGA})P(\text{passes} \vert \text{UGA})
$$

$$
P(\text{passes}) = \left(\frac{1}{3}\right)(0.95) + \left(\frac{2}{3}\right)(0.5) = 0.65
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-15 Partitions and the Law of Total Probability-1" src="https://github.com/user-attachments/assets/d5ef0fc6-f127-4132-b019-e0a837c5b5a2" />
    <img width="1264" height="1635" alt="2-15 Partitions and the Law of Total Probability-2" src="https://github.com/user-attachments/assets/715c7f05-bdb0-4a61-a7e9-000b3d5b98e2" />
  </div>
</details>
