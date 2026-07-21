---
title: "Statistics4 Module2 Hypothesis Test Exercises"
date: 2026-07-21 21:40:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, z-test, t-test, chi-squared, f-test, bernoulli]
math: true
---

## 2-1. 가설검정 입문 (Introduction to Hypothesis Testing)

### [문제 1] Z-검정통계량 계산 및 귀무가설 기각 여부 판단
* **[KR]** 과자 평균 무게가 $100\text{g}$인지 검정합니다 ($H_0: \mu = 100$ vs $H_1: \mu \neq 100$). $\sigma=10\text{g}, n=25, \bar{X}=105\text{g}, \alpha=0.05$ (임계값 $\pm1.96$).
* **[EN]** Test if the mean weight of snacks is $100\text{g}$ ($H_0: \mu = 100$ vs $H_1: \mu \neq 100$). Given $\sigma=10\text{g}, n=25, \bar{X}=105\text{g}, \alpha=0.05$ (critical values $\pm1.96$).

**[풀이 / Solution]**
1. Z-검정통계량($Z_{obs}$):
   $$ Z_{obs} = \frac{105 - 100}{\sqrt{10^2/25}} = 2.5 $$
  
2. 판정: $\lvert Z_{obs} \rvert = 2.5 > 1.96$ 이므로 **귀무가설 $H_0$를 기각한다**.

---

### [문제 2] t-검정통계량 계산 및 대립가설 채택 여부 판단
* **[KR]** 신약의 평균 소화 시간이 기존 $15$분보다 단축되었는지 검정합니다 ($H_0: \mu \ge 15$ vs $H_1: \mu < 15$). $n=16, \bar{X}=14.2, S=1.6, \alpha=0.05$ (기각역: $t_{obs} < -1.753$).
* **[EN]** Test if the mean digestion time of a new drug is shortened compared to the standard $15$ minutes ($H_0: \mu \ge 15$ vs $H_1: \mu < 15$). Given $n=16, \bar{X}=14.2, S=1.6, \alpha=0.05$ (rejection region: $t_{obs} < -1.753$).

**[풀이 / Solution]**
1. t-검정통계량($t_{obs}$):
   $$ t_{obs} = \frac{14.2 - 15}{\sqrt{1.6^2/16}} = -2.0 $$
  
2. 판정: $t_{obs} = -2.0 < -1.753$ 이므로 귀무가설 $H_0$를 기각하고 **대립가설($H_1$)의 주장을 인정한다**.

<br>

---

## 2-3. 모분산을 알 때의 정규모평균 검정 (Normal Mean Test with Known Variance)

### [문제 1] 양측검정 검정통계량 및 기각 여부
* **[KR]** 어린 25명의 체중 평균이 $60\text{kg}$인지 검정합니다 ($H_0: \mu = 60$ vs $H_1: \mu \neq 60$). $\sigma=4\text{kg}, n=25, \bar{X}=62\text{kg}, \alpha=0.05$ ($z_{0.025}=1.96$).
* **[EN]** Test if the mean weight of 25 children is $60\text{kg}$ ($H_0: \mu = 60$ vs $H_1: \mu \neq 60$). Given $\sigma=4\text{kg}, n=25, \bar{X}=62\text{kg}, \alpha=0.05$ ($z_{0.025}=1.96$).

**[풀이 / Solution]**
1. 검정통계량($Z_0$):
   $$ Z_0 = \frac{62 - 60}{4/\sqrt{25}} = 2.5 $$
  
2. 판정: $\lvert Z_0 \rvert = 2.5 > 1.96$ 이므로 **귀무가설 $H_0$를 기각한다**.

---

### [문제 2] p-value 계산 및 단측검정 의사결정
* **[KR]** 신소재 인장강도가 $100\text{MPa}$보다 큰지 검정합니다 ($H_0: \mu \le 100$ vs $H_1: \mu > 100$). $Z_0=2.00, \Phi(2.0)=0.9772, \alpha=0.05$.
* **[EN]** Test if the tensile strength of a new material is greater than $100\text{MPa}$ ($H_0: \mu \le 100$ vs $H_1: \mu > 100$). Given $Z_0=2.00, \Phi(2.0)=0.9772, \alpha=0.05$.

