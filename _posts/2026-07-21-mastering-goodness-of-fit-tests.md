---
title: "Mastering Goodness-of-Fit Tests"
date: 2026-07-21 21:30:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, goodness-of-fit, chi-squared, geometric-distribution, exponential-distribution]
math: true
---

## 1. 적합도 검정 개요 (Goodness-of-Fit Introduction)

**[KR]** 지금까지 우리는 타당한 분포를 추정하고 관련 파라미터를 구하는 과정을 거쳤습니다. 이제 우리가 사용한 도구들이 얼마나 성공적이었는지 확인하기 위해 정식 검정을 실시하고자 합니다. 즉, 우리가 가설로 세운 분포와 관련 파라미터가 타당한지 검증하는 적합도 검정(Goodness-of-Fit Test)을 수행할 것입니다. 귀무가설은 $H_0$: 데이터 $X$는 확률 질량/밀도 함수 $f(x)$를 따른다 로 설정됩니다.

**[EN]** Up to this point, suppose we have estimated a valid distribution and obtained the relevant parameters. Now, we want to conduct a formal test to see just how successful our tools have been. In other words, we verify whether our hypothesized distribution and relevant parameters are valid by performing a Goodness-of-Fit Test. The null hypothesis is set as $H_0$: Data $X$ follows the probability mass/density function $f(x)$.

---

## 2. 적합도 검정 절차의 5단계 (5-Step Procedure for Goodness-of-Fit Test)

**[KR]** 1단계: 분포 $f(x)$의 정의역을 $k$개의 집합 $A_1, A_2, \dots, A_k$ 로 나눕니다. ($X$가 이산형이면 서로 다른 점들로, 연속형이면 구간들로 나눕니다.)

**[EN]** Step 1: Divide the domain of the distribution $f(x)$ into $k$ sets $A_1, A_2, \dots, A_k$. (If $X$ is discrete, these are distinct points; if continuous, they are intervals.)

**[KR]** 2단계: 각 집합에 속하는 실제 관측값의 개수 $O_i$ 를 집계합니다. 만약 $p_i = P(X \in A_i)$ 라고 하면, $O_i \sim Bin(n, p_i)$ 가 됩니다.

**[EN]** Step 2: Tally the actual number of observations $O_i$ that fall in each set. If we let $p_i = P(X \in A_i)$, then $O_i \sim Bin(n, p_i)$.

**[KR]** 3단계: 귀무가설 $H_0$가 참일 때 각 집합에 떨어질 것으로 예상되는 기대 빈도 $E_i$ 를 $E_i = E[O_i] = n p_i$ 로 계산합니다.

**[EN]** Step 3: Calculate the expected frequency $E_i$ of observations that would fall in each set if $H_0$ were true, which is $E_i = E[O_i] = n p_i$.

**[KR]** 4단계: 실제 관측 빈도 $O_i$와 기대 빈도 $E_i$ 사이의 차이를 바탕으로 카이제곱 적합도 검정 통계량을 산출합니다.

**[EN]** Step 4: Calculate the chi-squared goodness-of-fit test statistic based on the difference between the actual observed frequency $O_i$ and the expected frequency $E_i$.

$$ \chi_0^2 = \sum_{i=1}^k \frac{(O_i - E_i)^2}{E_i} $$


**[KR]** (공식의 이유: 분자는 이론적 기대 빈도와 실제 관측 빈도의 오차를 나타내며, 양수와 음수가 상쇄되는 것을 막고 큰 오차에 더 큰 페널티를 주기 위해 제곱을 합니다. 분모를 $E_i$로 나누는 것은 오차의 절대적 크기가 아닌 비율적(상대적) 크기를 반영하기 위함이며, 마지막으로 모든 구간의 점수를 합산하여 종합적인 통계량을 만듭니다.)

**[EN]** (Reasoning for the formula: The numerator represents the error between the theoretical expected frequency and the actual observed frequency, and it is squared to prevent positive and negative values from canceling out and to give a larger penalty to big errors. Dividing by the denominator $E_i$ reflects the relative (proportional) size of the error rather than the absolute size, and summing them all up gives a comprehensive score.)

**[KR]** 5단계: $\chi_0^2$ 값이 크다는 것은 적합도가 나쁘다는 것을 의미하므로 단측 검정 기각 규칙($\chi_0^2 > \chi_{\alpha, k-1-s}^2$)을 적용하여 $H_0$를 기각합니다. 여기서 $s$는 $f(x)$에서 추정해야 하는 미지의 파라미터 개수입니다. 반대로 $\chi_0^2 \le \chi_{\alpha, k-1-s}^2$ 이면 기각에 실패합니다.

