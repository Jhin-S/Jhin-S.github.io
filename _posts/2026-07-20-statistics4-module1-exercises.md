---
title: "Statistics4 Module1 Exercises"
date: 2026-07-20 12:32:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, confidence-interval, normal-distribution, exercises, solutions]
math: true
---

이번 포스팅에서는 Gemini를 활용해 신뢰구간(Confidence Interval) 관련 연습문제를 직접 생성하고 풀어보았습니다.

이번 문제들은 공식에 값을 대입하기만 하면 되는 비교적 간단한 계산 위주로 구성되어 있습니다. 하지만 신뢰구간의 핵심은 단순히 계산을 해내는 데 있지 않습니다. 점추정량이 아닌 '확률변수'를 이용해, 해당 확률변수가 따르는 분포에 비추어 보았을 때 현재 관측된 값이 몇 퍼센트의 확률로 '그럴싸한지'를 이해하는 과정이 훨씬 중요합니다.
추후에 다룰 것이지만 가설검증 역시 "참이라고 가정했을 때 현재 관측된 값으로 계산된 확률변수(검정통계량이라 부릅니다)가 얼마나 그럴싸한지를 보는 것이 핵심입니다."

## 1-2. Normal Mean (정규 분포의 평균)

### [문제 1] 신뢰 구간 계산 / Confidence Interval Calculation
**[KR]** 어느 공장에서 생산되는 제품의 무게는 표준편차($\sigma$)가 10g인 정규 분포를 따른다고 합니다. 25개의 제품을 추출하여 평균을 측정한 결과 200g이었습니다. 95% 신뢰 수준에서 모평균 $\mu$의 신뢰 구간을 소수점 둘째 자리까지 구하세요 ($z_{0.025}=1.96$).
**[EN]** The weight of a product manufactured in a factory follows a normal distribution with a standard deviation ($\sigma$) of 10g. A sample of 25 products was taken, yielding a sample mean of 200g. Find the 95% confidence interval for the population mean $\mu$ to two decimal places ($z_{0.025}=1.96$).

**[KR] 풀이:** 오차 한계 공식을 적용하면 $H = 1.96 \sqrt{100/25} = 3.92$ 이므로, 정답은 $200 \pm 3.92$ 입니다.
**[EN] Solution:** Applying the margin of error formula, $H = 1.96 \sqrt{100/25} = 3.92$, so the answer is $200 \pm 3.92$.

### [문제 2] 표본 크기 계산 / Sample Size Calculation
**[KR]** $\sigma = 20$ 인 정규 모집단에서 모평균을 추정할 때, 95% 신뢰 수준에서 오차 한계를 4 이하로 유지하기 위한 최소 표본 크기 $n$을 구하세요 ($z_{0.025}=1.96$).
**[EN]** When estimating the population mean from a normal population with $\sigma = 20$, find the minimum sample size $n$ required to keep the margin of error at 4 or less at a 95% confidence level ($z_{0.025}=1.96$).

**[KR] 풀이:** 공식에 대입하면 $n \ge (20 \cdot 1.96 / 4)^2 = 96.04$ 이므로 최소 표본 크기는 97입니다.
**[EN] Solution:** Substituting the values, $n \ge (20 \cdot 1.96 / 4)^2 = 96.04$, meaning the minimum sample size is 97.

---

## 1-3. Difference of Two Normal Means (Variance Known)

### [문제 1] 두 집단의 평균 차이 신뢰 구간 / CI for Difference of Two Means
**[KR]** A학과($n=25, \bar{X}=85, \sigma_A=10$)와 B학과($m=36, \bar{Y}=75, \sigma_B=12$) 학생들의 전공 시험 점수 평균 차이($\mu_A - \mu_B$)에 대한 95% 신뢰 구간을 구하세요.
**[EN]** Find the 95% confidence interval for the difference in average major exam scores ($\mu_A - \mu_B$) between Dept A ($n=25, \bar{X}=85, \sigma_A=10$) and Dept B ($m=36, \bar{Y}=75, \sigma_B=12$).

**[KR] 풀이:** $\bar{X} - \bar{Y} = 10$ 이고, 오차 한계 $H = 1.96 \sqrt{10^2/25 + 12^2/36} \approx 5.54$ 이므로 $4.46 \le \mu_A - \mu_B \le 15.54$ 입니다.
**[EN] Solution:** The mean difference is 10, and the margin of error is $H = 1.96 \sqrt{10^2/25 + 12^2/36} \approx 5.54$, resulting in $4.46 \le \mu_A - \mu_B \le 15.54$.

