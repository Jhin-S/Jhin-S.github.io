---
title: "1-3 Difference of Two Normal Means (variances known)"
date: 2026-07-17 09:37:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, normal-distribution, difference-of-means, confidence-interval]
math: true
---

## 1. 두 집단의 모평균 차이 비교 (Comparing Difference of Two Means)

**[KR]** 두 개의 경쟁하는 대안이나 프로세스가 있을 때, 이들의 평균적인 성능 차이를 비교하는 가장 확실한 방법은 두 모평균의 차이($\mu_x - \mu_y$)에 대한 신뢰 구간을 구하는 것입니다. 이번 장에서는 두 모집단이 각각 정규 분포를 따르고, 각 집단의 모분산($\sigma_x^2, \sigma_y^2$)을 이미 알고 있다고 가정하는 가장 기초적인 모델을 다룹니다. (물론 현실에서는 분산을 모르는 경우가 대부분이므로, 이는 다음 장에서 다루게 될 것입니다.)

**[EN]** When comparing two competing alternatives or processes, the most definitive method is to construct a confidence interval for the difference between their population means ($\mu_x - \mu_y$). In this lesson, we cover the foundational model which assumes that both populations follow a normal distribution and that their respective population variances ($\sigma_x^2, \sigma_y^2$) are already known. (Of course, in reality, variances are usually unknown, a more realistic scenario we will address in the next lesson.)

---

## 2. 피벗 통계량과 신뢰 구간 도출 (Pivot Quantity and CI Derivation)

**[KR]** 두 모집단 1과 2에서 각각 크기가 $n$과 $m$인 독립적인 표본을 추출했다고 가정합시다.
$$X_1, \dots, X_n \sim N(\mu_x, \sigma_x^2)$$ 
$$Y_1, \dots, Y_m \sim N(\mu_y, \sigma_y^2)$$ 
각 집단의 표본 평균 $\bar{X}$와 $\bar{Y}$의 차이는 새로운 정규 분포를 형성하게 됩니다. 이를 표준화하면, 미지의 모수 차이($\mu_x - \mu_y$)를 중앙에 고립시킬 수 있는 피벗(Pivot) 통계량 $Z$를 얻을 수 있습니다.

$$
Z \equiv \frac{\bar{X} - \bar{Y} - (\mu_x - \mu_y)}{\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}} \sim N(0, 1)
$$

이 피벗을 활용하여 확률 방정식을 풀면, 모평균의 차이에 대한 $100(1-\alpha)\%$ 양측 신뢰 구간을 다음과 같이 도출할 수 있습니다.

$$
\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm z_{\alpha/2}\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}
$$

---

## 3. 단측 신뢰 구간 (One-sided Confidence Intervals)

**[KR]** 한쪽 방향으로만의 차이가 궁금할 때는 상한이나 하한만 존재하는 단측 신뢰 구간을 사용합니다.
* **단측 상한 (One-sided upper CI):** $\mu_x - \mu_y \le \bar{X} - \bar{Y} + z_\alpha\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}$
* **단측 하한 (One-sided lower CI):** $\mu_x - \mu_y \ge \bar{X} - \bar{Y} - z_\alpha\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}$

---

## 4. 실전 예제 및 표본 크기 계산 (Practice Example & Sample Size)

**[KR]** 조지아 공대(GT) 학생들과 조지아 대학교(UGA) 학생들의 시험 점수 평균을 비교하는 예제를 살펴봅시다. GT 학생 40명의 평균 점수는 95점(표준편차 20)이고, UGA 학생 24명의 평균 점수는 60점(표준편차 12)이었습니다. 
위의 공식을 이용해 90% 양측 신뢰 구간을 계산하면 다음과 같습니다.

$$
\mu_x - \mu_y = 35 \pm 1.645\sqrt{\frac{400}{40} + \frac{144}{24}} = 35 \pm 6.58
$$

즉, 두 학교 학생들의 평균 점수 차이가 $28.42$점에서 $41.58$점 사이에 있을 확률이 90%라는 결론을 내릴 수 있습니다.

**표본 크기 설정:** 만약 두 집단에서 동일한 개수의 표본을 추출($n=m$)한다고 가정할 때, 원하는 오차 한계(반폭, $\epsilon$)를 맞추기 위한 최소 표본 크기는 다음과 같이 계산됩니다.

$$
n \ge \frac{z_{\alpha/2}^2 (\sigma_x^2 + \sigma_y^2)}{\epsilon^2}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-3 Difference of Two Normal Means (variances known)-1" src="https://github.com/user-attachments/assets/8a1e47c3-3738-4e5f-aa3c-f7bccd2f2366" />
    <img width="1264" height="1635" alt="1-3 Difference of Two Normal Means (variances known)-2" src="https://github.com/user-attachments/assets/60886766-472e-4868-8d11-a11ed86c99ae" />
  </div>
</details>