**[EN]** Step 5: A large $\chi_0^2$ value means a bad fit, so we perform a one-sided test and reject $H_0$ if $\chi_0^2 > \chi_{\alpha, k-1-s}^2$. Here, $s$ is the number of unknown parameters that need to be estimated from $f(x)$. Conversely, if $\chi_0^2 \le \chi_{\alpha, k-1-s}^2$, we fail to reject $H_0$.

---

## 3. 참고사항 및 간단한 예제 (Remarks and Baby Example)

**[KR]** 카이제곱 적합도 검정이 잘 작동하려면 모든 $i$에 대해 기대 빈도 $E_i \ge 5$ 가 되도록 구간을 설정해야 하며, 전체 표본 수 $n$은 최소 30 이상이어야 합니다. 만약 자유도 $\nu$ 가 매우 크다면 다음의 근사식을 사용할 수 있습니다 ($Z_\alpha$는 표준정규분포의 상위 분위수입니다).

**[EN]** For the chi-squared goodness-of-fit test to work well, the intervals should be set such that the expected frequency $E_i \ge 5$ for all $i$, and the total sample size $n$ should be at least 30. If the degrees of freedom $\nu$ is very large, the following approximation can be used (where $Z_\alpha$ is the upper quantile of the standard normal distribution).

$$ \chi_{\alpha, \nu}^2 \approx \nu \left[ 1 - \frac{2}{9\nu} + Z_\alpha \sqrt{\frac{2}{9\nu}} \right]^3 $$


**[KR]** 📝 간단한 예제로 유의수준 $\alpha=0.05$ 에서 $n=1000$ 개의 관측값이 균일분포 $Unif(0,1)$ 을 따르는지 검정합니다. 동일한 길이를 가진 5개의 구간으로 나눌 때 각 기대 빈도는 200이 됩니다. 계산된 검정 통계량 $\chi_0^2 = 5.27$ 이 추정 파라미터가 없을 때($s=0$)의 임계값 $\chi_{0.05, 4}^2 = 9.49$ 이하이므로($5.27 \le 9.49$) 귀무가설 기각에 실패합니다.

**[EN]** 📝 As a baby example, we test if $n=1000$ observations follow a uniform distribution $Unif(0,1)$ at significance level $\alpha=0.05$. Dividing into 5 equal-length intervals gives an expected frequency of 200 for each. The calculated test statistic $\chi_0^2 = 5.27$ is less than or equal to the critical value $\chi_{0.05, 4}^2 = 9.49$ (with $s=0$ unknown parameters), so we fail to reject the null hypothesis.

---

## 4. 이산형 분포 적합도 검정 예제 (Discrete Example)

**[KR]** 인쇄회로기판(PCB)의 결함 개수가 기하분포 $Geom(p)$ 를 따른다는 가설을 세웠습니다. 총 $n=70$ 개의 회로기판을 추출하여 관측한 결과, 최대우도 추정량(MLE)을 구하면 $\hat{p} = 0.4965$ 가 됩니다.

**[EN]** We hypothesized that the number of defects in printed circuit boards (PCB) follows a geometric distribution $Geom(p)$. Extracting and observing a total of $n=70$ circuit boards, we find the maximum likelihood estimator (MLE) is $\hat{p} = 0.4965$.

**[KR]** MLE의 불변성에 따라 기대 빈도 $E_x = n(1-\hat{p})^{x-1}\hat{p}$ 를 계산합니다. 이때 특정 결함 개수의 $E_x$가 5 미만으로 떨어지는 구간이 발생하므로(예: 결함 4개의 기대빈도 $4.44 < 5$), 수학적으로 타당하게 작동하도록 마지막 셀들을 병합하여 결함 $\ge 4$ 구간으로 합칩니다. (기하분포는 발생 가능한 결과가 무한대이므로 하나로 묶어주는 것이 맞습니다.)

**[EN]** By the invariance of MLE, we calculate the expected frequencies $E_x = n(1-\hat{p})^{x-1}\hat{p}$. Since some expected frequencies drop below 5 (e.g., $E_4 = 4.44 < 5$), we merge the last cells into a $\ge 4$ category so that the chi-squared goodness-of-fit test works mathematically validly. (Since the geometric distribution has infinitely many possible outcomes, grouping them is theoretically appropriate.)

**[KR]** 병합 후 총 범주 $k=4$, 추정 파라미터 $s=1$ 일 때 통계량을 계산하면 $\chi_0^2 = 7.12$ 가 됩니다. 임계값 $\chi_{0.05, 2}^2 = 5.99$ 와 비교하면 $7.12 > 5.99$ 이므로 귀무가설 $H_0$를 기각합니다.

