---
title: "2-15 Goodness-of-Fit Tests: Honors Example"
date: 2026-07-21 21:03:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics IV: Confidence Intervals and Hypothesis Tests"]
tags: [probability, statistics, hypothesis-testing, goodness-of-fit, gamma-distribution, weibull-distribution, bisection-method, newtons-method]
math: true
---

## 1. 미니 프로젝트 개요 (Overview of the Mini-Project)

**[KR]** 이전 수업의 마지막 부분에서 다루었던 100개의 관측치 표본 데이터를 사용하여 더 확장된 예제(미니 프로젝트)를 진행해 보겠습니다. 

**[EN]** Let's make things more interesting with an expanded example/mini-project using the same sample of 100 observations from the end of the last lesson. 

**[KR]** 이 데이터셋의 표본 평균은 $\bar{x} = 0.8778$ 이고, 표본 표준편차는 $S = 0.3347$ 입니다. 

**[EN]** The sample mean for this data set is $\bar{x} = 0.8778$, and the sample standard deviation is $S = 0.3347$. 

**[KR]** 본 수업에서는 데이터가 다음 중 어떤 분포에서 추출되었을지 확인하기 위해 유의수준 $\alpha = 0.05$ 와 $k = 10$ 개의 동일 확률 구간을 사용하는 여러 카이제곱 적합도 검정을 수행할 것입니다. 

**[EN]** In this lesson, we will do various goodness-of-fit tests at level $\alpha = 0.05$ with $k = 10$ equal-probability intervals to determine which distribution(s) the data could come from. 

**[KR]** 고려할 가능성들은 다음과 같습니다: 지수 분포(이전 수업에서 기각됨), 감마 분포(지수 분포의 일반화), 와이블 분포(지수 분포의 또 다른 방식의 일반화)입니다.

**[EN]** We'll consider the following possibilities: Exponential (rejected in the previous lesson), Gamma (which generalizes the exponential), and Weibull (which generalizes the exponential in a different way).

---

## 2. 지수 분포 복습 (Exponential Distribution Recap)

**[KR]** 이전 수업에서 우리는 관측치들이 지수 분포 $Exp(\lambda)$를 따른다는 귀무가설을 테스트했고, 처참하게 기각되었습니다. 

**[EN]** In the previous lesson, we tested the null hypothesis that the observations were $Exp(\lambda)$, and recall that we failed miserably. 

**[KR]** 돌이켜보면 이는 일리가 있는 결과입니다. 왜냐하면 히스토그램 그래프가 전혀 지수 분포처럼 보이지 않았고, 지수 분포 확률 변수의 기댓값과 표준편차는 모두 $1/\lambda$ 이어야 하지만 우리의 표본 평균은 $0.8778$, 표본 표준편차는 $0.3347$ 로 차이가 크기 때문입니다.

**[EN]** In retrospect, this makes sense in light of the facts that the graph doesn't look anywhere near exponential, and the expected value and standard deviation of an $Exp(\lambda)$ random variable are both $1/\lambda$, yet the sample mean is $0.8778$ and the sample standard deviation is $0.3347$.

---

## 3. 감마 분포와 이분법 (Gamma Distribution & Bisection Method)

**[KR]** 파라미터 $r$과 $\lambda$를 가지는 감마 분포의 확률밀도함수(pdf)는 $f(x) = \frac{\lambda^r}{\Gamma(r)} x^{r-1} e^{-\lambda x}$ 입니다. 

**[EN]** The Gamma distribution with parameters $r$ and $\lambda$ has pdf $f(x) = \frac{\lambda^r}{\Gamma(r)} x^{r-1} e^{-\lambda x}$. 

**[KR]** 최대우도추정량(MLE)을 구하기 위해 $\hat{\lambda} = \hat{r}/\bar{x}$ 를 설정하고 다이감마 함수(Digamma function)를 근사하여 $g(r) = 0$ 이 되는 해를 찾아야 합니다. 

**[EN]** To find the MLEs, we set $\hat{\lambda} = \hat{r}/\bar{x}$ and must find $\hat{r}$ that solves $g(r) = 0$ by incorporating an approximation for the digamma function. 

**[KR]** 연속 함수의 근을 찾는 쉬운 방법인 이분법(Bisection method)을 사용합니다. 중간값 정리(IVT)를 기반으로 탐색 구간을 계속 반으로 자르며 $r^*$ 에 빠르게 수렴시킵니다. 

**[EN]** Bisection is an easy way to find a zero of any continuous function relying on the Intermediate Value Theorem (IVT), and each iteration chops the search area in two to converge to $r^*$ pretty quickly. 

**[KR]** 데이터에 이분법을 적용한 결과 $\hat{r} = 5.2349$ 및 $\hat{\lambda} = 5.9637$ 을 얻었습니다. 미지의 파라미터를 2개($s=2$) 추정했으므로, 10개의 구간을 활용한 적합도 검정 통계량 $\chi_0^2 = 6.2$ 를 자유도 $k-1-s = 7$ 의 임계값 $\chi_{0.05, 7}^2 = 14.07$ 과 비교합니다. 

