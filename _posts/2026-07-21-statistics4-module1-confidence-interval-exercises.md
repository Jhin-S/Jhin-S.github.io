---
title: "Statistics4 Module1 Confidence Interval Exercises"
date: 2026-07-21 21:34:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, confidence-interval, normal-distribution, t-distribution, f-distribution, chi-squared, bernoulli]
math: true
---

## 1. 정규 모평균 (Normal Mean)

### [문제 1] 신뢰구간 계산 (Confidence Interval Calculation)
**[KR]** 어느 공장에서 생산되는 제품의 무게는 표준편차($\sigma$)가 $10\text{g}$인 정규분포를 따른다고 합니다. 이 공장에서 제품 $25$개를 임의 추출하여 평균 무게를 측정했더니 $\bar{X}=200\text{g}$ 이었습니다. $95\%$ 신뢰수준에서의 모평균 $\mu$에 대한 신뢰구간을 구하세요. (단, $z_{0.025}=1.96$ 으로 계산하며, 최종 답안은 $\mu$의 범위를 소수점 둘째 자리까지 정확히 표기하세요.)

**[EN]** The weight of products produced in a factory follows a normal distribution with a standard deviation ($\sigma$) of $10\text{g}$. A random sample of $25$ products was taken, and the sample mean weight was $\bar{X}=200\text{g}$. Find the $95\%$ confidence interval for the population mean $\mu$. (Use $z_{0.025}=1.96$ and express the final answer for the range of $\mu$ precisely to two decimal places.)

**[풀이 / Solution]**
오차한계(Half-width) $H$ 계산:
$$ H = z_{\alpha/2}\sqrt{\frac{\sigma^2}{n}} = 1.96\sqrt{\frac{100}{25}} = 3.92 $$

**Answer:** $\mu \in [200 - 3.92, 200 + 3.92]$ 즉, $196.08 \le \mu \le 203.92$

---

### [문제 2] 표본 크기(n) 계산 (Sample Size Calculation)
**[KR]** 표준편차($\sigma$)가 $20$인 정규분포를 따르는 모집단에서 모평균을 추정하려고 합니다. $95\%$ 신뢰수준에서 오차한계(half-width, $H$)를 $4$ 이하로 유지하기 위해 필요한 최소 표본의 크기 $n$은 얼마인지 구하세요. (단, $z_{0.025}=1.96$ 으로 계산하며, 결과값이 소수점일 경우 반올림하여 정수로 답하세요.)

**[EN]** We want to estimate the population mean from a normal distribution with a standard deviation ($\sigma$) of $20$. Find the minimum sample size $n$ required to keep the half-width ($H$) at $4$ or less at a $95\%$ confidence level. (Use $z_{0.025}=1.96$ and round up to the nearest integer if the result is a decimal.)

**[풀이 / Solution]**
$H \le 4$ 가 되어야 하므로,
$$ n \ge \left(\frac{20 \cdot 1.96}{4}\right)^2 = 96.04 $$

**Answer:** 최소 표본 크기(Minimum sample size)는 $n=97$ 이다.

<br>

---

## 2. 두 정규 모평균의 차이 (분산 앎) (Difference of Two Normal Means - Variance Known)

### [문제 1] 두 집단의 평균 차이 신뢰구간 계산 (CI for Difference of Two Means)
**[KR]** 어느 대학의 두 학과(A학과, B학과) 학생들의 전공 시험 점수 차이를 비교하려고 합니다. 두 학과의 점수는 정규분포를 따르며, 표준편차는 각각 $\sigma_A=10$ 점, $\sigma_B=12$ 점으로 알려져 있습니다. 다음과 같은 표본 데이터를 얻었을 때, 두 학과의 평균 점수 차이($\mu_A - \mu_B$)에 대한 $95\%$ 신뢰구간을 구하세요. 
(A학과: $n=25, \bar{x}=85$ / B학과: $m=36, \bar{y}=75$ / $z_{0.025}=1.96$ / 답안 형식: $L \le \mu_A - \mu_B \le U$ 소수점 둘째 자리까지)

**[EN]** We want to compare the difference in major exam scores between students from two departments (Dept A and Dept B). The scores follow normal distributions with known standard deviations $\sigma_A=10$ and $\sigma_B=12$. Given the following sample data, find the $95\%$ confidence interval for the mean score difference ($\mu_A - \mu_B$).
(Dept A: $n=25, \bar{x}=85$ / Dept B: $m=36, \bar{y}=75$ / $z_{0.025}=1.96$)

**[풀이 / Solution]**
$$ \bar{x} - \bar{y} = 10 $$

$$ H = z_{\alpha/2}\sqrt{\frac{\sigma_A^2}{n} + \frac{\sigma_B^2}{m}} = 1.96\sqrt{\frac{10^2}{25} + \frac{12^2}{36}} = 5.54 $$

