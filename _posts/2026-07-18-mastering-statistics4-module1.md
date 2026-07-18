---
title: "Mastering Statistics4 Module1"
date: 2026-07-18 13:15:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, confidence-interval, normal-distribution, t-distribution, f-distribution, chi-squared, bernoulli]
math: true
---

이번에는 모듈1(신뢰구간)의 모든 내용을 정리하며 복습해보았습니다. 확률과 통계 과정은 개념도 많고 미적분학과 선형대수학과 다른 방향성으로 논리가 전개되기에 확실히 어려운 것 같습니다.
다만, 어려운 만큼 이해했을 때 재미있고 큰 성취감과 뿌듯함이 몰려옵니다. 이번 포스팅은 손으로 적은 페이지 수가 17페이지나 되네요. 꾸준히 실력을 증진해나가겠습니다. :)

## 1-1. 신뢰 구간의 도입 (Introduction to Confidence Intervals)

**[KR]** 통계적 추론에서 미지의 모수(Parameter, $\theta$)를 단 하나의 점(Point)으로 추정하는 것에는 필연적인 오차가 따릅니다. 이를 보완하기 위해 통계학에서는 모수를 특정 확률로 품고 있을 것이라 기대되는 '구간(Interval)'을 제시합니다. 
모수 $\theta$에 대한 $100(1-\alpha)\%$ 신뢰 구간은 아래의 확률 부등식을 만족하는 확률 변수 하한($L$)과 상한($U$)으로 정의됩니다. 

$$ P(L \le \theta \le U) = 1 - \alpha $$


여기서 $1-\alpha$를 **신뢰 계수(Confidence Coefficient)**라고 부르며, 이는 우리가 샘플링을 반복했을 때 실제 모수가 이 구간 사이에 존재할 확률을 의미합니다.

---

## 1-2. 정규 분포의 평균 추정: 분산을 아는 경우 (Normal Mean, Variance Known)

**[KR]** 알려지지 않은 모평균 $\mu$를 추정하기 위해 표본 평균 $\bar{X}$를 사용합니다. 모집단의 분산 $\sigma^2$을 알고 있다고 가정($X_i \sim N(\mu, \sigma^2)$)하면, 표본 평균을 표준화하여 완벽한 표준 정규 분포를 따르는 **피벗(Pivot)** 통계량 $Z$를 유도할 수 있습니다.

$$ Z \equiv \frac{\bar{X} - \mu}{\sqrt{\sigma^2/n}} \sim N(0, 1) $$


이 피벗을 활용하여 확률 부등식을 전개하면 $\mu$에 대한 양측 신뢰 구간을 얻을 수 있습니다. 
* **양측 신뢰 구간:** $\bar{X} - z_{\alpha/2}\sqrt{\frac{\sigma^2}{n}} \le \mu \le \bar{X} + z_{\alpha/2}\sqrt{\frac{\sigma^2}{n}}$
* **오차 한계(반폭, $H$)와 표본 크기:** $H = z_{\alpha/2}\sqrt{\sigma^2/n}$ 이며, 원하는 오차 $\epsilon$을 맞추기 위한 최소 표본 크기는 $n \ge \left(\frac{\sigma z_{\alpha/2}}{\epsilon}\right)^2$ 로 계산됩니다. 더 많은 관측치를 모을수록 구간은 짧아지고 정밀해집니다.

---

## 1-3. 두 정규 평균의 차이: 분산을 아는 경우 (Difference of Two Normal Means)

**[KR]** 서로 경쟁하는 두 집단(프로세스)의 평균 차이($\mu_x - \mu_y$)를 비교하기 위한 세팅입니다. 두 집단 모두 정규 분포를 따르고 각각의 분산($\sigma_x^2, \sigma_y^2$)을 안다고 가정할 때, 두 표본 평균의 차이 $\bar{X} - \bar{Y}$ 역시 정규 분포를 따릅니다.

$$ Z = \frac{\bar{X} - \bar{Y} - (\mu_x - \mu_y)}{\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}} \sim N(0, 1) $$


* **양측 신뢰 구간:** $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm z_{\alpha/2}\sqrt{\frac{\sigma_x^2}{n} + \frac{\sigma_y^2}{m}}$
* 두 집단의 표본 크기가 같을 때($n=m$), 목표 오차 $\epsilon$을 달성하기 위한 표본 크기는 $n \ge \frac{z_{\alpha/2}^2(\sigma_x^2 + \sigma_y^2)}{\epsilon^2}$ 입니다.

---

## 1-4. 정규 분포의 평균 추정: 분산을 모르는 경우 (Normal Mean, Variance Unknown)

