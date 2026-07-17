---
title: "1-4 Normal Mean (Variance Unknown)"
date: 2026-07-17 09:50:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, normal-distribution, t-distribution, confidence-interval, studentizing]
math: true
---

## 1. 모분산을 모르는 현실적인 상황 (Realistic Scenario: Unknown Variance)

**[KR]** 모평균 $\mu$를 추정할 때, 모집단의 진짜 분산 $\sigma^2$을 완벽히 알고 있는 경우는 현실에서 거의 존재하지 않습니다. 따라서 표본 데이터 $X_1, \dots, X_n \sim N(\mu, \sigma^2)$가 주어졌을 때, 미지의 $\sigma^2$ 역시 표본 데이터로부터 계산해 낸 표본 분산 $S^2$으로 대체하여 추정해야만 합니다.

**[EN]** When estimating the population mean $\mu$, it is highly unrealistic to know the true population variance $\sigma^2$. Thus, given sample data $X_1, \dots, X_n \sim N(\mu, \sigma^2)$, we must replace the unknown $\sigma^2$ with the sample variance $S^2$ calculated directly from the observed data.

---

## 2. 스튜던트화와 t-분포의 도출 (Studentizing and the t-distribution)

**[KR]** 분산을 $S^2$으로 대체하는 과정을 수학적으로 정당화하기 위해 다음 세 가지의 강력한 통계적 성질들이 활용됩니다.
* 표본 평균을 표준화한 통계량은 표준 정규 분포를 따릅니다 ($\frac{\bar{X} - \mu}{\sqrt{\sigma^2/n}} \sim N(0, 1)$).
* 코크란의 정리(Cochran's Theorem)에 의해, 표본 평균 $\bar{X}$와 표본 분산 $S^2$은 서로 완벽하게 독립(Independent)입니다.
* 표본 분산 $S^2$은 카이제곱 분포와 밀접한 관계를 가지며, $S^2 \sim \frac{\sigma^2 \chi^2(n-1)}{n-1}$ 이라는 공식이 성립합니다.

미지의 $\sigma^2$을 식에서 완전히 소거하기 위해, 표준 정규 분포를 카이제곱 분포의 수식과 결합하여 나누어 줍니다. 이 놀라운 과정을 **'표준화 및 스튜던트화(Standardizing and Studentizing)'**라고 부르며, 그 결과 미지의 모분산 없이 오직 표본 분산 $S^2$만으로 이루어진 자유도 $n-1$인 **t-분포**가 새롭게 도출됩니다.

$$
\frac{\bar{X} - \mu}{\sqrt{S^2/n}} \sim t(n-1)
$$


---

## 3. t-분포를 활용한 신뢰 구간 (Confidence Intervals using t-distribution)

**[KR]** 이제 우리의 피벗(Pivot) 통계량이 정규 분포가 아닌 t-분포를 따르므로, 신뢰 구간을 구할 때 $Z$ 분위수 대신 t-분포의 분위수인 $t_{\alpha/2, n-1}$을 사용해야만 합니다.

* **$100(1-\alpha)\%$ 양측 신뢰 구간 (Two-sided CI):** 
  $$ \mu \in \bar{X} \pm t_{\alpha/2, n-1} \sqrt{\frac{S^2}{n}} $$
* **$100(1-\alpha)\%$ 하한 단측 신뢰 구간 (Lower CI):** 
  $$ \mu \ge \bar{X} - t_{\alpha, n-1} \sqrt{\frac{S^2}{n}} $$
* **$100(1-\alpha)\%$ 상한 단측 신뢰 구간 (Upper CI):** 
  $$ \mu \le \bar{X} + t_{\alpha, n-1} \sqrt{\frac{S^2}{n}} $$

**[통계적 직관]** t-분포의 분위수는 표준 정규 분포의 분위수보다 값이 더 큽니다. 따라서 모분산을 모를 때 수립하는 신뢰 구간은 분산을 알 때의 신뢰 구간보다 그 오차 범위가 약간 더 길어지고 넓어집니다. 이는 분산을 추정하는 과정에서 발생한 '불확실성(Uncertainty)'에 대한 자연스러운 통계적 페널티라 할 수 있습니다.

---

## 4. 실전 예제 (Practice Example)

**[KR]** 방염 처리가 된 아동용 잠옷 20벌을 대상으로 잔류 불꽃이 지속되는 시간(초)을 측정한 데이터가 있다고 가정해 봅시다. 
* 수집된 20개의 데이터로부터 표본 평균은 $\bar{X} = 9.8525$, 표본 표준편차는 $S = 0.0965$ 로 도출되었습니다.
* 평균 시간에 대한 95% 신뢰 구간을 구하기 위해, 자유도가 19 ($n-1$)인 t-분위수를 찾으면 $t_{0.025, 19} = 2.093$ 이 나옵니다.
* 신뢰 구간의 반폭(Half-length)을 계산하면 $H = 2.093 \times \frac{0.0965}{\sqrt{20}} = 0.0451$ 이 됩니다.
* 최종적으로 도출된 평균 잔류 불꽃 시간의 95% 양측 신뢰 구간은 $9.8074 \le \mu \le 9.8976$ 입니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-4 Normal Mean (Variance Unknown)-1" src="https://github.com/user-attachments/assets/49c5a6d4-68b8-4edd-bdae-77137fdc579c" />
    <img width="1264" height="1635" alt="1-4 Normal Mean (Variance Unknown)-2" src="https://github.com/user-attachments/assets/afc0bea1-b4fd-43cd-8d0c-27a9f4a4a463" />
    <img width="1264" height="1635" alt="1-4 Normal Mean (Variance Unknown)-3" src="https://github.com/user-attachments/assets/210f9c46-0d78-4cdf-9c10-289a9baaf415" />
  </div>
</details>
