---
title: "2-3 Candidate Distributions"
date: 2026-07-14 16:45:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, candidate-distributions, discrete-distributions, continuous-distributions, empirical-distribution]
math: true
---

## 1. 후보 분포 선정 가이드 (Choosing a Candidate Distribution)

**[KR]** 통계 분석을 본격적으로 시작하기 전, 우리가 다루고 있는 데이터가 과연 어떤 확률 분포를 따를지 합리적으로 추측(Informed guess)하는 과정이 필요합니다. 훗날 '적합도 검정(Goodness-of-fit test)'이라는 공식적인 방법론을 통해 이 가설을 검증하겠지만, 그전에 우선 알맞은 후보군을 좁혀야 합니다. 이를 위해 다음과 같은 사전 질문들을 던져보아야 합니다.

**[EN]** Before diving into statistical analysis, we must make an informed guess about the type of probability distribution our data follows. While we will formally verify this later using 'Goodness-of-fit tests', we first need to narrow down the candidates. To do this, we should consider the following preliminary questions:

* 데이터가 이산형(Discrete), 연속형(Continuous), 혹은 혼합형(Mixed)인가?
* 단일 변수(Univariate)인가, 다변수(Multivariate)인가?
* 확보한 데이터의 양은 충분한가?
* 데이터의 본질에 대해 조언을 구할 수 있는 도메인 전문가(Expert)가 있는가?
* 만약 데이터가 거의 없다면, 최소한 직관적으로 가장 그럴듯한 분포를 추측해 낼 수 있는가?

---

## 2. 이산형 확률 분포 후보군 (Discrete Distribution Candidates)

**[KR]** 데이터가 정수로 뚝뚝 끊어지는 이산형이라면, 상황에 맞게 다음과 같은 훌륭하고 친숙한 분포들을 후보로 올릴 수 있습니다.

**[EN]** If the data is discrete, taking on specific integer values, we have a variety of familiar distributions to select from based on the context:

* **베르누이 분포 (Bernoulli):** 오직 성공 아니면 실패 단 두 가지 결과만 존재할 때.
* **이항 분포 (Binomial):** 정해진 횟수($n$번)의 독립 시행 중에서 '성공한 횟수'를 셀 때.
* **기하 분포 (Geometric):** '첫 번째 성공'을 거둘 때까지 반복한 총 시행 횟수를 모델링할 때.
* **음이항 분포 (Negative Binomial):** 첫 번째가 아닌, '여러 번($r$번) 성공'할 때까지 걸린 시행 횟수를 추적할 때.
* **푸아송 분포 (Poisson):** 특정 시간이나 공간 단위 내에서 무작위로 발생하는 사건의 '발생 횟수(건수)'를 셀 때.
* **실증 분포 (Empirical):** 히스토그램에 기반하여, 수학적 모델 대신 수집된 샘플 데이터 그 자체의 형태를 그대로 분포로 사용할 때.

---

## 3. 연속형 확률 분포 후보군 (Continuous Distribution Candidates)

**[KR]** 데이터가 소수점 아래로 연속적으로 이어지는 실수 값을 가진다면, 데이터의 성질이나 도메인 지식에 따라 다음의 분포들을 적용해 볼 수 있습니다.

**[EN]** If the data suggests a continuous distribution taking on any real value within an interval, the following distributions are excellent candidates depending on the data's characteristics and domain knowledge:

* **균등 분포 (Uniform):** 데이터에 대해 아는 정보가 오직 '최솟값'과 '최댓값'뿐이며, 그 사이에서는 모두 동일한 확률로 발생할 것이라 가정할 때.
* **삼각형 분포 (Triangular):** 최솟값과 최댓값에 더하여 '가장 빈번하게 발생할 최빈값(Most likely value)'까지 알고 있을 때 유용한 대안.
* **지수 분포 (Exponential):** 푸아송 프로세스 상에서 사건과 다음 사건 사이의 '대기 시간'이나 기계의 수명을 모델링할 때.
* **정규 분포 (Normal):** 키, 몸무게, IQ, 표본 평균 등 자연계와 사회 현상에서 가장 흔하게 발견되는 범용적인 종 모양 모델.
* **베타 분포 (Beta):** 비율이나 확률처럼 특정 구간(예: 0과 1 사이)으로 값이 엄격하게 제한되는 데이터를 다룰 때 매우 유연한 도구.
* **감마, 와이블, 굼벨, 로그정규 분포 (Gamma, Weibull, Gumbel, Lognormal):** 꼬리가 비대칭적으로 길거나, 기계의 고장 및 수명을 다루는 신뢰성 공학(Reliability engineering) 모델링에 탁월.
* **실증 분포 (Empirical):** 이산형과 마찬가지로, 이론적 배경 없이 수집된 연속형 샘플 데이터 자체를 만능으로 활용할 때.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-3 Candidate Distributions-1" src="https://github.com/user-attachments/assets/d5be2449-0dff-4c1f-80ba-a5d8e5f5a6d1" />

  </div>
</details>