**[KR]** 현실적으로 모분산 $\sigma^2$을 아는 경우는 없습니다. 따라서 이를 표본 분산 $S^2$으로 대체해야 합니다. 통계학의 핵심 정리들에 따르면 표본 평균 $\bar{X}$와 분산 $S^2$은 독립이며, 카이제곱 분포의 가법성을 이용한 대수적 증명을 통해 $S^2 \sim \frac{\sigma^2 \chi^2(n-1)}{n-1}$ 임을 유도할 수 있습니다. 
알 수 없는 $\sigma^2$을 식에서 완전히 소거하기 위해 표준 정규 변수 $Z$를 자유도가 $n-1$인 카이제곱 변수 $V$로 나누면 **t-분포**가 탄생합니다.

$$ \frac{\bar{X} - \mu}{S/\sqrt{n}} \sim t(n-1) $$


* **양측 신뢰 구간:** $\mu \in \bar{X} \pm t_{\alpha/2, n-1} \sqrt{\frac{S^2}{n}}$

---

## 1-5. 두 정규 평균의 차이: 분산은 모르지만 같은 경우 (Unknown Equal Variance)

**[KR]** 두 모집단의 분산을 모르지만 동일하다($\sigma_x^2 = \sigma_y^2 = \sigma^2$)고 가정하는 상황입니다. 두 집단의 표본 분산을 합쳐 공통 분산을 더 정확히 추정하는 **합동 분산 추정량(Pooled Estimator, $S_p^2$)**을 사용합니다. 

$$ S_p^2 = \frac{(n-1)S_x^2 + (m-1)S_y^2}{n+m-2} $$


이 식은 단순 평균이 아닌 '가중 평균(Weighted Average)'입니다. 각 집단의 자유도($n-1$, $m-1$)를 곱해 편차 제곱합을 구하고, 이를 총 자유도($n+m-2$)로 나누어 데이터가 더 많은 쪽에 가중치를 부여합니다.

* **피벗 및 신뢰 구간:** 피벗은 $t(n+m-2)$ 분포를 따르며, 구간은 $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, n+m-2} S_p \sqrt{\frac{1}{n} + \frac{1}{m}}$ 로 계산됩니다.

---

## 1-6. 두 정규 평균의 차이: 분산이 다를 경우 (Variance Unknown and Unequal)

**[KR]** 두 모집단의 분산이 확연히 다르다면 합동 분산을 쓸 수 없으며, **웰치의 근사 방법(Welch's Approximation)**을 동원해야 합니다. $V = \frac{S_x^2}{n} + \frac{S_y^2}{m}$ 라는 새로운 확률 변수를 정의하고, 적률법(MoM)을 통해 카이제곱 분포와 모멘트를 매칭시켜 복잡한 근사 자유도 $\nu$를 유도해냅니다.

$$ \nu \approx \frac{\left(\frac{S_x^2}{n} + \frac{S_y^2}{m}\right)^2}{\frac{(S_x^2/n)^2}{n-1} + \frac{(S_y^2/m)^2}{m-1}} $$


* **신뢰 구간:** 근사된 자유도 $\nu$ (보수적으로 내림하여 정수화)를 가진 $t$-분포를 사용하여 $\mu_x - \mu_y \in \bar{X} - \bar{Y} \pm t_{\alpha/2, \nu} \sqrt{\frac{S_x^2}{n} + \frac{S_y^2}{m}}$ 의 구간을 얻습니다.

---

## 1-7. 쌍체 표본의 평균 차이 (Difference of Paired Normal Means)

**[KR]** 두 모집단에서 데이터를 독립적으로 뽑지 않고 쌍(Pair)으로 수집하면, 외부 노이즈를 제거하여 차이를 더 정밀하게 포착할 수 있습니다. 쌍과 쌍 사이는 독립이지만, 쌍 내부의 $X_i$와 $Y_i$는 독립이 아닐 수 있습니다.
관측치의 차이 $D_i = X_i - Y_i$ 를 구하면, 문제는 단일 정규 분포의 평균과 분산을 모르는 케이스(1-4장)로 완벽히 단순화됩니다.

* **양측 신뢰 구간:** $\mu_d = \mu_x - \mu_y \in \bar{D} \pm t_{\alpha/2, n-1} \sqrt{\frac{S_d^2}{n}}$

---

## 1-8. 정규 분포의 분산 추정 (Normal Variance)

**[KR]** 시스템의 변동성(Variability)을 파악하기 위해 모분산 $\sigma^2$에 대한 신뢰 구간을 구합니다. 카이제곱 분포의 성질 $\frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1)$ 을 이용합니다.

* **양측 신뢰 구간:** 확률 부등식을 뒤집고 역수를 취하여 유도합니다.
$$ \sigma^2 \in \left[ \frac{(n-1)S^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)S^2}{\chi^2_{1-\alpha/2, n-1}} \right] $$

