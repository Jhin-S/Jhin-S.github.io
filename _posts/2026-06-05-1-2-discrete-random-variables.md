---
title: "1-2 Discrete Random Variables"
date: 2026-06-05 17:35:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, random-variable, pmf, binomial, poisson]
math: true
---

## 1. 이산 확률 변수와 확률 질량 함수 (Discrete RVs & PMF)

**[KR]** 이산 확률 변수 $X$가 특정한 값 $x$를 가질 정확한 확률을 나타내는 함수를 **확률 질량 함수(Probability Mass Function, pmf)**라고 부릅니다. 기호로는 $f(x) \equiv P(X=x)$로 표기합니다. 당연하게도, 모든 가능한 사건의 확률을 더하면 그 합은 항상 1이 됩니다 ($\sum f(x) = 1$).
예를 들어, 균등 분포(Uniform Distribution)를 따르는 주사위의 경우 $x \in \{1, 2, 3, 4, 5, 6\}$에 대해 각각의 확률 질량 함수 값은 $f(x) = \frac{1}{6}$이 됩니다.

**[EN]** If $X$ is a discrete random variable, its probability mass function (pmf) defines the exact probability that $X$ takes a specific value $x$. It is denoted as $f(x) \equiv P(X=x)$. The sum of all probabilities across the sample space must equal 1. For instance, in a uniform distribution like rolling a fair die, $f(x) = \frac{1}{6}$ for each face.

---

## 2. 이항 분포 (Binomial Distribution)

**[KR]** 결과가 오직 '성공' 아니면 '실패' 두 가지로만 나뉘는 실험을 **베르누이 시행(Bernoulli trials)**이라고 합니다. 이러한 베르누이 시행을 서로 영향을 주지 않게(독립적으로) $n$번 반복했을 때, **성공한 총 횟수 $X$가 따르는 확률 분포**를 이항 분포라고 합니다. 기호로는 $X \sim Bin(n, p)$로 적습니다.

**[EN]** Let $X$ denote the total number of "successes" from $n$ independent trials, where each trial has a constant probability of success, $p$. These are known as Bernoulli trials. The random variable $X$ follows the Binomial distribution, denoted as $X \sim Bin(n, p)$.

성공 확률이 $p$, 실패 확률이 $q = (1-p)$일 때, $n$번 중 정확히 $k$번 성공할 확률 공식은 다음과 같습니다.

$$
P(X=k) = \binom{n}{k} p^k q^{n-k}
$$

* **직관적 이해:** 특정 순서로 $k$번 성공하고 $n-k$번 실패할 확률($p^k q^{n-k}$)에, $n$개의 자리 중 성공이 배치될 $k$개의 자리를 고르는 경우의 수($\binom{n}{k}$)를 곱한 것입니다.

---

## 3. 푸아송 분포의 필요성과 직관 (Intuition behind Poisson Distribution)

**[KR]** 이항 분포는 동전이나 주사위처럼 '시행 횟수($n$)'가 명확하게 정해진 경우에 씁니다. 하지만 현실에서는 다음과 같은 문제에 부딪힙니다.
* **상황:** 대형 쇼핑몰의 하루 방문객 수, 또는 특정 사거리에서의 주간 교통사고 발생 건수를 구하고 싶습니다.
* **한계:** 잠재적인 전체 인구($n$)는 수백만 명으로 무한대에 가깝고($n \to \infty$), 그 수많은 사람 중 하필 특정 1명이 오늘 방문할 확률($p$)은 극도로 0에 가깝습니다($p \to 0$). 이항 분포로 계산하려 하면 컴퓨터조차 처리하기 힘듭니다.

그래서 시행 횟수의 상한선은 없지만, **평균적인 발생 횟수($\lambda$)**는 알고 있는 자연 현상이나 데이터를 분석하기 위해 이항 분포의 극한을 취해 만들어낸 것이 바로 **푸아송 분포(Poisson Distribution)**입니다.

**[EN]** The Binomial distribution is perfect when the number of trials ($n$) is fixed and known. However, in real-world scenarios—like predicting the number of visitors to a mall or traffic accidents at an intersection—the total potential population ($n$) approaches infinity, while the probability of a single specific occurrence ($p$) approaches zero. 
To analyze such phenomena where the exact number of trials is infinite but the **average rate of occurrence ($\lambda$)** is known, we use the Poisson distribution, which is mathematically derived from the limit of the Binomial distribution.

$$
P(X=k) = \frac{e^{-\lambda} \lambda^k}{k!}
$$

*(기호 표기: $X \sim Pois(\lambda)$)*

---

## 4. 푸아송 분포의 유도 과정 (Derivation of Poisson Distribution)

**[KR]** 이항 분포의 평균 공식 $E(X) = np$에서, 우리는 $\lambda = np$로 둘 수 있습니다. 즉, $p = \frac{\lambda}{n}$입니다. 이를 이항 분포 공식에 대입한 뒤 $n$을 무한대($\infty$)로 보내는 극한을 취해 공식을 유도합니다.

**[EN]** From the binomial expected value $E(X) = np$, we can set the average rate $\lambda = np$, which implies $p = \frac{\lambda}{n}$. By substituting this into the binomial probability mass function and taking the limit as $n \rightarrow \infty$, we derive the Poisson formula.

$$
P(X=k) = \binom{n}{k} \left(\frac{\lambda}{n}\right)^k \left(1 - \frac{\lambda}{n}\right)^{n-k}
$$

식을 팩토리얼과 지수 법칙을 이용해 두 개의 덩어리로 쪼개어 분석합니다:

1. **첫 번째 덩어리 극한 처리:**
$$
\lim_{n \to \infty} \frac{n(n-1) \dots (n-k+1)}{k! \, n^k} \lambda^k = \frac{\lambda^k}{k!}
$$
(분자와 분모 모두 최고차항이 $n^k$이므로 약분되어 1로 수렴합니다.)

2. **두 번째 덩어리 극한 처리 (자연상수 $e$의 정의 활용):**
$$
\lim_{n \to \infty} \left(1 - \frac{\lambda}{n}\right)^n \left(1 - \frac{\lambda}{n}\right)^{-k} = e^{-\lambda} \cdot 1
$$

이 두 결과를 합치면 최종적으로 앞서 본 푸아송 분포의 아름다운 공식이 완성됩니다.

$$
\lim_{n \to \infty} P(X=k) = \frac{e^{-\lambda} \lambda^k}{k!}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-1" src="https://github.com/user-attachments/assets/01c92c1f-c115-4810-9452-f761d7ca8507" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-2" src="https://github.com/user-attachments/assets/cbd96376-3dc7-4c68-96a7-c993e8eb2938" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-3" src="https://github.com/user-attachments/assets/6aa15ceb-94e2-44f5-a11d-4c7a515501cb" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-4" src="https://github.com/user-attachments/assets/e2aae827-3e5b-42b4-baf3-d452a317e3ad" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-5" src="https://github.com/user-attachments/assets/63b28df2-62b5-4b2a-9ae5-b178f92a9717" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-6" src="https://github.com/user-attachments/assets/ff72fd48-439a-49b1-8d92-cabef7d59fa2" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-7" src="https://github.com/user-attachments/assets/e1fa6e73-08f1-4e96-bc74-6555eb0360fb" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-8" src="https://github.com/user-attachments/assets/1f074e5a-2f3c-44e6-8aef-738d55309520" />
    <img width="1264" height="1635" alt="1-2 Discrete Random Variables-9" src="https://github.com/user-attachments/assets/9f165d53-3d67-49eb-a9c6-89a42299f2c8" />
  </div>
</details>