**Answer:** $4.46 \le \mu_A - \mu_B \le 15.54$

---

### [문제 2] 동일한 표본 크기 설정 (Determining Equal Sample Size)
**[KR]** 두 공정에서 생산되는 제품의 강도 차이를 조사하고자 합니다. 각 공정의 분산은 $\sigma_x^2=40$, $\sigma_y^2=60$ 으로 알려져 있습니다. 두 집단의 표본 크기를 동일하게 설정($n=m$)할 때, $95\%$ 신뢰수준에서 신뢰구간의 반폭(half-width)을 $4$ 이하로 만들기 위해 필요한 최소 표본 크기 $n$은 얼마인지 구하세요 ($z_{0.025}=1.96$, 올림하여 정수로 표기).

**[EN]** We want to investigate the difference in strength of products produced in two processes. The variances are known to be $\sigma_x^2=40$ and $\sigma_y^2=60$. When setting the sample sizes equally ($n=m$), find the minimum sample size $n$ required to make the half-width of the $95\%$ confidence interval $4$ or less.

**[풀이 / Solution]**
$$ n = \frac{z_{\alpha/2}^2 (\sigma_x^2 + \sigma_y^2)}{H^2} = \frac{1.96^2 (40 + 60)}{4^2} = 24.01 $$

**Answer:** 최소 표본 크기(Minimum sample size) $n=25$

<br>

---

## 3. 소표본의 모평균 (Small Sample Normal Mean)

### [문제 1] 소표본의 모평균 신뢰구간 계산 (CI for Small Sample Mean)
**[KR]** 새로운 사료를 먹인 돼지 $16$마리의 무게를 측정하였습니다. 측정 결과 표본 평균은 $\bar{x} = 120\text{kg}$ 이었고, 표본 표준편차는 $S = 8\text{kg}$ 이었습니다. 돼지의 무게가 정규분포를 따른다고 가정할 때, 모평균($\mu$)에 대한 $95\%$ 신뢰구간을 구하세요 ($n=16, t_{0.025, 15}=2.131$, 소수점 셋째 자리까지).

**[EN]** The weights of $16$ pigs fed a new feed were measured. The sample mean was $\bar{x} = 120\text{kg}$ and the sample standard deviation was $S = 8\text{kg}$. Assuming the weights follow a normal distribution, find the $95\%$ confidence interval for the population mean ($\mu$).

**[풀이 / Solution]**
$$ \bar{x} \pm t_{0.025, 15}\frac{S}{\sqrt{n}} = 120 \pm 2.131\frac{8}{\sqrt{16}} = 120 \pm 4.262 $$

**Answer:** $115.738 \le \mu \le 124.262$

---

### [문제 2] t-분포를 이용한 오차한계 계산 (Half-width Calculation using t-distribution)
**[KR]** 어느 전구 제조사에서 생산된 전구 $9$개의 수명을 조사한 결과, 표본 표준편차가 $S = 150$ 시간으로 나타났습니다. $99\%$ 신뢰수준에서 모평균을 추정할 때, 이 신뢰구간의 오차한계($H$)를 구하세요 ($n=9, t_{0.005, 8}=3.355$, 소수점 첫째 자리까지).

**[EN]** A life test of $9$ lightbulbs produced by a manufacturer showed a sample standard deviation of $S = 150$ hours. Calculate the half-width ($H$) of the confidence interval when estimating the population mean at a $99\%$ confidence level.

**[풀이 / Solution]**
$$ H = t_{0.005, 8}\frac{S}{\sqrt{n}} = 3.355 \times \frac{150}{\sqrt{9}} = 167.75 $$

**Answer:** $167.8$

<br>

---

## 4. 두 정규 모평균의 차이 (분산 모름, 동일 가정) (Difference of Two Normal Means - Unknown Equal Variances)

### [문제 1] 합동분산 계산 (Pooled Variance Calculation)
**[KR]** 두 집단 X, Y의 정보가 다음과 같을 때 합동분산 $S_p^2$ 를 구하세요 (소수점 둘째 자리에서 반올림).
(집단 X: $n=10, S_x^2=12$ / 집단 Y: $m=10, S_y^2=18$)

**[EN]** Calculate the pooled variance $S_p^2$ given the following information for two groups X and Y.
(Group X: $n=10, S_x^2=12$ / Group Y: $m=10, S_y^2=18$)

**[풀이 / Solution]**
$$ S_p^2 = \frac{(n-1)S_x^2 + (m-1)S_y^2}{n+m-2} = \frac{9 \cdot 12 + 9 \cdot 18}{18} = 15 $$

**Answer:** $15$

---