**[풀이 / Solution]**
1. p-value: $p = 1 - \Phi(2.0) = 1 - 0.9772 = 0.0228$.
2. 판정: $p = 0.0228 < 0.05$ 이므로 **대립가설($H_1$)을 채택(기각)한다**.

<br>

---

## 2-4. 모분산을 알 때의 정규모평균 검정: 설계 (Design)

### [문제 1] 양측검정 표본 크기 및 제2종 오류의 의미
* **[KR]** $\sigma=4, \delta = 62 - 60 = 2, \alpha=0.05 (z_{\alpha/2}=1.96), \beta=0.05 (z_\beta=1.645)$ 일 때 양측검정의 필요 표본 크기를 구하고 제2종 오류의 의미를 파악합니다.
* **[EN]** Find the required sample size for a two-sided test and identify the meaning of Type II error given $\sigma=4, \delta=2, \alpha=0.05, \beta=0.05$.

**[풀이 / Solution]**
1. 표본 크기($n$):
   $$ n \approx \frac{4^2 (1.96 + 1.645)^2}{2^2} = 51.9841 \implies 52 $$
  
2. 제2종 오류의 의미: **실제 평균 체중이 $62\text{kg}$으로 변했는데, 귀무가설을 기각하지 못하고 $60\text{kg}$이라고 잘못 유지하는 것** (보기 B).

---

### [문제 2] 단측검정 표본 크기 계산
* **[KR]** 타이어 평균 수명 개선 검정 ($H_0: \mu \le 40,000$ vs $H_1: \mu > 40,000$). $\sigma=3,000, \delta=1,000, \alpha=0.05 (z_\alpha=1.645), \beta=0.10 (z_\beta=1.28)$.
* **[EN]** Sample size calculation for tire lifespan improvement test. Given $\sigma=3,000, \delta=1,000, \alpha=0.05, \beta=0.10$.

**[풀이 / Solution]**
$$ n \approx \frac{3000^2 (1.645 + 1.28)^2}{1000^2} = 77.000625 \implies 78 $$

**Answer:** $n=78$

<br>

---

## 2-5. 모분산을 알 때 두 독립표본 정규모평균 검정 (Two-Sample Test - Known Variances)

### [문제 1] 양측검정 $Z_0$ 계산 및 기각 여부
* **[KR]** 집단 X($n=10, \bar{X}=824.9, \sigma_x^2=40$)와 집단 Y($m=10, \bar{Y}=818.6, \sigma_y^2=50$)의 평균 차이 양측검정 ($\alpha=0.05, z_{0.025}=1.96$).
* **[EN]** Two-sided test for difference in means between Group X and Group Y at $\alpha=0.05$.

**[풀이 / Solution]**
1. 검정통계량($Z_0$):
   $$ Z_0 = \frac{824.9 - 818.6}{\sqrt{\frac{40}{10} + \frac{50}{10}}} = 2.10 $$
  
2. 판정: $\lvert Z_0 \rvert = 2.1 > 1.96$ 이므로 **귀무가설 $H_0$를 기각한다**.

---

### [문제 2] 단측검정 $Z_0$ 계산 및 대립가설 인정 여부
* **[KR]** 공정 A와 B의 생산량 비교 단측검정 ($H_0: \mu_x \le \mu_y$ vs $H_1: \mu_x > \mu_y$). 집단 A($n=25, \bar{X}=105, \sigma_x^2=100$), 집단 B($m=25, \bar{Y}=100, \sigma_y^2=100$), $\alpha=0.05$ ($z_{0.05}=1.645$).
* **[EN]** One-sided test comparing process A and B. Given $n=m=25, \bar{X}=105, \bar{Y}=100, \sigma_x^2=\sigma_y^2=100, \alpha=0.05$.

**[풀이 / Solution]**
1. 검정통계량($Z_0$):
   $$ Z_0 = \frac{105 - 100}{\sqrt{\frac{100}{25} + \frac{100}{25}}} = 1.768 $$
  
2. 판정: $Z_0 = 1.768 > 1.645$ 이므로 **대립가설($H_1$)의 주장을 인정(기각)한다**.

<br>

---

## 2-6. 모분산을 모를 때의 정규모평균 검정 (Unknown Variance)

