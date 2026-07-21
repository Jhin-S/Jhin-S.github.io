---
title: "2-12 Two-Sample Bernoulli Proportions Test"
date: 2026-07-21 20:11:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, two-sample, bernoulli-distribution, proportion, z-test]
math: true
---

## 1. 개요 및 합동 추정량 (Overview and Pooled Estimator)

**[KR]** 서로 독립적인 두 베르누이 표본 $X_1, X_2, \dots, X_n \sim Bern(p_x)$ 와 $Y_1, Y_2, \dots, Y_m \sim Bern(p_y)$ 가 있다고 가정해 봅시다. 우리는 두 성공 파라미터의 차이인 $p_x - p_y$ 에 대한 가설을 검정하고자 합니다.

**[EN]** Suppose that $X_1, X_2, \dots, X_n \sim Bern(p_x)$ and $Y_1, Y_2, \dots, Y_m \sim Bern(p_y)$ are two independent Bernoulli samples. Now we are interested in testing hypotheses about the difference in the success parameters, $p_x - p_y$.

**[KR]** 양측 검정의 가설은 $H_0: p_x = p_y$ 대 $H_1: p_x \neq p_y$ 로 설정됩니다. 귀무가설 $H_0$가 참이라면 $p \equiv p_x = p_y$ 이며, 미지의 공통 비율 $p$를 추정하기 위해 두 표본을 합친 합동 추정량(Pooled estimator) $\hat{p}$를 다음과 같이 정의합니다.

**[EN]** The two-sided test hypotheses are set as $H_0: p_x = p_y$ versus $H_1: p_x \neq p_y$. If $H_0$ is true, then $p \equiv p_x = p_y$, and to estimate the unknown common proportion $p$, we define the pooled estimator $\hat{p}$ by combining both samples as follows.

$$ \hat{p} = \frac{\sum_{i=1}^n X_i + \sum_{j=1}^m Y_j}{n + m} $$


---

## 2. 검정 통계량과 가설 검정 (Test Statistic and Hypothesis Testing)

**[KR]** 중심극한정리(CLT)와 이전 모듈의 신뢰 구간 원리에 따라 표본 크기가 클 때 표본 평균은 정규 분포로 근사할 수 있습니다. 방금 구한 합동 추정량 $\hat{p}$를 식에 대입하면 우리가 최종적으로 사용할 수 있는 검정 통계량 $Z_0$를 얻게 됩니다.

**[EN]** By the CLT and our confidence interval work from the previous module, we know that for large $n$ and $m$, the sample means approximate a normal distribution. Now plug the pooled estimator $\hat{p}$ into the equation to get one last approximation for the test statistic $Z_0$ that we can finally work with.

$$ Z_0 \equiv \frac{\bar{X} - \bar{Y}}{\sqrt{\hat{p}(1-\hat{p})\left[\frac{1}{n} + \frac{1}{m}\right]}} \approx Nor(0, 1) $$


**[KR]** 양측 검정의 경우, $\lvert Z_0 \rvert > z_{\alpha/2}$ 이면 귀무가설 $H_0$를 기각합니다.

**[EN]** Thus, for the two-sided test, we reject $H_0$ if $\lvert Z_0 \rvert > z_{\alpha/2}$.

---

## 3. 단측 검정 (One-Sided Tests)

**[KR]** 단측 검정에 대한 가설과 기각 규칙은 다음과 같습니다.

**[EN]** The hypotheses and rejection rules for one-sided tests are as follows.

*   **[KR] 우측 검정 ($H_0: p_x \le p_y$ vs $H_1: p_x > p_y$):** $Z_0 > z_\alpha$ 일 때 $H_0$ 기각
*   **[EN] Right-sided test ($H_0: p_x \le p_y$ vs $H_1: p_x > p_y$):** Reject $H_0$ if $Z_0 > z_\alpha$

*   **[KR] 좌측 검정 ($H_0: p_x \ge p_y$ vs $H_1: p_x < p_y$):** $Z_0 < -z_\alpha$ 일 때 $H_0$ 기각
*   **[EN] Left-sided test ($H_0: p_x \ge p_y$ vs $H_1: p_x < p_y$):** Reject $H_0$ if $Z_0 < -z_\alpha$

---

## 4. 실전 예제 (Practice Example)

**[KR]** 📝 고객 리뷰를 바탕으로 두 레스토랑을 비교해 봅니다. 버거 폴-A(Burger Fol-A)는 $n=260$ 개의 리뷰 중 178개의 '맛있다' 평가를 받았고, 맥웬디스(McWendy's)는 $m=300$ 개의 리뷰 중 250개의 '맛있다' 평가를 받았습니다. 유의수준 $\alpha=0.05$ 에서 $H_0: p_B = p_M$ 대 $H_1: p_B \neq p_M$ 을 테스트합니다.

**[EN]** 📝 Let's compare two restaurants based on customer reviews. Burger Fol-A got 178 yummies out of $n=260$ reviews, while McWendy's got 250 yummies out of $m=300$ reviews. We test $H_0: p_B = p_M$ vs $H_1: p_B \neq p_M$ at level $\alpha=0.05$.

**[KR]** 각 레스토랑의 표본 비율과 합동 추정량은 다음과 같습니다.

**[EN]** The sample proportions and the pooled estimator are as follows.

*   $\bar{B} = \frac{178}{260} = 0.6846$
*   $\bar{M} = \frac{250}{300} = 0.8333$
*   $\hat{p} = \frac{178+250}{260+300} = 0.7643$

**[KR]** 공식에 대입하여 검정 통계량 $Z_0$를 계산합니다.

**[EN]** We calculate the test statistic $Z_0$ by plugging these into the formula.

$$ Z_0 = \frac{0.6846 - 0.8333}{\sqrt{0.7643(0.2357)\left[\frac{1}{260} + \frac{1}{300}\right]}} = -4.135 $$


**[결론 / Conclusion]**
**[KR]** $\lvert Z_0 \rvert = 4.135$ 가 임계값 $z_{0.025} = 1.96$ 보다 크기 때문에 우리는 $H_0$를 쉽게 기각할 수 있으며, 비공식적으로 맥웬디스가 승자라고 선언할 수 있습니다.

**[EN]** Since $\lvert Z_0 \rvert > z_{0.025} = 1.96$, we easily reject $H_0$ and informally declare McWendy's the winner.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-12 Two-Sample Bernoulli Proportions Test-1" src="https://github.com/user-attachments/assets/57ac0bb2-f858-482e-ab4f-15ee4cfe658d" />
    <img width="1264" height="1635" alt="2-12 Two-Sample Bernoulli Proportions Test-2" src="https://github.com/user-attachments/assets/e1b81d0f-9223-47a3-973b-1ddcfea3f33d" />
  </div>
</details>