### [문제 2] 두 평균 차이의 신뢰구간 하한 계산 (Lower Bound of CI)
**[KR]** 두 제품 A, B의 분산이 동일하다고 가정하고 수명을 비교합니다. ($\bar{X}=50, \bar{Y}=40, S_p=6, t_{0.025, 30}=2.04$). 평균 차이($\mu_x - \mu_y$)에 대한 $95\%$ 신뢰구간의 하한값을 구하세요.

**[EN]** Compare the lifespan of two products A and B assuming equal variances. Calculate the lower bound of the $95\%$ confidence interval for the mean difference ($\mu_x - \mu_y$).

**[풀이 / Solution]**
$$ \text{Lower bound} = \bar{X} - \bar{Y} - t_{\alpha/2, n+m-2}S_p\sqrt{\frac{1}{n} + \frac{1}{m}} = 50 - 40 - 2.04 \times 6 \times \sqrt{\frac{1}{16} + \frac{1}{16}} = 3.88 $$

**Answer:** $3.88$

<br>

---

## 5. 두 정규 모평균의 차이 (분산 모름, 다름 가정) (Difference of Two Normal Means - Variance Unknown & Unequal)

### [문제 1] 표준오차 계산 (Standard Error Calculation)
**[KR]** 두 모평균 차이 추정에 사용되는 표준오차 $SE = \sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}$ 의 값을 구하세요.
(집단 X: $n=25, S_x^2=400$ / 집단 Y: $m=16, S_y^2=100$)

**[EN]** Calculate the standard error $SE = \sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}$ used for estimating the difference between two population means.

**[풀이 / Solution]**
$$ SE = \sqrt{\frac{400}{25} + \frac{100}{16}} = 4.717 $$

**Answer:** $4.717$

---

### [문제 2] 평균 차이 신뢰구간 상한 계산 (Upper Bound of CI)
**[KR]** 라인 A($\bar{X}=100$), 라인 B($\bar{Y}=80$), $SE=4.717$, $t_{0.025, \nu}=2.026$ 일 때 두 집단 평균 차이의 $95\%$ 상한값을 구하세요.

**[EN]** Calculate the upper bound of the $95\%$ CI for the mean difference given $\bar{X}=100, \bar{Y}=80, SE=4.717$, and $t_{0.025, \nu}=2.026$.

**[풀이 / Solution]**
$$ H = 2.026 \times 4.717 = 9.557 $$

$$ \text{Upper bound} = 100 - 80 + 9.557 = 29.557 $$

**Answer:** $29.56$

<br>

---

## 6. 대응표본의 모평균 차이 (Difference of Paired Normal Means)

### [문제 1] 오차한계 계산 (Half-width Calculation)
**[KR]** 동일한 5명($n=5$)의 운동 전후 심박수 차이($D_i$)가 $4, 6, 2, 8, 5$ 입니다 ($S_d = 2.236$, $t_{0.025, 4}=2.776$). 평균 차이 신뢰구간의 오차한계를 구하세요.

**[EN]** Calculate the half-width for the CI of the mean difference for $5$ subjects whose before-and-after heart rate differences are $4, 6, 2, 8, 5$.

**[풀이 / Solution]**
$$ H = t_{\alpha/2, n-1}\sqrt{\frac{S_d^2}{n}} = 2.776\sqrt{\frac{5}{5}} = 2.776 $$

**Answer:** $2.78$

---

### [문제 2] 대응표본 하한 계산 (Lower Bound of Paired CI)
**[KR]** 5명이 두 차량의 평점을 부여한 차이 평균이 $\bar{D} = -9$, 분산 $S_d^2 = 42.5$ 입니다 ($t_{0.05, 4}=2.13$). 평균 평점 차이에 대한 $90\%$ 신뢰구간의 하한을 구하세요.

**[EN]** 5 drivers rated two cars with a mean difference $\bar{D} = -9$ and variance $S_d^2 = 42.5$. Find the lower bound of the $90\%$ CI for the mean rating difference.

**[풀이 / Solution]**
$$ H = 2.13 \times \sqrt{\frac{42.5}{5}} = 6.21 $$

$$ \text{Lower bound} = -9 - 6.21 = -15.21 $$

**Answer:** $-15.21$

<br>

---

## 7. 정규 분산 (Normal Variance)

### [문제 1] 모분산 상한 신뢰구간 계산 (Upper Confidence Interval of Variance)
**[KR]** $n=25, S^2=100, \chi_{0.95, 24}^2=13.85$ 일 때 모분산 $\sigma^2$ 의 $95\%$ 상한값을 구하세요.
**[EN]** Calculate the upper bound of the $95\%$ CI for the population variance given $n=25, S^2=100, \chi_{0.95, 24}^2=13.85$.

**[풀이 / Solution]**
$$ \frac{(n-1)S^2}{\chi_{0.95, 24}^2} = \frac{24 \cdot 100}{13.85} = 173.285 $$