### [문제 1] 양측검정 t-검정통계량 및 기각 여부
* **[KR]** 공정 평균이 $150$인지 검정 ($H_0: \mu = 150$). $n=16, \bar{X}=152.08, S=4.08, \alpha=0.05$ ($t_{0.025, 15}=2.131$).
* **[EN]** Two-sided t-test for process mean equals $150$. Given $n=16, \bar{X}=152.08, S=4.08, \alpha=0.05$.

**[풀이 / Solution]**
1. t-검정통계량($T_0$):
   $$ T_0 = \frac{152.08 - 150}{4.08/\sqrt{16}} = 2.039 $$
  
2. 판정: $\lvert T_0 \rvert = 2.039 < 2.131$ 이므로 **귀무가설을 기각하지 않는다(채택)**.

---

### [문제 2] p-value를 이용한 양측검정 의사결정
* **[KR]** $T_0 = 2.070, p = 0.0574, \alpha = 0.05$ 일 때의 의사결정과 p-value의 의미를 고릅니다.
* **[EN]** Decision and meaning of p-value given $T_0 = 2.070, p = 0.0574, \alpha = 0.05$.

**[풀이 / Solution]**
1. 판정: $p = 0.0574 > 0.05$ 이므로 **귀무가설을 기각하지 않는다**.
2. 의미 설명: **보기 A** (p-value가 유의수준보다 크므로 결과가 아주 희귀하지 않아 기각하지 못함).

<br>

---

## 2-7. 모분산을 모를 때 두 독립표본 정규모평균 검정 (Two-Sample t-Tests)

### [문제 1] 합동분산 및 $T_0$ 계산과 촉매 교체 의사결정
* **[KR]** 촉매 X($n=8, \bar{X}=91.73, S_x^2=3.89$)와 촉매 Y($m=8, \bar{Y}=93.75, S_y^2=4.02$)의 단측검정($\alpha=0.05, t_{0.05, 14}=1.761$).
* **[EN]** One-sided pooled t-test for catalysts X and Y at $\alpha=0.05$.

**[풀이 / Solution]**
1. 합동분산($S_p^2$) 및 검정통계량($T_0$):
   $$ S_p^2 = \frac{7(3.89) + 7(4.02)}{14} = 3.955 $$
   $$ T_0 = \frac{91.73 - 93.75}{\sqrt{3.955(\frac{1}{8} + \frac{1}{8})}} = -2.03 $$
  
2. 판정: $T_0 = -2.03 < -1.761$ 이므로 귀무가설을 기각하고 **촉매 Y로 교체해야 한다**.

---

### [문제 2] Welch 근사 t-검정통계량($T_0^*$) 계산
* **[KR]** 공정 X($n=15, \bar{X}=24.2, S_x^2=10$)와 공정 Y($m=10, \bar{Y}=23.9, S_y^2=20$)의 이분산 양측검정 ($\alpha=0.10, t_{0.05, 15}=1.753$).
* **[EN]** Welch's approximate t-test for unequal variances at $\alpha=0.10$.

**[풀이 / Solution]**
1. 통계량($T_0^*$):
   $$ T_0^* = \frac{24.2 - 23.9}{\sqrt{\frac{10}{15} + \frac{20}{10}}} = 0.1837 $$
  
2. 판정: $\lvert T_0^* \rvert = 0.1837 < 1.753$ 이므로 **보기 A** (기각하지 못하며 유의미한 차이가 있다는 증거가 없다).

<br>

---

## 2-8. 대응표본을 이용한 두 정규모평균 검정 (Paired Observations)

### [문제 1] 양측 대응표본 $T_0$ 계산 및 기각 여부
* **[KR]** 운전자 5명 차량 주차 시간 차이 ($\bar{D}=-9, S_d^2=42.5, n=5, \alpha=0.10, t_{0.05, 4}=2.13$).
* **[EN]** Paired t-test for parking times of 5 drivers given $\bar{D}=-9, S_d^2=42.5, n=5, \alpha=0.10$.

**[풀이 / Solution]**
1. 검정통계량($T_0$):
   $$ T_0 = \frac{-9}{\sqrt{42.5/5}} = -3.087 $$
  
2. 판정: $\lvert T_0 \rvert = 3.087 > 2.13$ 이므로 **귀무가설을 기각한다**.

---

### [문제 2] 단측 대립가설 채택 여부 판단
* **[KR]** 환자 9명의 신약 투여 전후 혈압 차이 검정 ($H_0: \mu_d \ge 0$ vs $H_1: \mu_d < 0$). $\bar{D}=-6, S_d^2=81, n=9, \alpha=0.05, -t_{0.05, 8}=-1.860$.
* **[EN]** One-sided paired t-test for blood pressure change after new drug administration.

