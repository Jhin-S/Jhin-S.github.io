---
title: "2-13 Conditional Probability"
date: 2026-06-05 15:56:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, conditional-probability, two-kids-problem]
math: true
---

## 1. 조건부 확률의 개념 (Idea of Conditional Probability)

**[KR]** 조건부 확률의 핵심 아이디어는 **'추가적인 정보를 얻었을 때 확률을 업데이트(Update)'**하는 것입니다. 사건 $B$가 일어났다는 정보는 전체 표본 공간(Sample space)을 $B$라는 새롭고 제한된 공간으로 축소시키는 역할을 합니다. $P(B) > 0$일 때, 사건 $B$가 주어졌을 때 사건 $A$가 일어날 조건부 확률은 다음과 같이 정의됩니다.

**[EN]** The core idea of conditional probability is to **update probabilities as we obtain more information**. The information that event $B$ has occurred allows us to regard $B$ as a new, restricted sample space. If $P(B) > 0$, the conditional probability of $A$ given $B$ is defined as:

$$
P(A \vert B) \equiv \frac{P(A \cap B)}{P(B)} = \frac{\vert A \cap B \vert / \vert S \vert}{\vert B \vert / \vert S \vert} = \frac{\vert A \cap B \vert}{\vert B \vert}
$$

* **Remark:** 만약 $A$와 $B$가 서로소(Disjoint, 교집합이 없음)라면, $P(A \vert B) = 0$이 됩니다. ($B$가 일어났다면 $A$가 일어날 가능성은 전혀 없기 때문입니다.)

---

## 2. 기본 예제 (Basic Examples)

### 주사위 예제 (Dice Example)
**[KR]** 주사위를 던질 때, 사건 $A = \{2, 4, 6\}$ (짝수)이고 사건 $B = \{1, 2, 3, 4, 5\}$ 라고 가정해 봅시다. 만약 $B$가 일어났다는 것을 안다면('6'이 나올 수 없다는 것을 의미), $A$가 일어날 확률은 어떻게 될까요?
**[EN]** Toss a die. Let $A = \{2, 4, 6\}$ and $B = \{1, 2, 3, 4, 5\}$. Suppose we know that $B$ occurs (so there is no way a "6" can come up). Then the probability that $A$ occurs given $B$ is:

$$
P(A \vert B) = \frac{\vert A \cap B \vert}{\vert B \vert} = \frac{2}{5}
$$

### 양말 뽑기 예제 (Socks Example)
**[KR]** 주머니에 4개의 하얀 양말(W)과 8개의 빨간 양말(R)이 있습니다. 비복원 추출로 2개를 뽑을 때 둘 다 하얀 양말일 확률을 구합니다. 사건 $A$를 '첫 번째가 W', 사건 $B$를 '두 번째가 W'로 둡니다.
**[EN]** 4 white sox, 8 red. Select 2 without replacement. Let $A$: 1st sock W, $B$: 2nd sock W, $C$: Both W ($A \cap B$).

$$
P(C) = P(A \cap B) = P(A)P(B \vert A) = \frac{4}{12} \cdot \frac{3}{11} = \frac{1}{11}
$$

---

## 3. 두 자녀 문제 (The Two Kids Problem)

**[KR]** 어떤 부부에게 두 명의 자녀가 있고, **적어도 한 명은 남자아이(Boy)**입니다. 이 때, **두 아이가 모두 남자아이일 확률**은 얼마일까요? 직관적으로 $\frac{1}{2}$이라 생각하기 쉽지만, 이는 오답입니다! 정보가 주어짐에 따라 표본 공간이 어떻게 축소되는지 봐야 합니다.
**[EN]** A couple has two kids and **at least one is a boy**. What's the probability that **BOTH are boys**? My intuition was $\frac{1}{2}$ — the wrong answer! As you get more information, you can make some surprising findings.

* 전체 표본 공간: $S = \{GG, GB, BG, BB\}$
* 사건 $D$ (적어도 한 명은 남자아이): $D = \{GB, BG, BB\}$
* 사건 $C$ (둘 다 남자아이): $C = \{BB\}$

$$
P(C \vert D) = \frac{P(C \cap D)}{P(D)} = \frac{1/4}{3/4} = \frac{1}{3}
$$

---

## 4. 심화: 화요일에 태어난 남자아이 (Honors Example: The Tuesday Boy)

**[KR]** 이번에는 조건이 추가됩니다. 어떤 부부에게 두 명의 자녀가 있고, **적어도 한 명은 화요일에 태어난 남자아이**입니다. 이 때, **두 아이가 모두 남자아이일 확률**은 얼마일까요?
**[EN]** A couple has two kids and **at least one is a boy born on a Tuesday**. What's the probability that **BOTH are boys**?

* $B_x$: $x$요일에 태어난 남자아이 (화요일은 $x=3$)
* 전체 표본 공간의 크기 (요일까지 고려): $\vert S \vert = 14 \times 14 = 196$
* 사건 $D$ (적어도 한 명은 화요일에 태어난 아들): 
  첫째가 화요일 아들인 경우 14가지 + 둘째가 화요일 아들인 경우 14가지 - 둘 다 화요일 아들인 중복 경우 1가지 $\implies \vert D \vert = 27$
* 사건 $C \cap D$ (둘 다 아들이고, 적어도 한 명은 화요일에 태어난 아들):
  첫째가 화요일 아들 & 둘째도 아들인 경우 7가지 + 첫째가 아들 & 둘째가 화요일 아들인 경우 7가지 - 중복 1가지 $\implies \vert C \cap D \vert = 13$

$$
P(C \vert D) = \frac{\vert C \cap D \vert}{\vert D \vert} = \frac{13}{27}
$$

---

## 5. 조건부 확률의 성질 (Properties of Conditional Probability)

**[KR]** 조건부 확률도 기존의 확률 공리(Axioms of Probability)와 유사한 성질들을 그대로 만족합니다.
**[EN]** Conditional probability has properties analogous to the Axioms of Probability.

1. $0 \le P(A \vert B) \le 1$
2. $P(S \vert B) = 1$ (축소된 표본 공간 내에서 일어날 확률은 100%)
3. 만약 $A_1$과 $A_2$가 서로소($A_1 \cap A_2 = \emptyset$)라면: 
   $$P(A_1 \cup A_2 \vert B) = P(A_1 \vert B) + P(A_2 \vert B)$$
4. 일반화: 만약 $A_1, A_2, \dots$ 가 모두 서로소라면:
   $$P(\bigcup_{i=1}^{\infty} A_i \vert B) = \sum_{i=1}^{\infty} P(A_i \vert B)$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-13 Conditional Probability-1" src="https://github.com/user-attachments/assets/0f9d5466-51e9-44a1-98ae-300e27596017" />
    <img width="1264" height="1635" alt="2-13 Conditional Probability-2" src="https://github.com/user-attachments/assets/96844bb4-1967-40fb-a2c2-d6e90cf04116" />
    <img width="1264" height="1635" alt="2-13 Conditional Probability-3" src="https://github.com/user-attachments/assets/acfe959f-dd37-4bbd-afc4-a71089601992" />
    <img width="1264" height="1635" alt="2-13 Conditional Probability-4" src="https://github.com/user-attachments/assets/fcb4191c-5a89-491d-b8f3-a210124763d6" />
    <img width="1264" height="1635" alt="2-13 Conditional Probability-5" src="https://github.com/user-attachments/assets/1b8ab99a-6580-4555-80ae-803b7c69be3b" />
  </div>
</details>
