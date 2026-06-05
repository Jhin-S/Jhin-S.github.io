---
title: "2-9 Permutations vs Combinations"
date: 2026-06-05 14:28:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, permutations, combinations]
math: true
---

## 문제 소개 (Problem Introduction)

**[KR]** 확률 문제를 풀 때 **순열(Permutations)**을 사용할지 **조합(Combinations)**을 사용할지는 문제에 접근하는 관점(Approach)에 따라 달라집니다. 다음 예제를 통해 두 가지 방식의 풀이 과정과 효율성을 비교해 보겠습니다.

**[EN]** Whether to use **permutations** or **combinations** depends on how you approach the problem. Let's compare the two methods and their efficiency using the following example.

> **Example:** 4개의 빨간 구슬(R)과 2개의 하얀 구슬(W)을 무작위 순서로 일렬로 나열할 때, 다음의 확률을 구하시오.
> (4 red marbles, 2 whites. Put them in a row in random order. Find:)
> 
> * **(a)** 양 끝의 구슬이 모두 하얀색일 확률 ($P(\text{2 end marbles are W})$)
> * **(b)** 양 끝의 구슬이 모두 하얀색이 아닐 확률 ($P(\text{2 end marbles aren't both W})$)
> * **(c)** 2개의 하얀 구슬이 나란히 있을 확률 ($P(\text{2 W's are side by side})$)

---

## Method 1: 순열을 이용한 풀이 (Using Permutations)

**[KR]** 첫 번째 방법은 모든 구슬을 서로 다른 것으로 간주하고 일렬로 나열하는 **순열(Permutations)** 방식을 사용합니다. 
전체 표본 공간(Sample Space) $S$는 6개의 구슬을 무작위로 배열하는 모든 경우의 수입니다.

**[EN]** The first method treats all marbles as distinct items and uses **permutations**. 
The sample space $S$ is every random ordering of the 6 marbles.

$$
|S| = 6! = 720
$$

* **(a) $A$: 양 끝이 하얀 구슬인 경우 (W _ _ _ _ W)**
  양 끝의 자리에 하얀 구슬 2개를 배열하는 경우의 수($2!$)에, 가운데 4자리에 빨간 구슬 4개를 배열하는 경우의 수($4!$)를 곱합니다.
  
$$
|A| = 2! \times 4! = 48
$$

$$
P(A) = \frac{|A|}{|S|} = \frac{48}{720} = \frac{1}{15}
$$

* **(b) $\bar{A}$: 양 끝이 모두 하얀 구슬은 아닌 경우**
  여사건의 확률을 이용합니다.
  
$$
P(\bar{A}) = 1 - P(A) = 1 - \frac{1}{15} = \frac{14}{15}
$$

* **(c) $B$: 2개의 하얀 구슬이 나란히 있는 경우**
  하얀 구슬 2개가 들어갈 이웃한 두 자리를 선택하는 경우의 수(5가지) $\times$ 하얀 구슬 2개를 그 자리에 배열($2!$) $\times$ 나머지 빨간 구슬 배열($4!$).
  
$$
|B| = 5 \times 2! \times 4! = 240
$$

$$
P(B) = \frac{|B|}{|S|} = \frac{240}{720} = \frac{1}{3}
$$

---

## Method 2: 조합을 이용한 풀이 (Using Combinations)

**[KR]** 순열을 이용한 방법은 팩토리얼 계산이 들어가 다소 번거로울 수 있습니다. 관점을 바꿔서, 구슬 전체를 나열하는 대신 **"하얀 구슬 2개가 어느 두 자리를 차지할 것인가?"**에만 집중하면 **조합(Combinations)**을 이용해 훨씬 쉽게 풀 수 있습니다.

**[EN]** Method 1 took too much time! Here's an easier way. Instead of arranging all marbles, let's just ask: **"Which 2 positions do the W's occupy?"** Now, the sample space $S$ is simply the possible pairs of slots that the W's can occupy out of 6 available slots.

$$
|S| = \binom{6}{2} = 15
$$

* **(a) $A$: 양 끝자리를 차지하는 경우**
  하얀 구슬이 맨 앞과 맨 뒤 자리를 차지하는 경우는 정확히 딱 **1가지** 뿐입니다.
  
$$
|A| = 1 \implies P(A) = \frac{|A|}{|S|} = \frac{1}{15}
$$

* **(b) $\bar{A}$: 양 끝이 아닌 경우**
  마찬가지로 여사건을 적용합니다.
  
$$
P(\bar{A}) = 1 - \frac{1}{15} = \frac{14}{15}
$$

* **(c) $B$: 나란히 두 자리를 차지하는 경우**
  6개의 자리 중 나란히 붙어있는 두 자리를 고르는 경우는 (1,2), (2,3), (3,4), (4,5), (5,6)으로 총 **5가지**입니다.
  
$$
|B| = 5 \implies P(B) = \frac{|B|}{|S|} = \frac{5}{15} = \frac{1}{3}
$$

**💡 결론 (Conclusion):** 두 방법 모두 동일한 확률을 도출하지만, 문제 상황에 맞춰 '조합(Combinations)'으로 관점을 전환했을 때 풀이와 계산이 훨씬 빠르고 간결해짐(That was much nicer!)을 알 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-9 Permutations vs Combinations-1" src="https://github.com/user-attachments/assets/8d1ab74c-84c8-42ee-88cf-8b87b4f0c4c2" />
    <img width="1264" height="1635" alt="2-9 Permutations vs Combinations-2" src="https://github.com/user-attachments/assets/b3158202-c192-4fb1-85a0-4a81569c2430" />
  </div>
</details>
