---
title: "2-11 The Envelope Problem"
date: 2026-06-05 14:56:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, envelope-problem, inclusion-exclusion, limit]
math: true
---

## 1. 포함-배제의 원리 (General Principle of Inclusion-Exclusion)

**[KR]** 여러 사건의 합집합 확률을 구할 때 사용하는 일반화된 원리입니다. 각 사건의 확률을 더하고, 두 사건의 교집합을 빼고, 세 사건의 교집합을 다시 더하는 과정을 반복하여 중복 계산을 보정합니다.

**[EN]** This is a generalized principle used to find the probability of the union of multiple events. You add the probabilities of individual events, subtract the intersections of pairs, add the intersections of triples, and so on, alternating signs to correct for overcounting.

$$
P(A_1 \cup A_2 \dots \cup A_n) = \sum_{i=1}^{n} P(A_i) - \sum_{i < j} P(A_i \cap A_j) + \dots + (-1)^{n-1} P(A_1 \cap \dots \cap A_n)
$$

---

## 2. 봉투 문제 (The Envelope Problem)

**[KR]** $n$명의 사람이 자신의 이름이 적힌 봉투 $n$개를 무작위로 섞어서 나누어 받았습니다. 이때, **적어도 한 명은 자신의 제대로 된 봉투를 받을 확률**을 구하는 문제입니다. 
사건 $A_i$를 '$i$번째 사람이 제대로 된 봉투를 받는 사건'이라고 정의하면, 우리가 구하고자 하는 것은 $P(A_1 \cup A_2 \cup \dots \cup A_n)$가 됩니다.

**[EN]** A group of $n$ people receives $n$ envelopes with their names on them, but someone has completely mixed them up. We want to find the probability that **at least one person will receive the proper envelope**. 
Let $A_i$ be the event that "Person $i$ receives the correct envelope." We are looking for $P(A_1 \cup A_2 \cup \dots \cup A_n)$.

### 확률 계산의 전개 (Expanding the Probability)

모든 $P(A_i)$의 확률은 동일하고, 모든 두 사건의 교집합 $P(A_i \cap A_j)$의 확률도 모두 동일합니다. 따라서 포함-배제의 원리와 조합(Combinations)을 사용하여 식을 묶을 수 있습니다.

$$
P(\bigcup_{i=1}^{n} A_i) = n P(A_1) - \binom{n}{2} P(A_1 \cap A_2) + \binom{n}{3} P(A_1 \cap A_2 \cap A_3) \dots + (-1)^{n-1} P(A_1 \cap \dots \cap A_n)
$$

* **참고:** 이항계수 $\binom{n}{2}$가 붙는 이유는 전체 $n$명 중 무순서로 교집합을 이룰 2명을 고르는 경우의 수이기 때문입니다.

---

## 3. 확률의 곱셈 정리와 최종 결과 (Multiplication Rule & Final Result)

**[KR]** 1번 사람이 제대로 된 봉투를 받을 확률 $P(A_1) = \frac{1}{n}$ 입니다. 
1번 사람이 제대로 받은 상태에서 2번 사람도 제대로 받을 확률(조건부 확률)은 $P(A_2 | A_1) = \frac{1}{n-1}$ 입니다.
확률의 곱셈 정리($P(A \cap B) = P(A) \times P(B|A)$)를 적용하여 위의 전개식에 대입해 봅니다.

**[EN]** The probability that the 1st person gets the correct envelope is $P(A_1) = \frac{1}{n}$. 
Given that the 1st person got it right, the probability the 2nd person gets it right is $P(A_2 | A_1) = \frac{1}{n-1}$. 
By applying the multiplication rule, we substitute these into our expanded equation.

$$
P(\bigcup_{i=1}^{n} A_i) = n\left(\frac{1}{n}\right) - \binom{n}{2}\left(\frac{1}{n \cdot (n-1)}\right) + \binom{n}{3}\left(\frac{1}{n \cdot (n-1) \cdot (n-2)}\right) \dots
$$

이를 약분하고 정리하면 다음과 같은 아름다운 수열이 나옵니다.

$$
= 1 - \frac{1}{2!} + \frac{1}{3!} - \dots + (-1)^{n-1}\frac{1}{n!}
$$

### 테일러 급수와의 연관성 (Connection to Taylor Series of $e^x$)

자연상수 $e^x$의 테일러 급수 전개식은 다음과 같습니다.
$$e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots$$

여기에 $x = -1$을 대입하면:
$$e^{-1} = 1 - 1 + \frac{1}{2!} - \frac{1}{3!} + \frac{1}{4!} \dots$$

위 봉투 문제의 결과식은 전체 $1$에서 위 테일러 급수식($e^{-1}$)의 형태를 뺀 것과 일치하게 되어, $n$이 무한히 커질 때 다음 값에 수렴하게 됩니다.

$$
1 - \frac{1}{e} \approx 0.6321
$$

**💡 결론 (Conclusion):**
사람 수($n$)가 10명이든, 100명이든, 1억 명이든 관계없이 봉투를 무작위로 섞어 나누어 주었을 때 **"적어도 한 명은 자신의 제대로 된 봉투를 받을 확률"은 약 63.2%로 일정하게 고정**됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-11 The Envelope Problem-1" src="https://github.com/user-attachments/assets/81592042-cd9c-41d7-bd46-f060bbf5fdef" />
    <img width="1264" height="1635" alt="2-11 The Envelope Problem-2" src="https://github.com/user-attachments/assets/49b998aa-6c3c-447c-832f-e73fc640f111" />
    <img width="1264" height="1635" alt="2-11 The Envelope Problem-3" src="https://github.com/user-attachments/assets/cde013d4-d1be-414f-a712-c6edb217194e" />
  </div>
</details>
