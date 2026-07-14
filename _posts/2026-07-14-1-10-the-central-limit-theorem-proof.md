---
title: "1-10 The Central Limit Theorem Proof"
date: 2026-07-14 14:30:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, central-limit-theorem, clt, proof, mgf, l-hospital]
math: true
---

## 1. 중심 극한 정리 (The Central Limit Theorem, CLT)

**[KR]** 확률과 통계 역사상 가장 위대하고 중요한 정리인 **중심 극한 정리(Central Limit Theorem)**입니다. 서로 독립이고 동일한 분포(i.i.d)를 따르는 확률 변수들 $X_1, X_2, \dots, X_n$이 있을 때, 원본 데이터가 정규 분포든, 이산 분포든, 심지어 형태를 알 수 없는 괴상한 분포든 상관없이 **"표본의 크기 $n$이 무한히 커지면, 표본 평균 $\bar{X}$의 분포는 결국 정규 분포에 수렴한다"**는 놀라운 마법 같은 법칙입니다.

**[EN]** The **Central Limit Theorem (CLT)** isarguably the most profound and critical theorem in the history of probability and statistics. Given independent and identically distributed (i.i.d) random variables $X_1, X_2, \dots, X_n$, regardless of whether the original population follows a normal distribution, a discrete distribution, or an unknown bizarre shape, the theorem states a magical fact: **"As the sample size $n$ approaches infinity, the distribution of the sample mean $\bar{X}$ ultimately converges to a normal distribution."**

표본 평균을 표준화한 확률 변수 $Z_n$의 누적 분포 함수는 $n \rightarrow \infty$ 일 때, 표준 정규 분포 $N(0, 1)$의 누적 분포 함수로 수렴합니다.

$$
Z_n = \frac{\bar{X} - \mu}{\sigma/\sqrt{n}} \xrightarrow{d} N(0, 1)
$$

---

## 2. 적률 생성 함수(MGF)를 이용한 증명 세팅 (Proof Setup via MGF)

**[KR]** 이 정리를 수학적으로 증명하기 위해 **적률 생성 함수(MGF)**의 수렴성을 이용합니다. 편의상, 그리고 어차피 표준화를 거칠 것이므로 원본 데이터의 평균을 $\mu = 0$, 분산을 $\sigma^2 = 1$로 가정(Without loss of generality)하고 시작하겠습니다. 우리의 최종 목표는 $Z_n$의 MGF가 표준 정규 분포의 MGF인 $e^{t^2/2}$ 로 수렴함을 보여주는 것입니다.

**[EN]** To prove this theorem mathematically, we utilize the convergence of the **Moment Generating Function (MGF)**. For convenience and without loss of generality (since we will standardize anyway), we assume the original data has a mean of $\mu = 0$ and a variance of $\sigma^2 = 1$. Our ultimate goal is to show that the MGF of $Z_n$ converges to $e^{t^2/2}$, which is the exact MGF of the Standard Normal Distribution.

표본 평균의 MGF 성질을 이용해 $Z_n$의 MGF를 식 하나로 정리하면 다음과 같습니다.

$$
M_{Z_n}(t) = \left[ M_X\left(\frac{t}{\sqrt{n}}\right) \right]^n
$$

---

## 3. 로피탈의 정리를 이용한 극한 계산 (Applying L'Hopital's Rule)

**[KR]** 위 식에 극한을 씌우기 위해 양변에 자연 로그($\ln$)를 취하고, 계산을 편하게 하기 위해 $y = \frac{1}{\sqrt{n}}$ 로 치환합니다. $n$이 무한대로 가면 $y$는 $0$으로 수렴합니다.

**[EN]** To apply limits, we take the natural logarithm ($\ln$) of both sides. For computational simplicity, we substitute $y = \frac{1}{\sqrt{n}}$. As $n$ approaches infinity, $y$ converges to $0$.

$$
\lim_{n \rightarrow \infty} \ln(M_{Z_n}(t)) = \lim_{y \rightarrow 0} \frac{\ln(M_X(ty))}{y^2}
$$

**[KR]** $y \rightarrow 0$ 일 때, 분모($y^2$)와 분자($\ln(M_X(0)) = \ln(1) = 0$) 모두 $0$으로 가는 **$0/0$ 꼴**이 되므로 미적분학의 **로피탈의 정리(L'Hopital's Rule)**를 연속으로 두 번 적용합니다.

**[EN]** As $y \rightarrow 0$, both the denominator ($y^2$) and the numerator ($\ln(M_X(0)) = \ln(1) = 0$) approach $0$, creating an indeterminate **$0/0$ form**. Thus, we apply **L'Hopital's Rule** from calculus twice consecutively.

1. **첫 번째 미분 (First Derivative):**
   
$$
\lim_{y \rightarrow 0} \frac{t M'_X(ty) / M_X(ty)}{2y} = \lim_{y \rightarrow 0} \frac{t M'_X(ty)}{2y M_X(ty)}
$$
   여전히 $M'_X(0) = \mu = 0$ 이므로 $0/0$ 꼴입니다. 한 번 더 미분합니다.

2. **두 번째 미분 (Second Derivative):**
   
$$
\lim_{y \rightarrow 0} \frac{t^2 M''_X(ty)}{2 M_X(ty) + 2yt M'_X(ty)} = \frac{t^2 M''_X(0)}{2 M_X(0) + 0}
$$

우리가 설정한 가정에 의해 $M_X(0) = 1$ 이고, 2차 적률인 $M''_X(0) = E[X^2] = \sigma^2 + \mu^2 = 1 + 0 = 1$ 이 됩니다. 결과적으로 이 극한값은 완벽하게 $\frac{t^2}{2}$ 로 귀결됩니다. 양변의 로그를 다시 벗겨주면 $e^{t^2/2}$ 가 되며 증명이 아름답게 완성됩니다.

---

## 4. 중심 극한 정리의 실무적 통찰 (Practical Insights of the CLT)

**[KR]** 이 정리가 우리에게 주는 통계적 의미는 실로 엄청납니다.
1. 데이터가 정규 분포가 아니더라도, 심지어 이산 확률 분포(동전 던지기 등)를 따르더라도 표본의 크기만 충분하다면 정규 분포의 마법을 빌려 쓸 수 있습니다.
2. 실무적으로 표본의 크기 $n \ge 30$ 이상이면 근사가 매우 훌륭하게 작동한다고 봅니다. (원래 분포가 대칭적이라면 30개보다 적어도 잘 작동합니다.)
3. 우리가 앞으로 배우게 될 통계적 추정이나 가설 검정에서, 진짜 모평균($\mu$)을 알 수 없더라도 표본 데이터를 믿고 수학적 분석을 전개할 수 있는 가장 강력한 명분이 됩니다.

**[EN]** The practical implications of this theorem are truly monumental.
1. Even if the population is completely non-normal or strictly discrete (like coin flips), as long as the sample size is sufficient, we can borrow the magic of the normal distribution.
2. In practice, a sample size of $n \ge 30$ is generally considered large enough for an excellent approximation. (If the original distribution is symmetric, even fewer observations are needed.)
3. It provides the strongest justification for future statistical estimations and hypothesis testing, allowing us to confidently perform mathematical analysis using sample data even when the true population mean ($\mu$) is unknown.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-10 The Central Limit Theorem Proof-1" src="https://github.com/user-attachments/assets/7d3cff29-6acc-4762-93c2-f128d12a715f" />
    <img width="1264" height="1635" alt="1-10 The Central Limit Theorem Proof-2" src="https://github.com/user-attachments/assets/78506a14-a5be-483b-a11a-eacf4670da25" />
  </div>
</details>