**[EN]** After merging, with total categories $k=4$ and estimated parameter $s=1$, calculating the statistic gives $\chi_0^2 = 7.12$. Comparing it with the critical value $\chi_{0.05, 2}^2 = 5.99$, since $7.12 > 5.99$, we reject the null hypothesis $H_0$.

---

## 5. 연속형 분포 적합도 검정 예제 (Continuous Example)

**[KR]** 연속형 분포의 경우, 모든 구간이 동일한 확률 $1/k$ 을 갖도록 경계값 $a_i$ 들을 선택합니다. 이렇게 설정하면 모든 구간에 대해 기대 빈도는 $E_i = n/k$ 로 고정됩니다.

**[EN]** For continuous distributions, we select boundaries $a_i$ such that every interval has an equal probability of $1/k$. By doing this, the expected frequency for all intervals becomes fixed at $E_i = n/k$.

**[KR]** 도착 간격 시간(Interarrival times) 데이터가 지수분포 $Exp(\lambda)$ 를 따르는지 알아보고자 합니다. 누적분포함수 $F(a_i) = 1 - e^{-\lambda a_i} = i/k$ 를 대수적으로 풀면 경계값 공식을 얻을 수 있으며, 미지의 파라미터 $\lambda$는 표본 평균의 역수인 MLE $\hat{\lambda} = 1/\bar{x}$ 로 대체하여 구합니다.

**[EN]** Suppose we are interested in whether interarrival times data follow an exponential distribution $Exp(\lambda)$. Solving the cumulative distribution function $F(a_i) = 1 - e^{-\lambda a_i} = i/k$ algebraically gives the boundary formula, and we replace the unknown parameter $\lambda$ with its MLE, which is the inverse of the sample mean ($\hat{\lambda} = 1/\bar{x}$).

**[KR]** 표본 크기 $n=100$, 구간 수 $k=10$, 표본 평균 $\bar{x} = 0.8778$ 일 때 각 기대 빈도는 $E_i = 10$ 이 됩니다. 각 구간별 실제 관측 빈도 $O_i$ 와 비교하여 산출된 검정 통계량은 $\chi_0^2 = 92.2$ 입니다. 

**[EN]** With sample size $n=100$, number of intervals $k=10$, and sample mean $\bar{x} = 0.8778$, each expected frequency is $E_i = 10$. Compared with the actual observed frequencies $O_i$ for each interval, the calculated test statistic is $\chi_0^2 = 92.2$.

**[KR]** 자유도가 $k-1-s = 10-1-1 = 8$ 이므로 임계값은 $\chi_{0.05, 8}^2 = 15.51$ 입니다. 검정 통계량이 임계값보다 훨씬 크므로 ($92.2 > 15.51$) 우리는 귀무가설 $H_0$를 기각하며, 해당 데이터는 지수분포를 따르지 않는다고 결론 내립니다.

**[EN]** Since the degrees of freedom is $k-1-s = 10-1-1 = 8$, the critical value is $\chi_{0.05, 8}^2 = 15.51$. Because the test statistic is much larger than the critical value ($92.2 > 15.51$), we reject the null hypothesis $H_0$ and conclude that the data does not follow an exponential distribution.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Mastering Goodness-of-Fit Tests-1" src="https://github.com/user-attachments/assets/cb8e68ac-50a1-43de-b33d-621aef13eaa3" />
    <img width="1264" height="1635" alt="Mastering Goodness-of-Fit Tests-2" src="https://github.com/user-attachments/assets/ce0ca24d-6735-427a-bda8-ff626bb81780" />
    <img width="1264" height="1635" alt="Mastering Goodness-of-Fit Tests-3" src="https://github.com/user-attachments/assets/c665e18a-98db-4b19-af1f-c82973fe61dd" />
    <img width="1264" height="1635" alt="Mastering Goodness-of-Fit Tests-4" src="https://github.com/user-attachments/assets/621e7f46-f7fa-4afe-99b2-7ac96d4c3766" />
    <img width="1264" height="1635" alt="Mastering Goodness-of-Fit Tests-5" src="https://github.com/user-attachments/assets/ed28106c-54e6-4918-b9ba-5a7d778d2036" />
    <img width="1264" height="1635" alt="Mastering Goodness-of-Fit Tests-6" src="https://github.com/user-attachments/assets/5e60473a-1650-486d-96e3-1b27a3a9c30b" />
  </div>
</details>
