---
title: "1-8 Standard Normal Distribution"
date: 2026-07-14 14:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, standard-normal, z-score, standardization, empirical-rule]
math: true
---

## 1. 표준 정규 분포 (Standard Normal Distribution)

**[KR]** 수많은 정규 분포 중에서도 **평균이 $0$이고 분산이 $1$인 가장 기본적이고 이상적인 형태**를 '표준 정규 분포'라고 부르며, 확률 변수로는 주로 $Z$를 사용합니다. 통계학자들이 이 분포를 사랑하는 이유는, 복잡한 적분 계산 없이도 미리 계산되어 있는 누적 분포 함수(CDF) 표(Z-table)나 소프트웨어를 통해 확률 값을 아주 쉽게 찾아낼 수 있기 때문입니다.

**[EN]** Among the infinite number of normal distributions, the **Standard Normal Distribution** is the most fundamental and ideal form, characterized by a **mean of $0$ and a variance of $1$**, typically denoted by the random variable $Z$. Statisticians favor this distribution because it eliminates the need for complex integration; one can simply look up probabilities using pre-calculated Cumulative Distribution Function (CDF) tables (Z-tables) or software.

* **확률 밀도 함수 (pdf):** $\phi(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2/2}$
* **누적 분포 함수 (CDF):** $\Phi(z) = \int_{-\infty}^z \phi(t) \,dt$

---

## 2. 대칭성과 통계적 기법 (Symmetry and Probabilities)

**[KR]** 표준 정규 분포 곡선은 $z=0$을 축으로 완벽한 좌우 대칭을 이룹니다. 이러한 대칭성 덕분에 음수 구간의 누적 확률을 구할 때도 양수 구간의 정보를 그대로 재활용할 수 있는 매우 유용한 기하학적 성질들이 파생됩니다.

**[EN]** The standard normal curve is perfectly symmetrical around the vertical axis at $z=0$. Thanks to this symmetry, we can derive highly useful geometric properties that allow us to calculate cumulative probabilities for negative values by simply reusing information from the positive side.

* **대칭성의 핵심 성질 (Symmetry Properties):**
  $$P(Z > b) = 1 - \Phi(b)$$
  $$\Phi(-b) = 1 - \Phi(b)$$
  $$P(-b \le Z \le b) = 2\Phi(b) - 1$$

---

## 3. Z-스코어와 표준화 (Standardization to Z-score)

**[KR]** 세상의 모든 정규 분포 $X \sim N(\mu, \sigma^2)$ 는 간단한 선형 변환을 거쳐 표준 정규 분포로 둔갑할 수 있습니다. 자신의 값에서 평균 $\mu$를 빼서 중심을 $0$으로 맞추고, 이를 표준편차 $\sigma$로 나누어 눈금을 $1$로 맞춰주는 이 과정을 **표준화(Standardization)**라고 합니다. 이렇게 변환된 값을 $Z$-스코어라고 부릅니다.

**[EN]** Every normal distribution in the world $X \sim N(\mu, \sigma^2)$ can be transformed into the standard normal distribution through a simple linear transformation. By subtracting the mean $\mu$ to shift the center to $0$, and dividing by the standard deviation $\sigma$ to scale the spread to $1$, we perform what is called **Standardization**. The resulting value is known as a $Z$-score.

$$
Z = \frac{X - \mu}{\sigma} \sim N(0, 1)
$$

### 자주 쓰이는 임계값과 분위수 (Famous Quantiles)
통계적 가설 검정이나 신뢰 구간(Confidence Interval)을 설정할 때 자주 등장하는 $Z$ 값들은 외워두는 것이 좋습니다. 확률 $p$를 만족하는 $Z$ 값을 $p$분위수($\Phi^{-1}(p)$)라고 합니다.
* 상위 $5\%$ 꼬리 ($p = 0.95$): $Z \approx 1.645$
* 상위 $2.5\%$ 꼬리 ($p = 0.975$): $Z \approx 1.96$ (95% 신뢰구간의 핵심 수치)
* 상위 $0.5\%$ 꼬리 ($p = 0.995$): $Z \approx 2.58$

---

## 4. 실전 응용 예제 (Practical Applications)

**[KR]** 서로 다른 평균과 분산을 가진 두 집단을 비교할 때, 앞서 배운 선형 결합의 성질과 표준화 기법을 융합하면 아주 우아하게 확률을 계산해낼 수 있습니다.

**[EN]** When comparing two groups with different means and variances, fusing the additive properties of normal distributions with the standardization technique allows us to calculate probabilities very elegantly.

**예제: 남녀의 키 비교 (Comparing Heights)**
* 남성의 키 $M \sim N(68, 4)$
* 여성의 키 $W \sim N(65, 1)$
* **질문:** 무작위로 뽑은 한 여성이 무작위로 뽑은 한 남성보다 더 클 확률은?

1. **새로운 확률 변수 정의:** 여성의 키에서 남성의 키를 뺀 변수 $W - M$ 을 정의합니다.
2. **분포 계산:** 정규 분포의 선형 결합 성질에 의해, 이 새로운 변수는 평균이 $65 - 68 = -3$ 이고, 분산이 $1 + 4 = 5$ 인 새로운 정규 분포를 따릅니다. 즉, $W - M \sim N(-3, 5)$ 입니다.
3. **표준화 및 확률 도출:** 여성이 남성보다 크다는 것은 $W - M > 0$ 임을 의미합니다.
   
$$
P(W - M > 0) = P\left(Z > \frac{0 - (-3)}{\sqrt{5}}\right) = P\left(Z > \frac{3}{\sqrt{5}}\right)
$$
   
이를 계산하면 $1 - \Phi(1.34)$ 가 되며, 최종적으로 약 $9\%$ 의 확률이 도출됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-8 Standard Normal Distribution-1" src="https://github.com/user-attachments/assets/aeac7dd8-64b3-46fc-83be-0ee526adb3c3" />
    <img width="1264" height="1635" alt="1-8 Standard Normal Distribution-2" src="https://github.com/user-attachments/assets/64d94253-de9a-4cb0-be36-15f5ba378c87" />
    <img width="1264" height="1635" alt="1-8 Standard Normal Distribution-3" src="https://github.com/user-attachments/assets/dd7dcfb5-42b4-43fe-a2b3-a5f3b7dc5715" />
  </div>
</details>
