---
title: "1-11 The Central Limit Theorem Examples"
date: 2026-07-14 14:45:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, clt, normal-approximation, continuity-correction, binomial]
math: true
---

## 1. 중심 극한 정리의 위력 (The Power of the CLT)

**[KR]** 중심 극한 정리(CLT)가 진정으로 위대한 이유는 원래 데이터의 분포 모양을 전혀 몰라도 된다는 점입니다. 원본이 사각형 모양의 균등 분포이든, 한쪽으로 쏠린 지수 분포이든 상관없이 표본의 개수가 많아지면 결국 완벽한 종 모양의 정규 분포로 수렴합니다. 심지어 평균이 1000이고 표준편차가 1000이라는 사실 외에는 아무것도 모르는 미지의 분포에서 데이터를 뽑더라도, 표본 평균의 확률을 아주 정확하게 계산할 수 있습니다.

**[EN]** The true greatness of the Central Limit Theorem (CLT) lies in the fact that you don't need to know the shape of the original population distribution. Whether the original data follows a rectangular uniform distribution or a heavily skewed exponential distribution, a sufficiently large sample size will inexorably force the sample mean to converge into a perfect, bell-shaped normal distribution. Even if we sample from an entirely unknown distribution where we only know the mean is 1000 and the standard deviation is 1000, we can still calculate the probabilities of the sample mean with remarkable accuracy.

**[수학적 적용 예시]**
평균이 $\mu = 1000$, 표준편차가 $\sigma = 1000$ 인 미지의 분포에서 $100$개의 표본을 추출했을 때, 표본 평균 $\bar{X}$가 $950$에서 $1050$ 사이일 확률은 오직 $Z$-스코어 표준화만으로 구할 수 있습니다.

$$
Z = \frac{\bar{X} - E[\bar{X}]}{\sqrt{Var(\bar{X})}} = \frac{\bar{X} - 1000}{1000 / \sqrt{100}} = \frac{\bar{X} - 1000}{100}
$$

$$
P(950 \le \bar{X} \le 1050) = P\left(\frac{950-1000}{100} \le Z \le \frac{1050-1000}{100}\right) = P(-0.5 \le Z \le 0.5) \approx 38.3\%
$$

---

## 2. 이항 분포의 정규 근사 (Normal Approximation to the Binomial)

**[KR]** 이항 분포 $Bin(n, p)$는 본질적으로 성공 확률이 $p$인 독립적인 베르누이 시행을 $n$번 더한 결과와 완벽하게 같습니다. 독립적인 사건들의 합이기 때문에, $n$이 충분히 커지면 이항 분포 역시 중심 극한 정리에 의해 자연스럽게 정규 분포의 형태를 띠게 됩니다. 이 성질을 이용하면 수백 번의 시행에 대한 확률을 구할 때 거대한 팩토리얼과 조합 수식을 일일이 계산하는 끔찍한 수고를 덜 수 있습니다. 통상적으로 $np \ge 5$ 이고 $nq \ge 5$ 일 때 이 근사가 아주 잘 들어맞습니다.

**[EN]** A Binomial distribution $Bin(n, p)$ is fundamentally identical to the sum of $n$ independent Bernoulli trials, each with a success probability of $p$. Since it is a sum of independent events, a sufficiently large $n$ guarantees that the binomial distribution will naturally take on the shape of a normal distribution due to the CLT. This property saves us from the nightmare of calculating massive factorials and combinations when evaluating probabilities for hundreds of trials. As a general rule of thumb, this approximation is considered highly reliable when $np \ge 5$ and $nq \ge 5$.

$$
Y \sim Bin(n, p) \implies Y \approx N(np, npq)
$$

---

## 3. 연속성 보정 (Continuity Correction)

**[KR]** 이항 분포는 정수 단위로 뚝뚝 끊어져 있는 이산형(Discrete) 분포이고, 정규 분포는 소수점 아래 무한대까지 이어지는 연속형(Continuous) 분포입니다. 이 근본적인 태생적 차이에서 오는 미세한 오차를 줄이기 위해, 목표값의 범위를 양옆으로 $0.5$만큼 넓혀주는 수학적 보정 작업을 **연속성 보정(Continuity Correction)**이라고 부릅니다.

**[EN]** The binomial distribution is discrete, meaning it only takes integer values, whereas the normal distribution is continuous, stretching infinitely through decimal places. To mitigate the slight discrepancies arising from this fundamental difference, we apply a mathematical adjustment called **Continuity Correction**, which widens the target boundaries by exactly $0.5$ in both directions.

### 실전 야구 경기 예제 (Baseball Game Example)
승률이 $80\%$ ($p = 0.8$)인 야구팀이 100경기($n = 100$)를 치를 때, 84승 이상을 거둘 확률 $P(Y \ge 84)$를 계산해 봅시다.

1. **정규 분포 근사:** $\mu = np = 80$, $\sigma^2 = npq = 16$ 이므로 $Y \approx N(80, 16)$ 을 따릅니다.
2. **연속성 보정 적용:** 이산형의 84 이상을 연속형으로 매끄럽게 덮기 위해 범위를 83.5부터 시작하도록 $P(Y \ge 83.5)$ 로 확장합니다.
3. **표준화 및 계산:**
   
$$
P(Y \ge 83.5) \approx P\left(Z \ge \frac{83.5 - 80}{\sqrt{16}}\right) = P(Z \ge 0.875) \approx 19.08\%
$$
   
(실제 복잡한 이항 분포 공식을 컴퓨터로 계산한 정확한 정답인 $19.23\%$ 와 소수점 단위까지 아주 훌륭하게 들어맞는 것을 볼 수 있습니다.)

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-11 The Central Limit Theorem Examples-1" src="https://github.com/user-attachments/assets/773360d4-3823-4dc1-8c82-b5e97b4fd89b" />
    <img width="1264" height="1635" alt="1-11 The Central Limit Theorem Examples-2" src="https://github.com/user-attachments/assets/4fa0f69b-325d-4fab-8628-185ca4c1e36d" />
    <img width="1264" height="1635" alt="1-11 The Central Limit Theorem Examples-3" src="https://github.com/user-attachments/assets/b3980a81-e986-42a5-b575-32101ea24635" />
  </div>
</details>