**[풀이 / Solution]**
1. 검정통계량($T_0$):
   $$ T_0 = \frac{-6}{\sqrt{81/9}} = -2.0 $$
  
2. 판정: $T_0 = -2.0 < -1.860$ 이므로 귀무가설을 기각하고 **대립가설을 인정한다(효과가 있음)**.

<br>

---

## 2-9. 정규분산 검정 (Normal Variance Test)

### [문제 1] 단측 카이제곱 검정통계량 계산 및 품질 적합 여부
* **[KR]** 모분산 기준치 검정 ($H_0: \sigma^2 \le 0.02$). $n=20, S^2=0.0225, \sigma_0^2=0.02, \alpha=0.05, \chi_{0.05, 19}^2=30.14$.
* **[EN]** One-sided chi-squared variance test given $n=20, S^2=0.0225, \sigma_0^2=0.02, \alpha=0.05$.

**[풀이 / Solution]**
1. 검정통계량($\chi_0^2$):
   $$ \chi_0^2 = \frac{(20-1) \times 0.0225}{0.02} = 21.375 $$
  
2. 판정: $\chi_0^2 = 21.375 < 30.14$ 이므로 **공정이 안정적이다(기각 실패)**.

---

### [문제 2] 양측 카이제곱 검정통계량 및 기각 여부
* **[KR]** 모분산 표준 검정 ($H_0: \sigma^2 = 10$). $n=11, S^2=18, \sigma_0^2=10, \alpha=0.05$ (임계값 범위: $[3.25, 20.48]$).
* **[EN]** Two-sided chi-squared variance test given $n=11, S^2=18, \sigma_0^2=10, \alpha=0.05$.

**[풀이 / Solution]**
1. 검정통계량($\chi_0^2$):
   $$ \chi_0^2 = \frac{(11-1) \times 18}{10} = 18 $$
  
2. 판정: $18$이 범위 $[3.25, 20.48]$ 내에 존재하므로 **귀무가설을 기각하지 않는다(채택)**.

<br>

---

## 2-10. 두 독립표본 정규분산 검정 (Two-Sample Variances F-Test)

### [문제 1] 양측 F-검정통계량 및 기각 여부
* **[KR]** 공정 X($n=7, S_x^2=7.78$)와 공정 Y($m=8, S_y^2=12.04$)의 분산 동일성 검정 ($\alpha=0.05$, 임계값 범위: $[0.176, 5.12$]).
* **[EN]** Two-sided F-test for variances of process X and Y at $\alpha=0.05$.

**[풀이 / Solution]**
1. 검정통계량($F_0$):
   $$ F_0 = \frac{7.78}{12.04} = 0.646 $$
  
2. 판정: $0.646$이 범위 $[0.176, 5.12]$ 내에 있으므로 **귀무가설을 기각하지 않는다**.

---

### [문제 2] 단측 F-검정통계량 및 공정 불안정성 비교
* **[KR]** 공정 X($n=10, S_x^2=36$)와 공정 Y($m=10, S_y^2=12$)의 단측검정 ($H_0: \sigma_x^2 \le \sigma_y^2$ vs $H_1: \sigma_x^2 > \sigma_y^2$). $\alpha=0.05, F_{0.05, 9, 9}=3.18$.
* **[EN]** One-sided F-test comparing variances of process X and Y at $\alpha=0.05$.

**[풀이 / Solution]**
1. 검정통계량($F_0$):
   $$ F_0 = \frac{36}{12} = 3 $$
  
2. 판정: $F_0 = 3 < 3.18$ 이므로 **귀무가설을 기각하지 못한다**.

<br>

---

## 2-11. 베르누이 비율 검정 (Bernoulli Proportion Test)

### [문제 1] 단측 Z-검정통계량 및 불량률 검정
* **[KR]** 반도체 불량률 검정 ($H_0: p \ge 0.06$ vs $H_1: p < 0.06$). $n=200, Y=4, p_0=0.06, \alpha=0.05, -z_{0.05}=-1.645$.
* **[EN]** One-sided proportion test for semiconductor defect rate given $n=200, Y=4, p_0=0.06$.

