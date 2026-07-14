---
title: "2-11 Sampling Distributions"
date: 2026-07-14 22:02:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, sampling-distribution, chi-squared, t-distribution, f-distribution]
math: true
---

## 1. 표본 분포와 정규 분포 (Sampling Distributions & Normal Distribution)

**[KR]** 통계학에서 통계량(Statistic)이란 우리가 관측한 표본 데이터들만으로 계산된 함수를 의미하며, 미지의 모수(Parameter)를 포함하지 않습니다. 표본을 추출할 때마다 관측치가 달라지므로 통계량 역시 확률 변수가 되며, 이러한 통계량들이 따르는 확률 분포를 **표본 분포(Sampling Distribution)**라고 부릅니다. 
대표적으로 표본 평균 $\bar{X}$는 정규 분포 $\bar{X} \sim N(\mu, \sigma^2/n)$를 따르게 되며, 이는 향후 모평균 $\mu$에 대한 신뢰 구간(Confidence Intervals) 설정과 가설 검정(Hypothesis Tests)을 수행하는 데 핵심적으로 사용됩니다.

---

## 2. 카이제곱 분포 ($\chi^2$ Distribution)

**[KR]** 통계학에서 표본의 분산을 다룰 때 필수적으로 등장하는 분포가 바로 **카이제곱 분포**입니다.
* **정의:** $k$개의 독립적인 표준 정규 분포 확률 변수 $Z_i \sim N(0,1)$ 들의 제곱을 모두 더한 값($Y = \sum_{i=1}^k Z_i^2$)은 자유도(Degrees of freedom, $df$)가 $k$인 카이제곱 분포 $\chi^2(k)$ 를 따릅니다. 
* **자유도의 의미:** 자유도는 시스템이 가진 '독립적인 정보의 개수'를 의미합니다. 특정 파라미터(예: 평균)를 추정하기 위해 표본 데이터를 사용할 때마다 우리는 이 자유도를 1개씩 잃게 됩니다.
* **특징:**
  * 카이제곱 분포의 기댓값은 $E[Y] = k$ 이며, 분산은 $Var(Y) = 2k$ 입니다.
  * 지수 분포는 카이제곱 분포의 특별한 케이스로, $\chi^2(2) \sim Exp(1/2)$ 가 성립합니다.
  * 독립적인 카이제곱 분포들을 더하면, 각 자유도를 더한 새로운 카이제곱 분포가 됩니다.
* **활용:** 모분산 $\sigma^2$ 을 추정할 때 활용되며, 표본 분산 $S^2$ 과 카이제곱 분포 사이에는 $S^2 \sim \frac{\sigma^2 \chi^2(n-1)}{n-1}$ 라는 아주 중요한 관계가 성립합니다.

---

## 3. 스튜던트 t 분포 (Student's t Distribution)

**[KR]** 모평균을 검정하고 싶지만 모집단의 진짜 분산을 알지 못할 때, 정규 분포를 대신하여 활약하는 분포입니다.
* **정의:** 독립적인 표준 정규 분포 변수 $Z$와 자유도가 $k$인 카이제곱 변수 $Y$를 결합하여, $T = \frac{Z}{\sqrt{Y/k}}$ 로 정의되며 자유도 $k$인 $t(k)$ 를 따릅니다.
* **특징:**
  * 표준 정규 분포와 비슷하게 중심이 0이고 좌우 대칭인 종 모양이지만, 양쪽 꼬리가 훨씬 더 두꺼운(Fatter tails) 형태를 띱니다.
  * 자유도 $k=1$ 일 때는 매우 극단적인 꼬리를 가지는 코시(Cauchy) 분포가 되며, 반대로 표본 크기가 커져서 자유도 $k$ 가 무한대로 가면 표준 정규 분포 $N(0,1)$ 에 완벽하게 수렴합니다.
* **기원과 활용:** 이 분포는 모평균 $\mu$ 의 신뢰 구간과 가설 검정에 사용되며, 아일랜드 기네스 양조장의 통계학자였던 윌리엄 고셋(William Gosset)이 'Student'라는 익명으로 논문을 발표한 데서 이름이 유래했습니다.

---

## 4. F 분포 (F Distribution)

**[KR]** 두 개의 서로 다른 모집단이나 공정에서 추출한 분산들의 비율을 비교할 때 사용되는 분포입니다.
* **정의:** 두 개의 독립적인 카이제곱 확률 변수 $X \sim \chi^2(n)$ 과 $Y \sim \chi^2(m)$ 이 있을 때, 이를 각각의 자유도로 나눈 비율 $F = \frac{X/n}{Y/m}$ 은 두 개의 자유도 $n$과 $m$을 가지는 F 분포 $F(n, m)$ 을 따릅니다.
* **특징:**
  * 데이터가 양수 영역에만 존재하며, 오른쪽으로 꼬리가 길게 늘어진 비대칭 형태(Skewed to the right)를 가집니다. 
  * 스튜던트 t 분포를 제곱한 것은 분자의 자유도가 1인 F 분포의 특수한 케이스와 같습니다.
* **분위수(Quantile) 역수 성질:** F 분포의 분위수를 계산할 때, 꼬리 확률을 뒤집거나 자유도의 순서를 바꾸면 서로 역수 관계가 되는 매우 유용한 성질이 있습니다. 즉, $F_{1-\alpha, m, n} = \frac{1}{F_{\alpha, n, m}}$ 이 성립합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-11 Sampling Distributions-1" src="https://github.com/user-attachments/assets/7e326d8b-b596-422a-9875-2ff3a829aeae" />
    <img width="1264" height="1635" alt="2-11 Sampling Distributions-2" src="https://github.com/user-attachments/assets/283bb8b1-7d43-4d43-8ed3-35f88e86c82b" />
    <img width="1264" height="1635" alt="2-11 Sampling Distributions-3" src="https://github.com/user-attachments/assets/b1a4b1b6-895c-4197-87a3-bdc175c7a8d1" />
    <img width="1264" height="1635" alt="2-11 Sampling Distributions-4" src="https://github.com/user-attachments/assets/5026a5b6-107d-4bd0-89d7-15b858a6636a" />
    <img width="1264" height="1635" alt="2-11 Sampling Distributions-5" src="https://github.com/user-attachments/assets/3e08d52b-4d4a-4a26-bff1-87cbed7c13d5" />
  </div>
</details>
