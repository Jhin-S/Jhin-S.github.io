---
title: "2-14 Goodness-of-Fit Tests: Examples"
date: 2026-07-21 21:00:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, goodness-of-fit, chi-squared, geometric-distribution, exponential-distribution]
math: true
---

## 1. 이산형 분포 예제: 기하 분포 (Discrete Example: Geometric Distribution)

**[KR]** 인쇄 회로 기판의 결함 수가 기하 분포 $Geometric(p)$를 따른다는 가설을 검정해 봅니다. 총 $n=70$ 개의 기판을 무작위로 추출하여 표본을 수집하고 각 기판의 결함 수를 관측했습니다. 관측된 결함 빈도는 1개(34번), 2개(18번), 3개(2번), 4개(9번), 5개 이상(7번)으로 집계되었습니다.

**[EN]** Let us test the hypothesis that the number of defects in printed circuit boards follows a Geometric(p) distribution. We collect a random sample of $n=70$ printed boards and observe the number of defects in each. The observed frequencies for the defects were 1 (34 times), 2 (18 times), 3 (2 times), 4 (9 times), and $\ge 5$ (7 times).

**[KR]** 기하 분포의 파라미터 $p$에 대한 최대우도추정량(MLE)을 구하기 위해 우도 함수를 미분하여 식을 풀면 $\hat{p} = 1/\bar{x}$ 가 도출됩니다. 데이터를 대입하여 계산하면 $\hat{p} \approx 0.4762$ 가 됩니다.

**[EN]** By taking the derivative of the likelihood function and solving it to get the maximum likelihood estimator (MLE) for the geometric parameter $p$, we obtain $\hat{p} = 1/\bar{x}$. Calculating this with the data gives $\hat{p} \approx 0.4762$.

**[KR]** MLE의 불변성(Invariance Property)을 활용하여, 각 범주의 기대도수 $E_x = n(1-\hat{p})^{x-1}\hat{p}$ 를 계산합니다. 계산 결과, 결함이 4개인 범주의 기대도수가 $4.79$ 로 5 미만으로 나타났습니다. 카이제곱 검정의 조건을 만족시키기 위해 결함이 4개인 범주와 5개 이상인 범주를 병합하여 $\ge 4$ 라는 하나의 범주로 새롭게 구성합니다. 이렇게 수정된 표의 총 범주 개수는 $k=4$ 개가 됩니다.

**[EN]** By the Invariance Property of MLEs, we calculate the expected number of boards for each category as $E_x = n(1-\hat{p})^{x-1}\hat{p}$. The calculation reveals that the expected frequency for exactly 4 defects is $4.79$, which is less than 5. To satisfy the conditions for the chi-squared test, we combine the cell for 4 defects with the cell for $\ge 5$ defects to create an "improved" table with a new $\ge 4$ category. Thus, the total number of cells we ultimately ended up with is $k=4$.

---

## 2. 이산형 예제 결론 (Discrete Example Conclusion)

**[KR]** 병합된 데이터를 바탕으로 카이제곱 적합도 검정 통계량을 계산하면 $\chi_0^2 = 9.12$ 가 산출됩니다. 

**[EN]** Using the combined data, the calculated chi-squared goodness-of-fit test statistic is $\chi_0^2 = 9.12$.

**[KR]** 범주 개수 $k=4$ 이고 우리가 추정한 미지 파라미터의 수가 $s=1$ 개이므로, 카이제곱 분포의 자유도는 $k - 1 - s = 2$ 가 됩니다. 유의수준 $\alpha = 0.05$ 일 때 해당하는 임계값은 $\chi_{0.05, 2}^2 = 5.99$ 입니다.

**[EN]** With $k=4$ cells and $s=1$ unknown parameter that we had to estimate, the degrees of freedom for the chi-squared distribution is $k - 1 - s = 2$. For a significance level of $\alpha = 0.05$, the critical value is $\chi_{0.05, 2}^2 = 5.99$.

**[KR]** 검정 통계량 $9.12$ 가 임계값 $5.99$ 보다 큽니다. 따라서 귀무가설 $H_0$를 기각하며, 기판의 결함 수는 기하 분포를 따르지 않는다고 결론 내립니다.

**[EN]** Since the test statistic $9.12$ is greater than the critical value $5.99$. Therefore, we reject $H_0$ and conclude that the number of defects probably isn't geometric.

---

## 3. 연속형 분포 예제: 지수 분포 (Continuous Example: Exponential Distribution)