**[풀이 / Solution]**
1. 검정통계량($Z_0$):
   $$ Z_0 = \frac{4 - 200(0.06)}{\sqrt{200(0.06)(0.94)}} = -2.382 $$
  
2. 판정: $Z_0 = -2.382 < -1.645$ 이므로 **귀무가설을 기각한다(품질 개선 인정)**.

---

### [문제 2] 비율 검정의 최소 표본 크기 계산
* **[KR]** $p_0=0.80, p_1=0.70, \alpha=0.05(z_{\alpha/2}=1.96), \beta=0.10(z_\beta=1.28)$ 일 때 필요한 최소 표본 크기를 구합니다.
* **[EN]** Calculate the minimum sample size for proportion test given $p_0=0.80, p_1=0.70, \alpha=0.05, \beta=0.10$.

**[풀이 / Solution]**
$$ n \approx \left[ \frac{1.96\sqrt{0.8 \times 0.2} + 1.28\sqrt{0.7 \times 0.3}}{0.7 - 0.8} \right]^2 = 187.96 \implies 188 $$

**Answer:** $n=188$

<br>

---

## 2-12. 두 독립표본 베르누이 비율 검정 (Two-Sample Proportions Test)

### [문제 1] 양측 합동 비율 Z-검정 및 기각 여부
* **[KR]** 매장 A($n=200, X=140$)와 매장 B($m=300, Y=210$)의 만족도 비율 차이 양측검정 ($\alpha=0.05, z_{0.025}=1.96$).
* **[EN]** Two-sided pooled proportion test for stores A and B at $\alpha=0.05$.

**[풀이 / Solution]**
1. 합동 비율($\hat{p}$) 및 검정통계량($Z_0$):
   $$ \hat{p} = \frac{140 + 210}{200 + 300} = 0.70 $$
   $$ Z_0 = \frac{0.70 - 0.70}{\sqrt{0.70(0.30)(\frac{1}{200} + \frac{1}{300})}} = 0 $$
  
2. 판정: $Z_0 = 0 < 1.96$ 이므로 **귀무가설을 기각하지 않는다**.

---

### [문제 2] 마케팅 효과 단측검정
* **[KR]** 그룹 A($n=100, \bar{X}=0.40$)와 그룹 B($m=100, \bar{Y}=0.20$)의 구매 비율 단측검정 ($\hat{p}=0.30, \alpha=0.05, z_{0.05}=1.645$).
* **[EN]** One-sided proportion test for marketing campaign effect between group A and B.

**[풀이 / Solution]**
1. 검정통계량($Z_0$):
   $$ Z_0 = \frac{0.40 - 0.20}{\sqrt{0.30(0.70)(\frac{1}{100} + \frac{1}{100})}} = 3.09 $$
  
2. 판정: $Z_0 = 3.09 > 1.645$ 이므로 **귀무가설을 기각한다(마케팅 효과 있음)**.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-01" src="https://github.com/user-attachments/assets/ee534a42-f2d4-415d-b28a-731afa754538" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-02" src="https://github.com/user-attachments/assets/ddb2f543-143c-4d32-b02f-8e104f7cabf3" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-03" src="https://github.com/user-attachments/assets/dfeaf553-94f2-4dba-9cbb-f2ea5db4d0ed" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-04" src="https://github.com/user-attachments/assets/ce9e18ae-5278-4e4e-99ec-20cf63f150b5" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-05" src="https://github.com/user-attachments/assets/5e81eaf5-689c-4c18-8bfb-ce272cada310" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-06" src="https://github.com/user-attachments/assets/85e72bb9-53c8-4d50-bbc1-46a311090aeb" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-07" src="https://github.com/user-attachments/assets/d21a6752-4eec-41dd-8bdd-971e92b84cfc" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-08" src="https://github.com/user-attachments/assets/2fb4c166-07d2-4485-8e0f-d8586f27d50c" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-09" src="https://github.com/user-attachments/assets/64f08a63-4c15-4ada-b664-98ebcc9b16f7" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-10" src="https://github.com/user-attachments/assets/df057efe-10f4-467a-9679-d2bbcc496dac" />
    <img width="1656" height="2342" alt="Statistics4 Module2 Hypothesis Test  Exercises-11" src="https://github.com/user-attachments/assets/030b940b-1a03-46d2-b35a-1ebd75d79219" />
  </div>
</details>
