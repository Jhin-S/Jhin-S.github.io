---
title: "2-2 The Error of Our Ways"
date: 2026-07-21 12:58:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, type-I-error, type-II-error, power]
math: true
---

## 1. 4가지 가능한 결과 (Four Possible Outcomes)

**[KR]** 가설 검정 과정에서 우리는 어떤 실수를 저지를 수 있을까요? 결정을 내릴 때 총 4가지 상황이 발생할 수 있습니다.
* 귀무가설($H_0$)이 실제로 참일 때 참이라고 결론 내리는 것은 좋은 결정입니다.
* 귀무가설($H_0$)이 실제로 거짓일 때 거짓이라고 결론 내리는 것 또한 좋은 결정입니다.
* 하지만 $H_0$가 참인데 거짓이라고 결론 내리는 것은 나쁜 결정이며, 이를 **1종 오류(Type I error)**라 부릅니다.
* 반대로 $H_0$가 거짓인데 참이라고 결론 내리는 것 역시 나쁜 결정이며, 이를 **2종 오류(Type II error)**라고 부릅니다.

**[EN]** Where can we go wrong in hypothesis testing? Four things can happen.
* If $H_0$ is actually true and we conclude that it's true, that is good.
* If $H_0$ is actually false and we conclude that it's false, that is also good.
* However, if $H_0$ is actually true and we conclude that it's false, it is bad, and this is called a **Type I error**.
* Conversely, if $H_0$ is actually false and we conclude that it's true, it is also bad, and this is known as a **Type II error**.

---

## 2. 의사결정 매트릭스와 예시 (Decision Matrix and Examples)

**[KR]** 이러한 상황들을 자연의 상태(실제 진실)와 우리의 결정에 따라 표로 나타내면 다음과 같습니다.
**[EN]** This can be represented in the following matrix based on the state of nature and our decision.

| State of nature \ Decision | Accept $H_0$ | Reject $H_0$ |
| :--- | :--- | :--- |
| **$H_0$ true** | Correct | Type I error |
| **$H_0$ false** | Type II error | Correct |

**[KR] 예시 (Examples):** 
* **1종 오류:** 시장에 있는 기존 약보다 성능이 열등한 새로운 약을 더 좋다고 잘못 결론 내리는 경우입니다.
* **2종 오류:** 기존 약보다 훨씬 우수한 새로운 약을 더 나쁘다고 잘못 결론 내리는 경우입니다.

**[EN] Examples:**
* **Type I error:** We incorrectly conclude that a new, inferior drug is better than the drug currently on the market.
* **Type II error:** We incorrectly conclude that a new, superior drug is worse than the drug currently on the market.

---

## 3. 오류의 확률과 검정력 (Probabilities of Errors and Power)

**[KR]** 우리는 이 두 가지 오류가 발생할 확률을 통제하고 유지하고자 합니다.
* 1종 오류가 발생할 확률은 $P(\text{Type I error}) = P(\text{Reject } H_0 | H_0 \text{ true}) \le \alpha$ 로 정의됩니다.
* 2종 오류가 발생할 확률은 $P(\text{Type II error}) = P(\text{Fail to reject } H_0 | H_0 \text{ false}) \le \beta$ 로 정의됩니다.

우리는 $\alpha$와 $\beta$를 직접 선택하며, 당연히 $\alpha + \beta < 1$ 이 되어야 합니다. 일반적으로 통계학에서는 1종 오류가 2종 오류보다 훨씬 더 치명적이고 나쁜 것으로 간주됩니다.

**[EN]** We want to keep the probabilities of these errors under control.
* The probability of a Type I error is expressed as $P(\text{Type I error}) = P(\text{Reject } H_0 | H_0 \text{ true}) \le \alpha$.
* The probability of a Type II error is expressed as $P(\text{Type II error}) = P(\text{Fail to reject } H_0 | H_0 \text{ false}) \le \beta$.

We choose $\alpha$ and $\beta$, and of course, we need to have $\alpha + \beta < 1$. Usually, a Type I error is considered to be much worse than a Type II error.

**[KR] 핵심 정의 (Key Definitions):**
* 1종 오류의 확률인 $\alpha$는 검정의 **'크기(Size)'** 또는 **'유의수준(Level of significance)'**이라고 부릅니다.
* 가설 검정의 **'검정력(Power)'**은 $1 - \beta = P(\text{Reject } H_0 | H_0 \text{ false})$ 로 정의되며, 이 검정력이 높은 것은 매우 좋은 것입니다.

**[EN] Key Definitions:**
* The probability of a Type I error, $\alpha$, is called the **size** or **level of significance** of the test.
* The **power** of a hypothesis test is defined as $1 - \beta = P(\text{Reject } H_0 | H_0 \text{ false})$, and it is good to have high power.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-2 The Error of Our Ways-1" src="https://github.com/user-attachments/assets/c7b9c9d4-afa6-47ca-b0f2-506d2ea924f5" />
  </div>
</details>
