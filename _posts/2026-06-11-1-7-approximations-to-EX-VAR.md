---
title: "1-7 Approximations to E[h(X)] and Var(h(X))"
date: 2026-06-11 10:48:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, taylor-approximation, expected-value, variance]
math: true
---

## 1. 테일러 전개를 이용한 기댓값과 분산의 근사 (Approximations via Taylor Series)

**[KR]** 확률 변수 $X$에 대한 함수 $Y = h(X)$가 너무 복잡하여 기댓값과 분산을 정확하게 계산하기 어려울 때가 있습니다. 이때 우리는 미적분학에서 배운 **테일러 급수(Taylor Series)**를 활용하여, 원래 함수의 모양을 우리가 다루기 쉬운 다항식 형태로 '근사(Approximation)'함으로써 기댓값과 분산을 추정할 수 있습니다.

**[EN]** When a function of a random variable $Y = h(X)$ is too highly complex to calculate its expected value and variance exactly, we can use the **Taylor Series** from calculus. By approximating the complex function with a simpler polynomial, we can estimate its statistical properties with high accuracy.

---

## 2. 기댓값의 근사 유도 (Approximating Expected Value)

**[KR]** $X$의 평균을 $\mu = E[X]$, 분산을 $\sigma^2 = Var(X)$라고 합시다. 확률 변수 $X$가 주로 평균 $\mu$ 근처의 값을 가진다고 가정하고, 함수 $h(X)$를 $X = \mu$ 를 중심으로 2차 테일러 다항식으로 전개합니다.

**[EN]** Let $\mu = E[X]$ and $\sigma^2 = Var(X)$. Assuming that the random variable $X$ stays relatively close to its mean $\mu$, we can expand $h(X)$ using a second-order Taylor polynomial centered at $\mu$.

$$
h(X) \approx h(\mu) + h'(\mu)(X - \mu) + \frac{h''(\mu)}{2}(X - \mu)^2
$$

이제 양변에 기댓값(Expectation) 연산자 $E[\cdot]$를 취해줍니다.
* $E[h(\mu)]$는 상수이므로 그대로 $h(\mu)$가 됩니다.
* $E[X - \mu] = E[X] - \mu = \mu - \mu = 0$ 이므로 1차항은 완전히 사라집니다.
* $E[(X - \mu)^2]$는 분산의 정의에 의해 $\sigma^2$ 이 됩니다.

결과적으로 기댓값에 대한 아주 깔끔한 근사 공식을 얻을 수 있습니다.

$$
E[h(X)] \approx h(\mu) + \frac{h''(\mu)}{2}\sigma^2
$$

---

## 3. 분산의 근사 유도 (Approximating Variance)

**[KR]** 분산을 근사할 때는 계산의 편의를 위해 1차 테일러 전개까지만 사용합니다. 분산의 선형성 성질($Var(aX + b) = a^2 Var(X)$)을 이용하면 유도 과정이 매우 간단해집니다.

**[EN]** For the variance, we typically use a first-order (linear) Taylor approximation to keep the calculation manageable. By applying the linear properties of variance ($Var(aX + b) = a^2 Var(X)$), the derivation becomes very straightforward.

$$
Var(h(X)) \approx Var\Big(h(\mu) + h'(\mu)(X - \mu)\Big)
$$

여기서 $h(\mu)$와 $\mu h'(\mu)$는 모두 상수이므로 분산에 영향을 주지 않아 무시됩니다. 변수 $X$에 곱해진 계수 $h'(\mu)$만 제곱되어 밖으로 나오게 됩니다.

$$
Var(h(X)) \approx [h'(\mu)]^2 Var(X) = [h'(\mu)]^2 \sigma^2
$$

---

## 4. 실전 예제 (Practice Example)

**[KR]** 확률 밀도 함수가 $f(x) = 3x^2 \quad (0 \le x \le 1)$ 인 $X$가 있고, 아주 복잡해 보이는 함수 $Y = X^{3/4}$ 의 평균과 분산을 구한다고 가정해 봅시다.

**[EN]** Suppose a random variable $X$ has the probability density function $f(x) = 3x^2$ for $0 \le x \le 1$. We want to find the mean and variance of a relatively complex function $Y = X^{3/4}$.

먼저 $X$ 자체의 통계량을 구하면 평균 $\mu = 3/4$, 분산 $\sigma^2 = 0.0375$ 입니다.
테일러 근사를 위해 $h(\mu)$, $h'(\mu)$, $h''(\mu)$ 의 값을 $\mu = 0.75$ 에서 계산하면 다음과 같습니다.
* $h(\mu) = (0.75)^{3/4} \approx 0.8059$
* $h'(\mu) = \frac{3}{4}(0.75)^{-1/4} \approx 0.8059$
* $h''(\mu) = -\frac{3}{16}(0.75)^{-5/4} \approx -0.2686$

**1) 기댓값의 근사:**
$$
E[Y] \approx 0.8059 + \frac{-0.2686}{2}(0.0375) \approx 0.8009
$$
(실제 적분으로 구한 정확한 기댓값 $0.8$과 매우 유사합니다.)

**2) 분산의 근사:**
$$
Var(Y) \approx (0.8059)^2 (0.0375) \approx 0.0243
$$
(실제 적분으로 구한 정확한 분산 $0.0267$과 꽤 가깝게 추정된 것을 볼 수 있습니다.)

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-7 Approximations to E h(X)  and Var(h(X))-1" src="https://github.com/user-attachments/assets/0103d16e-f5d1-4e89-b37c-605beb28094b" />
    <img width="1264" height="1635" alt="1-7 Approximations to E h(X)  and Var(h(X))-2" src="https://github.com/user-attachments/assets/a4086e01-1770-4895-a97a-e5467ee23a93" />
    <img width="1264" height="1635" alt="1-7 Approximations to E h(X)  and Var(h(X))-3" src="https://github.com/user-attachments/assets/e4a01717-9d77-47d8-9be5-012e9d986ce3" />
    <img width="1264" height="1635" alt="1-7 Approximations to E h(X)  and Var(h(X))-4" src="https://github.com/user-attachments/assets/7879eb83-d5de-4331-99ba-f1ad17846081" />
    <img width="1264" height="1635" alt="1-7 Approximations to E h(X)  and Var(h(X))-5" src="https://github.com/user-attachments/assets/33bfc3a9-53bf-4a5f-b22d-b3c0b0a3f421" />
  </div>
</details>
