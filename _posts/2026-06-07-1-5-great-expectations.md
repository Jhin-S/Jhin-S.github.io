---
title: "1-5 Great Expectations"
date: 2026-06-07 14:12:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, expected-value, geometric-distribution, exponential-distribution]
math: true
---

## 1. 기댓값의 정의와 의미 (Expected Value & Mean)

**[KR]** 확률 변수 $X$의 평균(Mean) 또는 기댓값(Expected Value, $\mu$)은 확률 분포가 전체적으로 어느 위치를 중심으로 모여있는지를 나타내는 중심 경향성(Central Tendency)의 지표입니다. 
단순한 산술 평균이 아니라, 각 사건이 발생할 확률 $f(x)$를 가중치(Weight)로 곱하여 더하는 **가중 평균(Weighted Average)**의 개념을 갖습니다.

**[EN]** The expected value $E[X]$ or mean $\mu$ indicates the central tendency of a random variable. It is not a simple average, but rather a **weighted average** of all possible values, where the weights are their respective probabilities $f(x)$.

* **이산 확률 변수 (Discrete RV):** $\mu = E[X] = \sum_{x} x f(x)$
* **연속 확률 변수 (Continuous RV):** $\mu = E[X] = \int_{-\infty}^{\infty} x f(x) \,dx$

### 기본 예시 (Basic Examples)
1. **베르누이 분포 (Bernoulli Distribution):** 성공 확률이 $p$일 때, $E[X] = (1 \cdot p) + (0 \cdot q) = p$
2. **주사위 던지기 (Uniform on 1~6):** $E[X] = 1(\frac{1}{6}) + 2(\frac{1}{6}) + \dots + 6(\frac{1}{6}) = 3.5$

---

## 2. 기하분포와 기댓값 (Geometric Distribution)

**[KR]** 기하분포는 '첫 번째 성공'을 거둘 때까지 시도한 총 횟수 $X$를 모델링합니다. (성공 확률을 $p$, 실패 확률을 $q = 1-p$라고 합니다.)
**[EN]** The geometric distribution models the number of trials $X$ needed to achieve the first success. ($X \sim Geom(p)$)

$$
f(x) = q^{x-1} p \quad (x = 1, 2, 3, \dots)
$$

### 실전 예제: 농구 자유투 (Basketball Free Throws)
성공 확률이 $p = 0.4$ 인 선수가 있습니다.
1. **최소 3번 이상 슛을 쏴야 첫 성공을 거둘 확률 ($P(X \ge 3)$):**
   전체 확률 1에서, 1번 만에 성공할 확률과 2번 만에 성공할 확률을 빼서 구합니다.
   $$P(X \ge 3) = 1 - P(X=1) - P(X=2) = 1 - 0.4 - (0.6 \times 0.4) = 0.36$$
2. **첫 성공까지 필요한 평균 슛 횟수 ($E[X]$):**
   기하분포의 평균 공식에 의해 $E[X] = 1/p$ 이므로, $1 / 0.4 = 2.5$ 번입니다.

### 기댓값 공식의 수학적 증명 (Derivation of $E[X] = 1/p$)
무한 등비급수의 미분을 활용하여 아름답게 증명할 수 있습니다.

$$
E[X] = \sum_{x=1}^{\infty} x q^{x-1} p = p \sum_{x=1}^{\infty} \frac{d}{dq} q^x
$$

미분 기호를 시그마 밖으로 빼내고 등비급수의 합 공식을 적용합니다.

$$
= p \frac{d}{dq} \left( \sum_{x=1}^{\infty} q^x \right) = p \frac{d}{dq} \left( \frac{q}{1-q} \right) = p \left[ \frac{(1-q) - q(-1)}{(1-q)^2} \right] = \frac{p}{p^2} = \frac{1}{p}
$$

---

## 3. 지수분포와 푸아송 분포의 관계 (Exponential & Poisson)

**[KR]** 지수분포는 어떤 사건이 발생할 때까지 걸리는 '대기 시간'을 모델링하며 $X \sim Exp(\lambda)$ 로 표기합니다. 이 분포의 기댓값 부분적분을 통해 $E[X] = \frac{1}{\lambda}$ 로 계산됩니다.
특히, 지수분포는 푸아송 분포(Poisson)와 아주 깊은 연관성을 가집니다.

**[EN]** The exponential distribution models the waiting time until a specific event occurs, denoted as $X \sim Exp(\lambda)$. Using integration by parts, its expected value is found to be $E[X] = \frac{1}{\lambda}$. It is deeply related to the Poisson distribution.

### 왜 지수분포의 pdf가 그렇게 생겼을까? (Intuition)
푸아송 분포에서 어떤 단위 시간(길이 $x$) 동안 사건이 평균 $\lambda x$ 번 발생한다고 합시다.
첫 번째 사건이 일어날 때까지 걸린 대기 시간 $X$가 특정 시간 $x$보다 클 확률($P(X > x)$)은, 다르게 말하면 **"시간 $x$ 동안 사건이 단 한 번도 일어나지 않았다(발생 횟수 $k=0$)"**는 뜻과 완벽하게 같습니다.

푸아송 공식 $P(k) = \frac{(\lambda x)^k e^{-\lambda x}}{k!}$ 에 $k=0$을 대입해 봅시다.

$$
P(X > x) = \frac{(\lambda x)^0 e^{-\lambda x}}{0!} = e^{-\lambda x}
$$

이제 우리가 원하는 누적 분포 함수(CDF)를 구하기 위해 여사건을 적용합니다.
$$
F(x) = P(X \le x) = 1 - e^{-\lambda x}
$$

마지막으로 이 CDF를 미분하면, 우리가 잘 알고 있는 지수분포의 확률 밀도 함수(pdf)가 탄생합니다.
$$
f(x) = \frac{d}{dx} F(x) = \lambda e^{-\lambda x}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-5 Great Expectations-1" src="https://github.com/user-attachments/assets/0272f27b-77aa-453d-aa97-8598bf97124c" />
    <img width="1264" height="1635" alt="1-5 Great Expectations-2" src="https://github.com/user-attachments/assets/3fba572c-f933-4a18-b6e1-f37c8a792636" />
    <img width="1264" height="1635" alt="1-5 Great Expectations-3" src="https://github.com/user-attachments/assets/811bd27e-1e9a-4a4a-a68e-f526bc8fd896" />
    <img width="1264" height="1635" alt="1-5 Great Expectations-4" src="https://github.com/user-attachments/assets/bce334ba-563a-45a1-a315-3dee30ea48c1" />
    <img width="1264" height="1635" alt="1-5 Great Expectations-5" src="https://github.com/user-attachments/assets/565b48c2-2727-4185-be0f-51026e5b2dab" />
  </div>
</details>
