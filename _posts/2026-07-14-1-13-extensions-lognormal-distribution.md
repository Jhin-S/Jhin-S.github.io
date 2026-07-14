---
title: "1-13 Extensions - Lognormal Distribution"
date: 2026-07-14 15:15:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, lognormal-distribution, black-scholes, option-pricing, finance]
math: true
---

## 1. 로그정규 분포 (Lognormal Distribution)

**[KR]** 확률 변수 $Y$가 정규 분포 $N(\mu_Y, \sigma_Y^2)$를 따를 때, 이 값을 자연상수 $e$의 지수로 올려 만든 새로운 변수 $X = e^Y$는 **로그정규 분포(Lognormal Distribution)**를 따르게 됩니다. 변수 $X$에 자연로그($\ln$)를 취하면 다시 정규 분포가 되기 때문에 이런 이름이 붙었습니다. 이 분포는 값이 무조건 $0$보다 커야 하고 오른쪽으로 꼬리가 길게 늘어지는 비대칭적인 데이터(예: 주식 가격, 소득 분포 등)를 모델링할 때 아주 강력한 도구가 됩니다.

**[EN]** When a random variable $Y$ follows a normal distribution $N(\mu_Y, \sigma_Y^2)$, transforming it by taking the exponential creates a new random variable $X = e^Y$ that follows the **Lognormal Distribution**. It earns its name because taking the natural logarithm ($\ln$) of $X$ yields a normal distribution again. This distribution is an exceptionally powerful tool for modeling asymmetric data that must strictly take positive values and features a long right tail, such as stock prices or income distributions.

* **확률 밀도 함수 (pdf):**
  
$$
f(x) = \frac{1}{x\sigma_Y\sqrt{2\pi}} \exp\left\{ -\frac{1}{2\sigma_Y^2} [\ln(x) - \mu_Y]^2 \right\}, \quad x > 0
$$

* **기댓값과 분산 (Mean and Variance):** 지수 변환의 특성상 평균과 분산의 수식이 정규 분포 파라미터들의 지수 형태로 표현됩니다.
  
$$
E[X] = \exp\left\{ \mu_Y + \frac{\sigma_Y^2}{2} \right\}
$$
  
$$
Var(X) = \exp\left\{ 2\mu_Y + \sigma_Y^2 \right\} \left( \exp\{\sigma_Y^2\} - 1 \right)
$$

### 확률 계산 예제 (Basic Probability Calculation)
만약 $Y \sim N(10, 4)$ 이고 $X = e^Y$ 일 때, $X$가 $1000$ 이하일 확률을 구해보겠습니다.
로그정규 분포의 확률은 양변에 로그를 취해 다시 친숙한 정규 분포 문제로 바꿔서 해결합니다.

$$
P(X \le 1000) = P(Y \le \ln(1000))
$$

이제 $Y$를 표준화(Standardization)하여 $Z$-스코어로 변환합니다.

$$
= P\left(Z \le \frac{\ln(1000) - 10}{\sqrt{4}}\right) = \Phi(-1.55) \approx 0.061
$$

---

## 2. 금융 공학과 블랙-숄즈 모형 (Finance & Black-Scholes Model)

**[KR]** 로그정규 분포가 역사상 가장 눈부시게 활약한 무대는 바로 금융 공학의 **옵션 가격 결정(Option Pricing)**입니다. 주가의 변동이 로그정규 분포를 따른다고 가정하면, 특정 미래 시점 $T$에서의 주가 $S(T)$를 다음과 같이 우아한 수학적 모델로 표현할 수 있습니다.

**[EN]** The grandest stage where the lognormal distribution has historically shined is **Option Pricing** in financial engineering. By assuming that stock price fluctuations follow a lognormal distribution, the future stock price $S(T)$ at a specific time $T$ can be elegantly modeled as follows:

$$
S(T) = S(0)\exp\left\{ \left(\mu - \frac{\sigma^2}{2}\right)T + \sigma\sqrt{T}Z \right\}
$$

(여기서 $\mu$는 주식의 자연적인 성장률(Drift), $\sigma$는 주가의 변동성(Volatility), $Z$는 표준 정규 분포 확률 변수를 의미합니다.)

### 유러피안 콜 옵션 (European Call Option)
**[KR]** 정해진 만기일 $T$에 특정 주식을 미리 약속된 행사가(Strike Price) $K$로 살 수 있는 권리를 '콜 옵션'이라고 합니다. 합리적인 투자자라면, 만기일에 실제 주가 $S(T)$가 행사가 $K$보다 높을 때만 권리를 행사하여 차익을 얻고, 반대의 경우엔 권리를 포기할 것입니다. 따라서 이 옵션의 본질적인 기대 가치(초기 지불 적정가) $E[C]$는 무위험 이자율 $r$을 반영하여 다음과 같이 정의됩니다.

**[EN]** A 'Call Option' grants the right to buy a specific stock at a pre-agreed strike price $K$ on a set expiry date $T$. A rational investor will only exercise this right to make a profit if the actual stock price $S(T)$ exceeds the strike price $K$; otherwise, they will simply walk away. Therefore, the intrinsic expected value $E[C]$ (the fair price to pay upfront) is defined by discounting the expected payoff with the risk-free interest rate $r$:

$$
E[C] = e^{-rT} E[\max\{0, S(T) - K\}]
$$

### 블랙-숄즈 공식 (The Black-Scholes Formula)
**[KR]** 위의 기댓값 수식을 로그정규 분포의 적분을 통해 완벽하게 풀어낸 결과물이 바로 노벨 경제학상을 수상한 그 유명한 **블랙-숄즈 공식**입니다.

**[EN]** The result of perfectly solving the expected value equation above through the integration of the lognormal distribution is the world-famous, Nobel Prize-winning **Black-Scholes Formula**.

$$
E[C] = S(0)\Phi(b + \sigma\sqrt{T}) - K e^{-rT}\Phi(b)
$$

$$
\text{where} \quad b \equiv \frac{rT - \frac{\sigma^2 T}{2} - \ln(K/S(0))}{\sigma\sqrt{T}}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-13 Extensions - Lognormal Distribution-1" src="https://github.com/user-attachments/assets/f7873d19-ed48-41da-9a5a-730245629de9" />
    <img width="1264" height="1635" alt="1-13 Extensions - Lognormal Distribution-2" src="https://github.com/user-attachments/assets/9cb6fee6-fd06-4880-ac92-91eb49cc0318" />
    <img width="1264" height="1635" alt="1-13 Extensions - Lognormal Distribution-3" src="https://github.com/user-attachments/assets/489f3936-da6a-4cf0-9e06-06146e67f1ad" />
  </div>
</details>
