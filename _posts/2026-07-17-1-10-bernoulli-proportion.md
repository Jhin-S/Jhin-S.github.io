---
title: "1-10 Bernoulli Proportion"
date: 2026-07-17 10:14:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, bernoulli-distribution, proportion, confidence-interval, central-limit-theorem]
math: true
---

## 1. 베르누이 모비율의 추정과 중심극한정리 (Bernoulli Proportion & CLT)

**[KR]** 결과가 성공 또는 실패로만 나뉘는 베르누이 분포 $Bern(p)$에서, 우리가 궁극적으로 알고 싶은 것은 진짜 '성공 확률(Proportion, $p$)'입니다. $n$번의 독립적인 시행을 거친 표본 데이터 $X_1, \dots, X_n$이 있을 때, 표본 평균 $\bar{X}$의 기댓값은 $E[\bar{X}] = p$ 이며 분산은 $Var(\bar{X}) = pq/n$ 입니다. 
표본의 크기 $n$이 충분히 크다고 가정하면(복잡한 이항 분포표를 보지 않기 위해), **중심극한정리(Central Limit Theorem)**에 의해 표본 평균의 분포를 정규 분포로 근사할 수 있습니다. 

**[EN]** In a Bernoulli distribution $Bern(p)$ where outcomes are strictly success or failure, the ultimate target we want to estimate is the true 'probability of success (Proportion, $p$)'. Given independent sample data $X_1, \dots, X_n$ from $n$ trials, the expected value of the sample mean is $E[\bar{X}] = p$ and its variance is $Var(\bar{X}) = pq/n$. 
Assuming the sample size $n$ is sufficiently large (to avoid dealing with nasty Binomial tables), the **Central Limit Theorem (CLT)** allows us to approximate the distribution of the sample mean as a normal distribution.

* **피벗(Pivot) 통계량의 도출:**
  표준화 공식을 적용하면 $\frac{\bar{X} - p}{\sqrt{pq/n}} \approx N(0, 1)$ 이 됩니다. 여기서 분모에 포함된 미지의 파라미터 $p$와 $q$를 식에서 제거하기 위해, 이들의 최대 우도 추정량(MLE)인 $\bar{X}$ 와 $(1-\bar{X})$ 로 과감하게 대체하는 트릭을 사용합니다.
  
  $$ \frac{\bar{X} - p}{\sqrt{\bar{X}(1-\bar{X})/n}} \approx N(0, 1) $$
 

---

## 2. 모비율에 대한 근사 신뢰 구간 (Approximate Confidence Interval)

**[KR]** 위에서 도출한 정규 분포 피벗을 이용하여 확률 방정식을 풀면, 모비율 $p$에 대한 근사 신뢰 구간 공식을 얻을 수 있습니다.

**[EN]** By solving the probability equation using the normal distribution pivot derived above, we can obtain the approximate confidence interval formula for the population proportion $p$.

* **$100(1-\alpha)\%$ 양측 신뢰 구간 (Two-sided CI):**
  $$ p \in \bar{X} \pm z_{\alpha/2} \sqrt{\frac{\bar{X}(1-\bar{X})}{n}} $$
 
* **하한 단측 (One-sided Lower):** $p \ge \bar{X} - z_{\alpha} \sqrt{\frac{\bar{X}(1-\bar{X})}{n}}$
* **상한 단측 (One-sided Upper):** $p \le \bar{X} + z_{\alpha} \sqrt{\frac{\bar{X}(1-\bar{X})}{n}}$

---

## 3. 표본 크기의 결정: 보수적 접근과 사전 연구 (Sample-Size Calculation)

**[KR]** 신뢰 구간의 오차 한계(반폭, $\epsilon$)를 원하는 수준으로 통제하기 위해 필요한 최소 표본 크기 $n$을 계산할 수 있습니다. 공식은 $n \ge (z_{\alpha/2} / \epsilon)^2 \bar{X}(1-\bar{X})$ 로 전개되지만, 실제 실험을 하기 전에는 $\bar{X}$ 값을 알 수 없다는 딜레마가 발생합니다. 이를 해결하기 위한 두 가지 전략이 있습니다.

