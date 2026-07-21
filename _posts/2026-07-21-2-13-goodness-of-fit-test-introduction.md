---
title: "2-13 Goodness-of-Fit Test: Introduction"
date: 2026-07-21 20:43:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, goodness-of-fit, chi-squared]
math: true
---

## 1. 개요 (Overview)

**[KR]** 우리가 데이터를 설명하기 위해 합리적인 분포를 추측하고 관련 파라미터들을 추정했다고 가정해 봅시다. 이제 우리가 세운 가설적 분포와 파라미터가 수용 가능한지(즉, 얼마나 성공적으로 데이터를 설명하는지) 확인하기 위해 공식적인 적합도 검정(Goodness-of-fit test)을 수행합니다. 이때 귀무가설은 $H_0: X$ 가 확률질량/밀도함수 $f(x)$ 를 따른다는 것입니다.

**[EN]** Suppose that we have guessed a reasonable distribution and estimated the relevant parameters. Now we conduct a formal goodness-of-fit test to see just how successful our tools have been, meaning whether our hypothesized distribution and its relevant parameters are acceptable. The null hypothesis is set as $H_0: X$ has the pmf/pdf $f(x)$.

---

## 2. 적합도 검정의 5단계 절차 (5-Step Procedure for Goodness-of-Fit Test)

**[KR]** 적합도 검정 절차는 다음의 다섯 단계로 이루어집니다.

**[EN]** A high-level view of the goodness-of-fit test procedure consists of the following five steps.

*   **Step 1:** 
    *   **[KR]** $f(x)$의 정의역을 $k$개의 집합 $A_1, A_2, \dots, A_k$ 로 나눕니다. ($X$가 이산형이면 서로 다른 점으로, 연속형이면 구간으로 분할합니다.)
    *   **[EN]** Divide the domain of $f(x)$ into $k$ sets, say $A_1, A_2, \dots, A_k$. (These are distinct points if $X$ is discrete, or intervals if $X$ is continuous.)

*   **Step 2:** 
    *   **[KR]** 각 집합에 속하는 실제 관측치의 수($O_i$)를 집계합니다. 만약 $p_i \equiv P(X \in A_i)$ 라고 정의하면, 각 $i = 1, 2, \dots, k$ 에 대해 $O_i \sim Bin(n, p_i)$ 의 분포를 따르게 됩니다.
    *   **[EN]** Tally the actual number of observations that fall in each set. If $p_i \equiv P(X \in A_i)$, then $O_i \sim Bin(n, p_i)$ for $i = 1, 2, \dots, k$.

*   **Step 3:** 
    *   **[KR]** 만약 귀무가설 $H_0$가 참일 경우 각 집합에 속할 것으로 기대되는 관측치의 수($E_i$)를 결정합니다. 이는 $E_i = E[O_i] = n p_i$ 로 계산됩니다.
    *   **[EN]** Determine the expected number of observations that would fall in each set if $H_0$ were true. This is calculated as $E_i = E[O_i] = n p_i$.

*   **Step 4:** 
    *   **[KR]** 실제 관측치 $O_i$와 기대치 $E_i$의 차이를 바탕으로 카이제곱 적합도 검정 통계량 $\chi_0^2$를 계산합니다.
    *   **[EN]** Calculate the chi-squared goodness-of-fit test statistic $\chi_0^2$ based on the differences between the $O_i$'s and $E_i$'s.
    $$ \chi_0^2 \equiv \sum_{i=1}^k \frac{(O_i - E_i)^2}{E_i} $$
   

*   **Step 5:** 
    *   **[KR]** $\chi^2$ 값이 크다는 것은 분포가 잘 맞지 않음(bad fit)을 의미하므로 우측 단측 검정만 수행합니다. $\chi_0^2 > \chi_{\alpha, k-1-s}^2$ 이면 $H_0$를 기각하며, 반대로 $\chi_0^2 \le \chi_{\alpha, k-1-s}^2$ 이면 $H_0$ 기각에 실패하여 수용하게 됩니다.
    *   **[EN]** A large value of $\chi^2$ indicates a bad fit, so we just do a one-sided test. We reject $H_0$ if $\chi_0^2 > \chi_{\alpha, k-1-s}^2$. If $\chi_0^2 \le \chi_{\alpha, k-1-s}^2$, we fail to reject (and grudgingly accept) $H_0$.

---

## 3. 중요한 참고 사항 (Important Remarks)

**[KR]** 가설 검정을 수행할 때 알아두어야 할 추가적인 사항들입니다.

**[EN]** Here are some additional remarks to keep in mind when performing the hypothesis test.

