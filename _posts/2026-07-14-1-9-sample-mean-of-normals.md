---
title: "1-9 Sample Mean of Normals"
date: 2026-07-14 14:16:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, sample-mean, normal-distribution, law-of-large-numbers]
math: true
---

## 1. 정규 분포의 표본 평균 (Sample Mean of Normals)

**[KR]** 서로 독립이고 동일한 정규 분포 $N(\mu, \sigma^2)$를 따르는 $n$개의 확률 변수들 $X_1, X_2, \dots, X_n$이 있을 때, 이들의 산술 평균인 **표본 평균(Sample Mean, $\bar{X}$)** 역시 완벽한 정규 분포를 따릅니다. 표본 평균은 개별 정규 확률 변수들의 선형 결합(Linear Combination)으로 이루어져 있기 때문에, 정규 분포의 선형 결합 성질에 의해 자연스럽게 정규 분포 형태가 그대로 유지됩니다.

**[EN]** Given $n$ independent and identically distributed (i.i.d) random variables $X_1, X_2, \dots, X_n$ that follow a normal distribution $N(\mu, \sigma^2)$, their arithmetic average, known as the **Sample Mean ($\bar{X}$)**, also perfectly follows a normal distribution. Since the sample mean is a linear combination of independent normal variables, it inherently retains the normal distribution due to the additive property of normals.

* **표본 평균의 분포 (Distribution of $\bar{X}$):**
  $$\bar{X} = \frac{1}{n} \sum_{i=1}^n X_i \sim N\left(\mu, \frac{\sigma^2}{n}\right)$$
* **기댓값과 분산 (Mean and Variance):**
  $$E[\bar{X}] = \mu$$
  $$Var(\bar{X}) = \frac{\sigma^2}{n}$$

---

## 2. 대수의 법칙과 통계적 의미 (Law of Large Numbers)

**[KR]** 위 공식에서 아주 중요하고 핵심적인 통계적 통찰을 얻을 수 있습니다. 표본의 크기 $n$이 커질수록, 표본 평균의 기댓값은 원래의 모평균 $\mu$로 일정하게 유지되는 반면, 분산은 $n$에 반비례하여 점점 작아집니다. 즉, 데이터(관측치)를 많이 모을수록 표본 평균 $\bar{X}$가 실제 모평균 $\mu$ 근처에 아주 빽빽하게 밀집하게 되며, 이를 **대수의 법칙(Law of Large Numbers)**이라고 부릅니다. 이 성질 덕분에 우리는 알지 못하는 실제 모평균을 추정할 때 표본 평균을 훌륭한 추정량(Estimator)으로 사용할 수 있습니다.

**[EN]** A highly significant statistical insight emerges from this formula. As the sample size $n$ increases, the expected value of the sample mean remains constant at the population mean $\mu$, while its variance progressively shrinks in inverse proportion to $n$. In other words, gathering more observations causes the sample mean $\bar{X}$ to cluster very tightly around the true mean $\mu$. This is known as the **Law of Large Numbers**. Thanks to this property, the sample mean serves as an excellent estimator for the unknown true population mean in practice.

---

## 3. 실전 응용 예제 (Practice Example)

**[KR]** $n$개의 관측치가 서로 독립이며 각각 $N(14, 16)$ 인 정규 분포를 따른다고 가정해 봅시다. 이때, 우리가 구한 표본 평균 $\bar{X}$가 실제 모평균 $\mu=14$ 로부터 오차 $1$ 이내로 들어올 확률이 95% 이상이 되게 하려면, 최소 몇 개의 데이터를 뽑아야(관측해야) 할까요?

**[EN]** Suppose we have $n$ independent observations drawn from a normal distribution $N(14, 16)$. How many observations must you take to ensure that there is at least a 95% probability that the sample mean $\bar{X}$ falls within 1 unit of the true mean $\mu=14$?

1. **표본 평균의 분포 설정:** $\bar{X} \sim N(14, 16/n)$
2. **확률 부등식 세우기:** $P(|\bar{X} - 14| \le 1) \ge 0.95$
3. **표준화 (Standardization):** 양변에서 평균 $14$를 빼고 표준편차 $4/\sqrt{n}$ 으로 나누어 $Z$-스코어로 변환합니다.
   $$P\left(\frac{-1}{4/\sqrt{n}} \le Z \le \frac{1}{4/\sqrt{n}}\right) \ge 0.95$$
4. **누적 분포 함수(CDF) 적용:** 대칭성에 의해 $2\Phi(\sqrt{n}/4) - 1 \ge 0.95$ 이므로, $\Phi(\sqrt{n}/4) \ge 0.975$ 가 됩니다.
5. **임계값 계산:** 표준 정규 분포 표에서 상위 2.5%($0.975$)에 해당하는 $Z$ 값은 $1.96$입니다.
   $$\frac{\sqrt{n}}{4} \ge 1.96 \implies \sqrt{n} \ge 7.84 \implies n \ge 61.47$$
        
**결론:** 조건을 만족하기 위해서는 최소 **62개**의 표본을 관측하여 평균을 내야 합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-9 Sample Mean of Normals-1" src="https://github.com/user-attachments/assets/f45e2f39-7835-4d16-b64b-fa6cb0e4cac3" />
  </div>
</details>