**[KR]** 연속형 분포의 경우, 계산의 편의를 위해 모든 구간이 동일한 확률 $1/k$ 을 가지도록 정의역 구간 $A_i \equiv (a_{i-1}, a_i]$ 의 경계값들을 설정합니다. 이 방법을 적용하면 모든 구간의 기대도수는 $E_i = n/k$ 로 일정해집니다.

**[EN]** For the continuous case, for convenience, we choose the intervals $A_i \equiv (a_{i-1}, a_i]$ to ensure that we have equal-probability intervals of $1/k$. By doing this, we immediately have $E_i = n/k$ for all intervals.

**[KR]** 어떤 도착 간격 시간이 지수 분포 $Exp(\lambda)$를 따르는지 확인하는 적합도 검정을 고려해 보겠습니다. 누적 분포 함수(CDF) $F(a_i) = 1 - e^{-\lambda a_i} = i/k$ 를 정리하면 경계값은 $a_i = -(1/\lambda) \ln(1 - i/k)$ 가 됩니다. 파라미터 $\lambda$를 모르는 상태이므로, MLE인 $\hat{\lambda} = 1/\bar{x}$ 를 사용하여 추정된 경계값 $\hat{a}_i = -\bar{x} \ln(1 - i/k)$ 를 구합니다.

**[EN]** Suppose we are interested in fitting a distribution to see if a series of interarrival times follows $Exp(\lambda)$. By solving the CDF $F(a_i) = 1 - e^{-\lambda a_i} = i/k$, the interval boundaries become $a_i = -(1/\lambda) \ln(1 - i/k)$. Since $\lambda$ is unknown, we use its MLE $\hat{\lambda} = 1/\bar{x}$ to estimate the boundaries as $\hat{a}_i = -\bar{x} \ln(1 - i/k)$.

---

## 4. 연속형 예제 결론 (Continuous Example Conclusion)

**[KR]** 총 $n=100$ 개의 관측치를 $k=10$ 개의 동일 확률 구간으로 나누면 각 구간의 기대도수는 모두 $10$ 이 됩니다. 100개 관측치의 표본 평균이 $\bar{x} = 0.8778$ 로 주어졌을 때, 각 구간에 속하는 실제 빈도 $O_i$ 를 집계하여 검정 통계량을 구하면 $\chi_0^2 = 92.2$ 가 산출됩니다.

**[EN]** We take $n=100$ observations and divide them into $k=10$ equal-probability intervals, so that $E_i = 10$ for all intervals. Suppose the sample mean based on the 100 observations is $\bar{x} = 0.8778$; tallying up the actual frequencies $O_i$ for each interval yields a test statistic of $\chi_0^2 = 92.2$.

**[KR]** 자유도가 $k - 1 - s = 10 - 1 - 1 = 8$ 일 때의 카이제곱 임계값은 $\chi_{\alpha, 8}^2 = 15.51$ 입니다.

**[EN]** The critical value for degrees of freedom $k - 1 - s = 10 - 1 - 1 = 8$ is $\chi_{\alpha, 8}^2 = 15.51$.

**[KR]** 검정 통계량 $92.2$ 가 임계값 $15.51$ 을 확연히 초과하므로 귀무가설 $H_0$를 기각합니다. 즉, 해당 관측치들은 지수 분포를 따르지 않는다는 결론을 내립니다.

**[EN]** Because the test statistic $92.2$ clearly exceeds the critical value $15.51$, we reject $H_0$. The conclusion is that these guys aren't Exponential.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-14 Goodness-of-Fit Tests_ Examples-1" src="https://github.com/user-attachments/assets/b9bf4eb5-535b-491f-bb95-186028ebd0b1" />
    <img width="1264" height="1635" alt="2-14 Goodness-of-Fit Tests_ Examples-2" src="https://github.com/user-attachments/assets/700e0f1a-dc6b-4bd7-b6f7-c387067aa4ab" />
    <img width="1264" height="1635" alt="2-14 Goodness-of-Fit Tests_ Examples-3" src="https://github.com/user-attachments/assets/8d4b28f1-aec9-4407-a6a2-447ae261781b" />
    <img width="1264" height="1635" alt="2-14 Goodness-of-Fit Tests_ Examples-4" src="https://github.com/user-attachments/assets/81b6f0c7-693e-41ce-b632-bca31a9b68a1" />
  </div>
</details>