### [문제 2] 동일한 표본 크기 결정 / Equal Sample Size Determination
**[KR]** 두 공정의 분산이 $\sigma_x^2=40, \sigma_y^2=60$ 이고 동일한 표본 크기 $n=m$을 사용할 때, 95% 신뢰 수준의 오차 한계를 4 이하로 만들기 위한 최소 표본 크기 $n$을 구하세요.
**[EN]** Given variances $\sigma_x^2=40$ and $\sigma_y^2=60$, and using an equal sample size $n=m$, find the minimum $n$ required to make the margin of error 4 or less at a 95% confidence level.

**[KR] 풀이:** $n = 1.96^2(40+60)/4^2 = 24.01$ 이므로 정답은 25입니다.
**[EN] Solution:** $n = 1.96^2(40+60)/4^2 = 24.01$, so the required sample size is 25.

---

## 1-4. Normal Mean (Variance Unknown)

### [문제 1] 소표본의 모평균 신뢰 구간 / Small Sample CI for Mean
**[KR]** 표본 크기 $n=16$, 표본 평균 120kg, 표본 표준편차 8kg 일 때 모평균의 95% 신뢰 구간을 구하세요 ($t_{0.025, 15}=2.131$).
**[EN]** Find the 95% confidence interval for the population mean given a sample size $n=16$, sample mean 120kg, and sample standard deviation 8kg ($t_{0.025, 15}=2.131$).

**[KR] 풀이:** t-분포를 사용한 오차 한계 $H = 2.131 \sqrt{64/16} = 4.262$ 이므로 정답은 $120 \pm 4.262$ 입니다.
**[EN] Solution:** Using the t-distribution margin of error, $H = 2.131 \sqrt{64/16} = 4.262$, yielding $120 \pm 4.262$.

### [문제 2] t-분포 오차 한계 계산 / t-distribution Margin of Error
**[KR]** 표본 크기 $n=9$, 표본 표준편차 150시간일 때 99% 신뢰 수준의 오차 한계를 구하세요 ($t_{0.005, 8}=3.355$).
**[EN]** Find the margin of error at a 99% confidence level for a sample size $n=9$ and sample standard deviation of 150 hours ($t_{0.005, 8}=3.355$).

**[KR] 풀이:** $H = 3.355 \sqrt{150^2/9} = 167.75 \approx 167.8$ 입니다.
**[EN] Solution:** $H = 3.355 \sqrt{150^2/9} = 167.75 \approx 167.8$.

---

## 1-5. Difference of Two Normal Means (Equal Variances)

### [문제 1] 합동 분산 계산 / Pooled Variance Calculation
**[KR]** 두 모집단의 분산이 동일하다고 가정할 때, 집단 X($n=10, S_x^2=12$)와 집단 Y($m=10, S_y^2=18$)의 합동 분산 $S_p^2$를 구하세요.
**[EN]** Assuming equal population variances, find the pooled variance $S_p^2$ for Group X ($n=10, S_x^2=12$) and Group Y ($m=10, S_y^2=18$).

**[KR] 풀이:** $S_p^2 = (9 \cdot 12 + 9 \cdot 18) / 18 = 15$ 입니다.
**[EN] Solution:** $S_p^2 = (9 \cdot 12 + 9 \cdot 18) / 18 = 15$.

### [문제 2] 평균 차이 신뢰 구간 하한 / Lower Bound of Mean Difference
**[KR]** 두 제품 A($n=16, \bar{X}=50$)와 B($m=16, \bar{Y}=40$)의 합동 표준편차가 $S_p=6$ 일 때, 평균 차이에 대한 95% 신뢰 구간 하한을 구하세요 ($t_{0.025, 30}=2.04$).
**[EN]** With a pooled standard deviation $S_p=6$ for products A ($n=16, \bar{X}=50$) and B ($m=16, \bar{Y}=40$), find the lower bound of the 95% CI for the difference in means ($t_{0.025, 30}=2.04$).

**[KR] 풀이:** 하한은 $50 - 40 - 2.04 \cdot 6 \sqrt{1/16 + 1/16} = 3.88$ 입니다.
**[EN] Solution:** The lower bound is $50 - 40 - 2.04 \cdot 6 \sqrt{1/16 + 1/16} = 3.88$.

---

## 1-6. Difference of Two Normal Means (Variance Unknown)

### [문제 1] 표준 오차 계산 / Standard Error Calculation
**[KR]** 두 집단 X($n=25, S_x^2=400$)와 Y($m=16, S_y^2=100$)의 모평균 차이 추정에 사용되는 표준 오차(SE)를 구하세요.
**[EN]** Calculate the Standard Error (SE) used to estimate the difference in population means for groups X ($n=25, S_x^2=400$) and Y ($m=16, S_y^2=100$).