**Answer:** $173.3$

---

### [문제 2] 모분산 양측 신뢰구간 하한 계산 (Lower Bound of Variance CI)
**[KR]** $n=11, S^2=40, \chi_{0.025, 10}^2=20.48$ 일 때 모분산의 $95\%$ 신뢰구간 하한을 구하세요.
**[EN]** Calculate the lower bound of the $95\%$ CI for the variance given $n=11, S^2=40, \chi_{0.025, 10}^2=20.48$.

**[풀이 / Solution]**
$$ \frac{(n-1)S^2}{\chi_{0.025, 10}^2} = \frac{10 \cdot 40}{20.48} = 19.53 $$

**Answer:** $19.53$

<br>

---

## 8. 두 정규 분산의 비율 (Ratio of Variances of Two Normals)

### [문제 1] 두 분산 비율 상한 계산 (Upper Bound of Variance Ratio CI)
**[KR]** 검사 A($n=25, S_A^2=100$)와 검사 B($m=16, S_B^2=70$)의 분산 비율($\sigma_A^2/\sigma_B^2$)에 대한 $95\%$ 상한 신뢰구간을 구하세요 ($F_{0.05, 15, 24}=2.11$).
**[EN]** Calculate the upper bound of the $95\%$ CI for the variance ratio ($\sigma_A^2/\sigma_B^2$) of Test A and Test B.

**[풀이 / Solution]**
$$ \frac{S_x^2}{S_y^2} F_{0.05, m-1, n-1} = \frac{100}{70} \times 2.11 = 3.01 $$

**Answer:** $3.01$

---

### [문제 2] 두 분산 비율 하한 계산 (Lower Bound of Variance Ratio CI)
**[KR]** 공정 X($n=10, S_x^2=18$)와 공정 Y($m=10, S_y^2=6$)의 분산 비율 하한값을 구하세요 ($F_{0.05, 9, 9}=3.18$).
**[EN]** Calculate the lower bound of the $95\%$ CI for the variance ratio of Process X and Y.

**[풀이 / Solution]**
$$ \frac{S_x^2}{S_y^2} \frac{1}{F_{0.05, n-1, m-1}} = \frac{18}{6} \times \frac{1}{3.18} = 0.94 $$

**Answer:** $0.94$

<br>

---

## 9. 베르누이 비율 (Bernoulli Proportion)

### [문제 1] 오차한계 계산 (Half-width of Proportion CI)
**[KR]** 200명 중 160명이 정답을 맞혔습니다($\bar{X}=0.8$). 성공 확률 $p$에 대한 $95\%$ 신뢰구간의 오차한계를 구하세요 ($z_{0.025}=1.96$).
**[EN]** 160 out of 200 students answered correctly ($\bar{X}=0.8$). Calculate the half-width of the $95\%$ CI for the success probability $p$.

**[풀이 / Solution]**
$$ H = 1.96\sqrt{\frac{(0.8)(0.2)}{200}} = 0.055 $$

**Answer:** $0.055$

---

### [문제 2] 표본 크기 계산 (Sample Size for Proportion)
**[KR]** 오차한계가 $\pm 3\% (\epsilon=0.03)$ 이내가 되기 위한 최소 표본 크기 $n$을 보수적인 공식($n \ge \frac{z_{\alpha/2}^2}{4\epsilon^2}$)으로 구하세요.
**[EN]** Calculate the minimum sample size $n$ required to achieve an error margin of $\pm 3\%$ using the most conservative formula.

**[풀이 / Solution]**
$$ n \ge \frac{(1.96)^2}{4(0.03)^2} = 1067.11... $$

**Answer:** $n=1068$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-1" src="https://github.com/user-attachments/assets/c1a7c301-7b71-4e12-922a-b29751f43602" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-2" src="https://github.com/user-attachments/assets/5c3e3802-0eb9-49df-816b-7ec736bb0e40" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-3" src="https://github.com/user-attachments/assets/05f03c5f-01cf-4499-8019-c59f6077ad17" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-4" src="https://github.com/user-attachments/assets/fec0080b-167c-4f53-bcfb-660c03979d60" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-5" src="https://github.com/user-attachments/assets/3a3b976f-e4c8-4a1c-add3-b7d70b8e8bb4" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-6" src="https://github.com/user-attachments/assets/b1321582-1e9e-4c59-8716-a019e5276ae7" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-7" src="https://github.com/user-attachments/assets/a43f55b4-19bb-43e8-a1f1-e946f1d2c6af" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-8" src="https://github.com/user-attachments/assets/da1790f4-587e-49a4-850a-e54f45ac5538" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Confidence Interval Exercises-9" src="https://github.com/user-attachments/assets/3b73f76e-d216-4d76-bfdc-d853b5c964f5" />
  </div>
</details>