**[EN]** To control the margin of error (half-width, $\epsilon$) of the confidence interval to a desired level, we must calculate the minimum required sample size $n$. The formula expands to $n \ge (z_{\alpha/2} / \epsilon)^2 \bar{X}(1-\bar{X})$, but we face a dilemma: we don't know the value of $\bar{X}$ before actually conducting the experiment. There are two strategies to resolve this.

1. **보수적 선택 (Conservative Choice):**
   $\bar{X}(1-\bar{X})$ 의 값이 가질 수 있는 수학적 최댓값은 $\bar{X} = 0.5$ 일 때인 $1/4$ 입니다. 이 최댓값을 대입하여 어떤 상황에서도 오차 범위를 만족하도록 가장 보수적으로 표본을 크게 잡는 방법입니다.
   $$ n \ge \frac{z_{\alpha/2}^2}{4\epsilon^2} $$
  
   *(예: 95% 신뢰 수준에서 오차 $\pm 3\%$ 를 원할 때, 최소 1068개의 샘플이 필요합니다.)*
   
2. **사전 추정치 활용 (Pilot Study Estimate):**
   만약 사전 연구나 파일럿 테스트를 통해 모비율에 대한 대략적인 추정치 $\hat{p}$ 를 알고 있다면, 무작정 표본을 크게 잡을 필요 없이 이 값을 대입하여 필요한 표본 크기를 효율적으로 줄일 수 있습니다.
   $$ n \ge \frac{z_{\alpha/2}^2 \hat{p}(1-\hat{p})}{\epsilon^2} $$
  
   *(예: $\hat{p} = 0.7$ 로 예상된다면, 필요한 샘플 개수는 897개로 대폭 줄어듭니다.)*

---

## 4. 두 모비율의 차이에 대한 신뢰 구간 (Difference Between Two Proportions)

**[KR]** 독립적인 두 개의 베르누이 모집단($X$와 $Y$) 간의 성공 확률 차이($p_x - p_y$)를 비교하는 공식 역시 기존의 정규 분포 근사 논리를 그대로 확장하여 도출할 수 있습니다.

**[EN]** The formula for comparing the difference in success probabilities ($p_x - p_y$) between two independent Bernoulli populations ($X$ and $Y$) can also be easily derived by extending the same normal approximation logic.

* **차이에 대한 양측 신뢰 구간:**
  $$ p_x - p_y \in \bar{X} - \bar{Y} \pm z_{\alpha/2} \sqrt{\frac{\bar{X}(1-\bar{X})}{n} + \frac{\bar{Y}(1-\bar{Y})}{m}} $$
 

**[실전 예제: SAT 점수 비교]**
조지아 공대(GT) 학생들과 조지아 대학교(UGA) 학생들 중 SAT 수학에서 700점 이상을 받을 확률을 비교해 봅시다. 
* **GT 데이터:** 200명 중 160명 성공 $\implies \bar{X} = 0.8$
* **UGA 데이터:** 400명 중 50명 성공 $\implies \bar{Y} = 0.125$

위 공식에 대입하여 95% 신뢰 구간을 구하면 $0.8 - 0.125 \pm 1.96 \sqrt{\frac{(0.8)(0.2)}{200} + \frac{(0.125)(0.875)}{400}}$ 로 계산되어, 결과적으로 **$0.675 \pm 0.064$** 라는 신뢰 구간을 얻게 됩니다. 이 구간이 양수 영역에 명확히 존재하므로 GT 학생들의 성적이 훨씬 더 높다는 것을 통계적으로 강력하게 증명할 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-10 Bernoulii Proportion-1" src="https://github.com/user-attachments/assets/5fc1ea41-6001-4f6d-89dd-ce74c53a3857" />
    <img width="1264" height="1635" alt="1-10 Bernoulii Proportion-2" src="https://github.com/user-attachments/assets/263798e9-69a7-47a7-8c68-6fe1552fa01d" />
    <img width="1264" height="1635" alt="1-10 Bernoulii Proportion-3" src="https://github.com/user-attachments/assets/efbbd090-3e3e-4b63-bc52-74a481df9326" />
  </div>
</details>
