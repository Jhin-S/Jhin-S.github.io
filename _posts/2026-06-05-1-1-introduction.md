---
title: "1-1 Introduction"
date: 2026-06-05 17:15:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, random-variable, discrete, continuous]
math: true
---

## 1. 확률 변수의 정의 (Definition of a Random Variable)

**[KR]** 확률 변수(Random Variable, RV)는 표본 공간(Sample space)에 있는 각각의 실험 결과들을 실수(Real numbers)에 대응시키는 수학적 함수입니다. 표기할 때는 주로 $X, Y, Z$와 같은 대문자를 사용하여 확률 변수 자체를 나타내고, 소문자 $x, y, z$를 사용하여 그 변수가 가지는 특정한 실수 값을 나타냅니다. 

**[EN]** A random variable (RV) is essentially a function that maps outcomes from a sample space to the real number line, typically denoted as $X: S \rightarrow \mathbb{R}$. We use uppercase letters like $X, Y, Z$ to denote the random variables themselves, and lowercase letters like $x, y, z$ to represent their specific numerical values.

예를 들어, 동전 2개를 던지는 실험을 생각해 봅시다. 표본 공간 $S = \{HH, HT, TH, TT\}$에서 확률 변수 $X$를 '앞면(H)이 나오는 횟수'라고 정의한다면, 결과값은 다음과 같이 실수로 매핑됩니다.
* $X(TT) = 0$
* $X(HT) = X(TH) = 1$
* $X(HH) = 2$

이때 각각의 값이 나올 확률은 다음과 같이 표현할 수 있습니다.

$$
P(X=0) = \frac{1}{4}, \quad P(X=1) = \frac{1}{2}, \quad P(X=2) = \frac{1}{4}
$$

---

## 2. 확률 변수의 성질과 예시 (Properties and Examples)

**[KR]** 확률 변수는 실제 일어나는 물리적 사건의 형태가 다르더라도 수학적 확률 분포가 동일하다면 서로 같은 것으로 취급할 수 있습니다. 예를 들어, 동전을 던져 뒷면/앞면에 따라 각각 0과 1을 부여하는 확률 변수 $X$와, 주사위를 던져 1~3이 나오면 0, 4~6이 나오면 1을 부여하는 확률 변수 $Y$는 모두 0과 1을 가질 확률이 $\frac{1}{2}$로 동일하므로 이 문맥에서는 동일한 특징을 가집니다.

또한, 0과 1 사이의 임의의 실수를 선택하는 경우를 생각해 봅시다. 0과 1 사이에는 무한히 많은 실수가 존재하므로, 정확히 어떤 특정한 점(예: 0.65)을 뽑을 확률은 0이 됩니다 ($P(X=x)=0$). 이 경우에는 특정한 점이 아닌 구간의 길이(Interval length)를 통해 확률을 정의해야 합니다.

**[EN]** Different physical experiments can result in identically distributed random variables. For example, assigning 0 or 1 for a coin flip (Tails=0, Heads=1) yields the same probabilities as a dice roll where outcomes 1-3 map to 0 and 4-6 map to 1. Since both probabilities equal $\frac{1}{2}$ for the values 0 and 1, they are mathematically equivalent in this context.

Furthermore, consider picking a random real number between 0 and 1. Because there are infinitely many possibilities, the probability of selecting one exact point is zero ($P(X=x)=0$). Instead, the probability is determined by the length of the interval, such as $P(X \le 0.65) = 0.65$.

---

## 3. 이산형 vs 연속형 확률 변수 (Discrete vs. Continuous RVs)

**[KR]** 확률 변수가 가질 수 있는 값들의 형태에 따라 크게 이산형(Discrete)과 연속형(Continuous)으로 분류합니다.
1. **이산 확률 변수 (Discrete RV):** 동전 던지기나 주사위 굴리기처럼 확률 변수가 가질 수 있는 값의 개수가 유한하거나 셀 수 있는(Countable) 경우를 뜻합니다.
2. **연속 확률 변수 (Continuous RV):** 임의의 실수 뽑기처럼 무한한 범위의 값을 가질 수 있으며, 특정한 한 점에서의 확률이 항상 0인 경우를 뜻합니다.
3. 상황에 따라 두 성질이 혼합된 경우도 존재합니다. 예를 들어 대기줄에서 기다리는 시간은 운이 좋으면 정확히 '0분'(이산적 특징)일 수도 있고, 0보다 큰 임의의 실수 시간(연속적 특징)을 가질 수도 있습니다.

**[EN]** Based on the possible values a random variable can take, we classify them primarily into discrete and continuous types.
1. **Discrete RV:** The number of possible values is finite or countably infinite (e.g., counting coin flips or rolling dice).
2. **Continuous RV:** Takes on values over a continuous range where the probability at any specific, exact point is exactly zero (e.g., picking a random real number in a given interval).
3. Mixed distributions also exist. For example, waiting time in a line could be exactly zero (a discrete property) or any positive real number (a continuous property), combining both characteristics.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1 Introduction-1" src="https://github.com/user-attachments/assets/2797bad3-41b0-49c4-940a-90ea300fd80a" />
    <img width="1264" height="1635" alt="1-1 Introduction-2" src="https://github.com/user-attachments/assets/fa2dc484-78e5-481b-8f84-957f9a876a86" />
    <img width="1264" height="1635" alt="1-1 Introduction-3" src="https://github.com/user-attachments/assets/2140ca67-4b2a-48ba-9ee1-3a0ce1566b92" />
  </div>
</details>