이 구간은 미지의 $\mu$를 포함하지 않으며, 표본 분산 $S^2$에 정비례합니다.

---

## 1-9. 두 정규 분포의 분산 비율 (Ratio of Variance of Two Normals)

**[KR]** 두 집단 중 어느 쪽의 변동성이 더 큰지 확인하기 위해 분산의 비율 $\sigma_x^2 / \sigma_y^2$ 을 비교합니다. 각각의 카이제곱 확률 변수를 자유도로 나눈 비율은 **F-분포**를 따릅니다.

$$ \frac{S_y^2 / \sigma_y^2}{S_x^2 / \sigma_x^2} \sim F(m-1, n-1) $$


* **양측 신뢰 구간:** F-분포의 대칭성과 역수 성질을 이용해 부등식을 정리하면 다음을 얻습니다.
$$ \frac{\sigma_x^2}{\sigma_y^2} \in \left[ \frac{S_x^2}{S_y^2} \frac{1}{F_{\alpha/2, m-1, n-1}}, \frac{S_x^2}{S_y^2} F_{\alpha/2, n-1, m-1} \right] $$


---

## 1-10. 베르누이 비율의 추정 (Bernoulli Proportion)

**[KR]** 성공 아니면 실패만 존재하는 베르누이 분포 $Bern(p)$에서 진짜 성공 확률 $p$를 추정합니다. 표본 크기 $n$이 충분히 크면 중심극한정리(CLT)에 의해 정규 분포로 근사할 수 있습니다. 
미지의 분산 $pq/n$을 최대우도추정량(MLE)인 $\bar{X}(1-\bar{X})/n$ 으로 과감히 대체(Plug-in)하여 피벗을 만듭니다.

* **양측 신뢰 구간:** $p \in \bar{X} \pm z_{\alpha/2}\sqrt{\frac{\bar{X}(1-\bar{X})}{n}}$
* **표본 크기 결정:** 오차 한계를 통제하기 위한 $n$을 구할 때, $p$를 모르므로 수학적 최댓값인 $1/4$를 대입하는 **보수적 방법($n \ge \frac{z_{\alpha/2}^2}{4\epsilon^2}$)**과 사전 연구 추정치 $\hat{p}$를 활용하는 방법이 있습니다.
* **두 모비율 차이의 구간:** 두 집단의 차이 역시 $p_x - p_y \in (\bar{X} - \bar{Y}) \pm z_{\alpha/2}\sqrt{\frac{\bar{X}(1-\bar{X})}{n} + \frac{\bar{Y}(1-\bar{Y})}{m}}$ 으로 확장할 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-01" src="https://github.com/user-attachments/assets/7ee05f2b-8bd9-4457-8041-a6c44c9c1d3d" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-02" src="https://github.com/user-attachments/assets/ff4da844-2836-4729-9069-903a16f9ad92" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-03" src="https://github.com/user-attachments/assets/248a2ef0-e4e7-43d8-9318-0cf33ccb5706" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-04" src="https://github.com/user-attachments/assets/ff3baedf-669c-4a49-83b2-dfdb9c974ce4" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-05" src="https://github.com/user-attachments/assets/a1b8a57d-dcd6-4597-892e-b35dd2ff1db6" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-06" src="https://github.com/user-attachments/assets/14cdc0f3-e9c5-4349-afcd-4d811bbb70dd" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-07" src="https://github.com/user-attachments/assets/20009c4b-fb2a-45ec-9781-388b6e2f7218" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-08" src="https://github.com/user-attachments/assets/e09dd006-a68f-4016-95cc-fb8507300fd0" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-09" src="https://github.com/user-attachments/assets/99133c07-f09c-421e-b932-8a2f062de5c5" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-10" src="https://github.com/user-attachments/assets/bfa808f4-fa26-4b1c-bccf-6fc603f28b11" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-11" src="https://github.com/user-attachments/assets/f5773226-5616-42ad-b9d8-f073baf1eb12" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-12" src="https://github.com/user-attachments/assets/fe83d930-7419-4374-b7ee-f950c496bf27" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-13" src="https://github.com/user-attachments/assets/f3aaa4c2-7595-4cae-8002-323eb2f93af5" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-14" src="https://github.com/user-attachments/assets/fece3479-1020-44c1-96d2-c0ba24834140" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-15" src="https://github.com/user-attachments/assets/859e3edc-8608-4e9d-8e07-67911122c52b" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-16" src="https://github.com/user-attachments/assets/6fd1b479-8bc7-4797-b354-7410110e9abd" />
    <img width="1264" height="1635" alt="Mastering Statistics4 Module1-17" src="https://github.com/user-attachments/assets/df4ebaf7-6092-4a4b-92eb-ce4f8156f0c0" />
  </div>
</details>