**[KR] 풀이:** $SE = \sqrt{400/25 + 100/16} = 4.717$ 입니다.
**[EN] Solution:** $SE = \sqrt{400/25 + 100/16} = 4.717$.

### [문제 2] 평균 차이 신뢰 구간 상한 / Upper Bound of Mean Difference
**[KR]** 분산이 다른 두 라인 A($\bar{X}=100$)와 B($\bar{Y}=80$)의 평균 차이에 대한 95% 신뢰 구간 상한을 구하세요 (표준 오차 $4.717$, $t_{0.025, \nu}=2.026$).
**[EN]** Find the upper bound of the 95% CI for the mean difference between Line A ($\bar{X}=100$) and Line B ($\bar{Y}=80$) assuming unequal variances (SE = 4.717, $t_{0.025, \nu}=2.026$).

**[KR] 풀이:** 오차 한계는 $2.026 \cdot 4.717 = 9.557$ 이며, 상한은 $20 + 9.557 = 29.56$ 입니다.
**[EN] Solution:** The margin of error is $2.026 \cdot 4.717 = 9.557$, so the upper bound is $20 + 9.557 = 29.56$.

---

## 1-7. Difference of Paired Normal Means

### [문제 1] 차이의 표본 평균과 오차 한계 / Sample Mean Difference and Margin of Error
**[KR]** 5명의 운동 전후 심박수 차이 평균 신뢰 구간을 위한 오차 한계를 구하세요 ($S_d = 2.236$, $t_{0.025, 4}=2.776$).
**[EN]** Calculate the margin of error for the CI of the mean difference in heart rates before and after exercise for 5 participants ($S_d = 2.236$, $t_{0.025, 4}=2.776$).

**[KR] 풀이:** $H = 2.776 \sqrt{5/5} = 2.776 \approx 2.78$ 입니다.
**[EN] Solution:** $H = 2.776 \sqrt{5/5} = 2.776 \approx 2.78$.

### [문제 2] 대응 표본 t-신뢰 구간 하한 / Lower Bound of Paired t-Interval
**[KR]** 두 차량 평점 차이($\bar{D}=-9, S_d^2=42.5, n=5$)에 대한 90% 신뢰 구간 하한을 구하세요 ($t_{0.05, 4}=2.13$).
**[EN]** Find the lower bound of the 90% CI for the rating difference between two cars ($\bar{D}=-9, S_d^2=42.5, n=5$) using $t_{0.05, 4}=2.13$.

**[KR] 풀이:** $H = 2.13 \sqrt{42.5/5} = 6.21$ 이며, 하한은 $-9 - 6.21 = -15.21$ 입니다.
**[EN] Solution:** $H = 2.13 \sqrt{42.5/5} = 6.21$, and the lower bound is $-9 - 6.21 = -15.21$.

---

## 1-8. Normal Variance

### [문제 1] 모분산 신뢰 구간 상한 / Upper Bound for Variance CI
**[KR]** 표본 크기 $n=25$, 표본 분산 $S^2=100$ 일 때, 모분산에 대한 95% 단측 상한 신뢰 구간의 상한값을 구하세요 ($\chi^2_{0.95, 24}=13.85$).
**[EN]** Given sample size $n=25$ and sample variance $S^2=100$, find the upper limit of the 95% one-sided upper CI for the population variance ($\chi^2_{0.95, 24}=13.85$).

**[KR] 풀이:** $\sigma^2 \le (24 \cdot 100) / 13.85 = 173.285 \approx 173.3$ 입니다.
**[EN] Solution:** $\sigma^2 \le (24 \cdot 100) / 13.85 = 173.285 \approx 173.3$.

### [문제 2] 모분산 양측 신뢰 구간 하한 / Lower Bound for Two-sided Variance CI
**[KR]** $n=11$, $S^2=40$ 일 때 모분산 95% 양측 신뢰 구간의 하한값을 구하세요 ($\chi^2_{0.025, 10}=20.48$).
**[EN]** For $n=11$ and $S^2=40$, find the lower bound of the 95% two-sided CI for the population variance ($\chi^2_{0.025, 10}=20.48$).

**[KR] 풀이:** $(10 \cdot 40) / 20.48 = 19.53$ 입니다.
**[EN] Solution:** $(10 \cdot 40) / 20.48 = 19.53$.

---

## 1-9. Ratio of Variance of Two Normals