**[EN]** Applying bisection to our dataset yields $\hat{r} = 5.2349$ and $\hat{\lambda} = 5.9637$. Since we estimated $s=2$ unknown parameters, we compare the test statistic $\chi_0^2 = 6.2$ against the critical value $\chi_{0.05, 7}^2 = 14.07$. 

**[KR]** 검정 통계량이 임계값보다 작으므로 기각에 실패하며, 이 데이터는 감마 분포일 수도 있다고 인정하게 됩니다.

**[EN]** Since the test statistic is smaller, we fail to reject $H_0$, meaning these may indeed be gamma.

---

## 4. 와이블 분포와 뉴턴법 (Weibull Distribution & Newton's Method)

**[KR]** 와이블 분포의 누적분포함수(cdf)는 $F(x) = 1 - \exp[-(\lambda x)^r]$ 입니다 ($r=1$ 일 경우 지수 분포가 됩니다). 

**[EN]** The Weibull distribution has cdf $F(x) = 1 - \exp[-(\lambda x)^r]$, and note that $r=1$ yields the Exponential as a special case. 

**[KR]** 2개의 미지 파라미터($s=2$)에 대한 MLE를 구하기 위해 우도 함수를 미분하여 연립방정식을 도출합니다. 이분법보다 훨씬 빠른 뉴턴법(Newton's method)을 활용하여 방정식을 풉니다. 

**[EN]** We get the MLEs for the $s=2$ unknown parameters by setting the derivatives of the log-likelihood function to zero and getting simultaneous equations. Let's use Newton's method, which is usually a lot faster than Bisection. 

**[KR]** 초기값 $r_0 = \bar{x}/S = 2.6227$ 로 뉴턴법을 시작하여 $r_{i+1} \leftarrow r_i - g(r_i)/g'(r_i)$ 공식을 반복 업데이트합니다. 수렴 결과 $\hat{r} = 2.8607$ 과 $\hat{\lambda} = 1.0148$ 을 얻었습니다. 

**[EN]** Initializing Newton with $r_0 = \bar{x}/S = 2.6227$, we iteratively update $r_{i+1} \leftarrow r_i - g(r_i)/g'(r_i)$. This results in $\hat{r} = 2.8607$ and $\hat{\lambda} = 1.0148$. 

**[KR]** 동일하게 적합도 검정을 수행하여 $\chi_0^2 = 5.0$ 을 도출했으며, 이는 임계값 $14.07$ 보다 작으므로 귀무가설을 기각하지 못합니다. 따라서 이 관측치들은 와이블 분포를 따른다고 여길 수 있습니다.

**[EN]** Doing a $\chi^2$ g-o-f test yields $\chi_0^2 = 5.0$, which is less than the critical value $14.07$, so we fail to reject $H_0$ and will grudgingly pretend these observations are Weibull.

---

## 5. 진실 공개 (The Big Reveal)

**[KR]** 📝 사실 이 데이터셋의 관측치들은 파라미터 $r=3$, $\lambda=1$ 을 가지는 와이블 분포(Weibull distribution)에서 의도적으로 생성된 것들입니다. 우리의 추정과 적합도 검정 결과가 매우 성공적이었음을 알 수 있습니다!

**[EN]** 📝 The Big Reveal: I actually generated the observations from a Weibull distribution with parameters $r=3$ and $\lambda=1$. So we did pretty well!

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-15 Goodness-of-Fit Tests_ Honors Example-1" src="https://github.com/user-attachments/assets/882d5fb7-b2b5-459b-bf21-065673701ee2" />
    <img width="1264" height="1635" alt="2-15 Goodness-of-Fit Tests_ Honors Example-2" src="https://github.com/user-attachments/assets/6f4747fe-5a42-4064-b769-cd1c8a2ddcb9" />
    <img width="1264" height="1635" alt="2-15 Goodness-of-Fit Tests_ Honors Example-3" src="https://github.com/user-attachments/assets/96353c31-5a7c-4287-8258-e55b3bd521f0" />
    <img width="1264" height="1635" alt="2-15 Goodness-of-Fit Tests_ Honors Example-4" src="https://github.com/user-attachments/assets/e7a30feb-a782-42e3-a173-dcc1ce4e29cf" />
    <img width="1264" height="1635" alt="2-15 Goodness-of-Fit Tests_ Honors Example-5" src="https://github.com/user-attachments/assets/67e7519a-74a4-4604-acdc-3236b2b0290b" />
    <img width="1264" height="1635" alt="2-15 Goodness-of-Fit Tests_ Honors Example-6" src="https://github.com/user-attachments/assets/2d05f542-9a23-45ad-bf4b-9a9275e16751" />
  </div>
</details>