*   **[KR]** 기각역 계산 시 사용되는 $s$는 $f(x)$에서 추정해야 하는 미지의 파라미터 개수입니다. (예를 들어, $X \sim Nor(\mu, \sigma^2)$ 라면 $s=2$ 입니다.)
*   **[EN]** The $s$ in the critical value is the number of unknown parameters from $f(x)$ that have to be estimated. (For example, if $X \sim Nor(\mu, \sigma^2)$, then $s=2$.)

*   **[KR]** 카이제곱 적합도 검정이 잘 작동하려면 모든 $i$에 대해 기대도수 $E_i \ge 5$ 가 되고 전체 표본 크기 $n$이 30 이상이 되도록 구간 $k$와 $n$을 설정하는 것이 좋습니다.
*   **[EN]** The usual recommendation for the test to work is to pick $k$ and $n$ such that $E_i \ge 5$ for all $i$, and $n$ is at least 30.

*   **[KR]** 만약 자유도 $\nu = k-1-s$ 가 매우 클 경우, 표준 정규 분포 분위수 $z_\alpha$를 이용한 다음 근사식을 사용할 수 있습니다.
*   **[EN]** If the degrees of freedom $\nu = k-1-s$ happens to be very big, you can use the following approximation where $z_\alpha$ is the standard normal quantile.
    $$ \chi_{\alpha, \nu}^2 \approx \nu \left[ 1 - \frac{2}{9\nu} + z_\alpha \sqrt{\frac{2}{9\nu}} \right]^3 $$
   

*   **[KR]** 카이제곱 검정 외에도 콜모고로프-스미르노프(Kolmogorov-Smirnov), 앤더슨-달링(Anderson-Darling), 샤피로-윌크(Shapiro-Wilk) 등의 다양한 적합도 검정 방법들이 존재합니다.
*   **[EN]** Other goodness-of-fit tests include Kolmogorov-Smirnov, Anderson-Darling, and Shapiro-Wilk.

---

## 4. 기본 예제 (Baby Example)

**[KR]** 📝 유의수준 $\alpha = 0.05$ 에서 관측치 $X_i$들이 균등 분포 $Unif(0, 1)$를 따르는지 테스트해 봅시다 ($H_0$). 총 $n=1000$ 개의 관측치를 $k=5$ 개의 동일한 길이의 구간으로 나누었습니다.

**[EN]** 📝 Let's test $H_0$: $X_i$'s are $Unif(0, 1)$ with $\alpha = 0.05$. Suppose we have $n=1000$ observations divided into $k=5$ equal-length intervals.

| Interval | $p_i$ | $E_i = np_i$ | $O_i$ (Actual) |
| :--- | :--- | :--- | :--- |
| $[0, 0.2]$ | $0.2$ | $200$ | $179$ |
| $(0.2, 0.4]$ | $0.2$ | $200$ | $208$ |
| $(0.4, 0.6]$ | $0.2$ | $200$ | $222$ |
| $(0.6, 0.8]$ | $0.2$ | $200$ | $199$ |
| $(0.8, 1.0]$ | $0.2$ | $200$ | $192$ |

**[KR]** 차이를 바탕으로 검정 통계량을 계산하면 $\chi_0^2 \equiv \sum_{i=1}^k (O_i - E_i)^2 / E_i = 5.27$ 이 산출됩니다. 
추정해야 할 미지의 파라미터가 없으므로 $s=0$ 이며, 자유도가 4인 카이제곱 임계값은 $\chi_{0.05, 4}^2 = 9.49$ 입니다. 

**[EN]** It turns out that calculating the test statistic yields $\chi_0^2 \equiv \sum_{i=1}^k (O_i - E_i)^2 / E_i = 5.27$. 
Since there are no unknown parameters, $s=0$, and the critical value is $\chi_{0.05, 4}^2 = 9.49$. 

**[결론 / Conclusion]**
**[KR]** $\chi_0^2 \le \chi_{\alpha, k-1-s}^2$ ($5.27 \le 9.49$) 조건을 만족하므로 $H_0$ 기각에 실패합니다. 즉, 관측된 숫자들이 균등 분포를 따른다고 무리 없이 받아들일 수 있습니다.

**[EN]** Since $\chi_0^2 \le \chi_{\alpha, k-1-s}^2$ ($5.27 \le 9.49$), we fail to reject $H_0$. So we will grudgingly pretend that the numbers are uniform.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-13 Goodness-of-Fit Test_ Introduction-1" src="https://github.com/user-attachments/assets/7911f13d-a340-4ec8-9cbf-6b9a03bd22ed" />
    <img width="1264" height="1635" alt="2-13 Goodness-of-Fit Test_ Introduction-2" src="https://github.com/user-attachments/assets/824df646-c7ed-46a8-8853-9716afc11cab" />
  </div>
</details>
