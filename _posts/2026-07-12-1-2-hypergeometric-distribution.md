---
title: "1-2 Hypergeometric Distribution"
date: 2026-07-12 13:45:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, hypergeometric, binomial, expected-value, variance]
math: true
---

## 1. 초기하 분포의 정의 (Hypergeometric Distribution)

**[KR]** 초기하 분포는 전체 집단이 두 가지 그룹으로 나뉘어 있을 때, **'비복원 추출(Without Replacement)'** 방식으로 표본을 뽑을 경우 특정 그룹의 객체가 몇 번 뽑히는지를 모델링하는 확률 분포입니다. 
전체 $a+b$ 개의 객체 중 1번 타입이 $a$개, 2번 타입이 $b$개 있다고 가정해 봅시다. 여기서 무작위로 $n$개의 객체를 비복원 추출할 때, 1번 타입의 객체가 정확히 $k$개 뽑힐 확률 질량 함수(pmf)는 조합(Combination)을 이용하여 다음과 같이 정의됩니다.

**[EN]** The Hypergeometric distribution models the probability of a specific number of successes in a sequence of draws from a finite population **without replacement**. 
Suppose a population consists of $a+b$ objects, where $a$ objects are of Type 1 and $b$ objects are of Type 2. If we draw $n$ objects at random without replacement, the probability mass function (pmf) for drawing exactly $k$ objects of Type 1 is given by combinations as follows:

$$
P(X = k) = \frac{\binom{a}{k} \binom{b}{n-k}}{\binom{a+b}{n}}
$$

---

## 2. 실전 예제: 양말 뽑기 (Practice Example)

**[KR]** 상자 안에 빨간 양말 15개와 파란 양말 10개가 들어있습니다 (총 25개). 이 상자에서 무작위로 7개의 양말을 '다시 집어넣지 않고(비복원)' 뽑을 때, 빨간 양말이 정확히 3개 뽑힐 확률을 계산해 봅시다.

**[EN]** A box contains 15 red socks and 10 blue socks (25 socks in total). If you pick 7 socks at random without replacement, what is the probability of picking exactly 3 red socks?

빨간 양말 15개 중 3개를 뽑고, 동시에 파란 양말 10개 중 4개(7개 중 나머지)를 뽑아야 하므로 공식에 대입하면 다음과 같습니다.

$$
P(X = 3) = \frac{\binom{15}{3} \binom{10}{4}}{\binom{25}{7}}
$$

---

## 3. 기댓값, 분산 및 이항 분포와의 비교 (Mean, Variance, and Binomial Comparison)

**[KR]** 초기하 분포에서 1번 타입이 뽑힐 기본 비율을 $p = \frac{a}{a+b}$ 라고 생각해 볼 수 있습니다. 이를 바탕으로 초기하 분포의 평균과 분산을 구하고, 동일한 성공 확률 $p$를 가진 **이항 분포(Binomial Distribution)**와 비교해 보면 아주 흥미로운 통계적 성질을 발견할 수 있습니다.

**[EN]** In a hypergeometric distribution, the initial probability of drawing a Type 1 object can be thought of as $p = \frac{a}{a+b}$. By calculating the mean and variance and comparing them with a **Binomial Distribution** that shares the exact same success probability $p$, we can observe a fascinating statistical property.

* **초기하 분포의 평균과 분산 (Hypergeometric):**
  
$$
E[X] = n\left(\frac{a}{a+b}\right)
$$
  
$$
Var(X) = n\left(\frac{a}{a+b}\right)\left(1 - \frac{a}{a+b}\right)\left(\frac{a+b-n}{a+b-1}\right)
$$

* **이항 분포의 평균과 분산 (Binomial, 복원 추출을 가정한 경우):**
  
$$
E[Y] = n\left(\frac{a}{a+b}\right)
$$
  
$$
Var(Y) = n\left(\frac{a}{a+b}\right)\left(1 - \frac{a}{a+b}\right)
$$

**[결론 / Conclusion]**
초기하 분포와 이항 분포는 **평균(기댓값)이 완벽하게 동일**합니다. 하지만 분산의 경우, 초기하 분포에는 유한 모집단 수정 계수(Finite Population Correction Factor)인 $\left(\frac{a+b-n}{a+b-1}\right)$ 가 추가로 곱해져 있습니다. 
표본을 비복원으로 뽑을수록 상자 안에 남은 객체의 불확실성이 점점 줄어들기 때문에, **초기하 분포의 분산은 이항 분포의 분산보다 항상 더 작게 나타납니다.**

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-2 Hypergeometric Distribution-1" src="https://github.com/user-attachments/assets/3730cad5-4b2a-43d7-a9b7-6c04b90eff30" />
  </div>
</details>