### [문제 1] 두 분산 비율의 상한 / Upper Bound of Variance Ratio
**[KR]** 검사 A($n=25, S_A^2=100$)와 검사 B($m=16, S_B^2=70$)의 분산 비율 $\sigma_A^2/\sigma_B^2$ 에 대한 95% 상한 신뢰 구간의 상한값을 구하세요 ($F_{0.05, 15, 24}=2.11$).
**[EN]** Find the upper limit of the 95% one-sided upper CI for the variance ratio $\sigma_A^2/\sigma_B^2$ of Test A ($n=25, S_A^2=100$) and Test B ($m=16, S_B^2=70$) using $F_{0.05, 15, 24}=2.11$.

**[KR] 풀이:** $(100/70) \cdot 2.11 = 3.01$ 입니다.
**[EN] Solution:** $(100/70) \cdot 2.11 = 3.01$.

### [문제 2] 두 분산 비율의 하한 / Lower Bound of Variance Ratio
**[KR]** 공정 X($n=10, S_x^2=18$)와 공정 Y($m=10, S_y^2=6$)의 분산 비율 $\sigma_x^2/\sigma_y^2$ 에 대한 95% 하한 신뢰 구간의 하한값을 구하세요 ($F_{0.05, 9, 9}=3.18$).
**[EN]** Find the lower limit of the 95% one-sided lower CI for the variance ratio $\sigma_x^2/\sigma_y^2$ of Process X ($n=10, S_x^2=18$) and Process Y ($m=10, S_y^2=6$) using $F_{0.05, 9, 9}=3.18$.

**[KR] 풀이:** $(18/6) \cdot (1/3.18) = 0.94$ 입니다.
**[EN] Solution:** $(18/6) \cdot (1/3.18) = 0.94$.

---

## 1-10. Bernoulli Proportion

### [문제 1] 성공 비율 오차 한계 / Margin of Error for Success Proportion
**[KR]** 200명 중 160명이 정답을 맞혔을 때($\bar{X}=0.8$), 성공 확률 $p$의 95% 신뢰 구간 오차 한계를 구하세요 ($z_{0.025}=1.96$).
**[EN]** With 160 correct answers out of 200 ($\bar{X}=0.8$), calculate the margin of error for the 95% CI of the success probability $p$ ($z_{0.025}=1.96$).

**[KR] 풀이:** $H = 1.96 \sqrt{(0.8 \cdot 0.2) / 200} = 0.055$ 입니다.
**[EN] Solution:** $H = 1.96 \sqrt{(0.8 \cdot 0.2) / 200} = 0.055$.

### [문제 2] 최소 표본 크기 계산 / Minimum Sample Size Calculation
**[KR]** 성공 비율 $p$ 추정 시 오차 한계 3% 이하를 위한 보수적인 최소 표본 크기 $n$을 구하세요 ($z_{0.025}=1.96$).
**[EN]** Find the conservative minimum sample size $n$ required to keep the margin of error for estimating proportion $p$ within 3% ($z_{0.025}=1.96$).

**[KR] 풀이:** $n \ge 1.96^2 / (4 \cdot 0.03^2) = 1067.11$ 이므로 정답은 1068입니다.
**[EN] Solution:** $n \ge 1.96^2 / (4 \cdot 0.03^2) = 1067.11$, so the required sample size is 1068.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 연습문제 원본 사진 및 손필기 노트 첨부 / Attachments (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-1" src="https://github.com/user-attachments/assets/625b0d6a-5363-488c-b974-bab9040fe1ff" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-2" src="https://github.com/user-attachments/assets/69485854-6221-4e17-9a37-832a29a13d8c" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-3" src="https://github.com/user-attachments/assets/4bc6d244-b4be-407d-8a1d-5e74e0ef579b" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-4" src="https://github.com/user-attachments/assets/029ae900-3430-4b1f-ba2e-02f528ce1f17" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-5" src="https://github.com/user-attachments/assets/de72bfaa-df35-4897-a450-ec9eed86de7f" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-6" src="https://github.com/user-attachments/assets/2438176a-501d-4c6c-893c-5c02800418c4" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-7" src="https://github.com/user-attachments/assets/a801c782-3d5a-4d0d-a0ec-002c40ae4c33" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-8" src="https://github.com/user-attachments/assets/a5230bf2-b06f-4226-81f0-cf2af138f63e" />
    <img width="1656" height="2342" alt="Statistics4 Module1 Exercises-9" src="https://github.com/user-attachments/assets/988f90e1-c6dc-482c-ab2a-f39459209eae" />
  </div>
</details>
