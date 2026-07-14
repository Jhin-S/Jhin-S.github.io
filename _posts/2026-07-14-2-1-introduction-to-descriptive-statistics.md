---
title: "2-1 Introduction to Descriptive Statistics"
date: 2026-07-14 16:30:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, descriptive-statistics, data-types, histogram, sampling]
math: true
---

## 1. 기술 통계학의 본질 (The Essence of Descriptive Statistics)

**[KR]** 통계학은 결과가 정해지지 않은 불확실한 현실 속에서, 관측되거나 실험을 통해 얻은 데이터를 바탕으로 가장 합리적이고 논리적인 의사결정을 내릴 수 있도록 돕는 학문입니다. 단일 집단을 심층적으로 분석하거나 여러 집단의 특성을 서로 비교할 때 매우 강력한 도구로 사용됩니다. 
가장 핵심적인 아이디어는 무수히 많은 '모집단(Population)' 전체를 하나하나 조사하는 것이 현실적으로 불가능하기 때문에, 그중 일부인 **'표본(Sample)'을 추출하여 전체의 특성을 과학적으로 추론**한다는 점입니다.

**[EN]** Statistics provides a rational and logical foundation for making decisions under uncertainty, relying on observed or experimental data. It serves as a powerful tool whether you are deeply analyzing a single population or comparing the characteristics of multiple groups. 
The core idea is that since it is practically impossible to survey an infinitely large 'Population' in its entirety, we extract a smaller **'Sample' to scientifically infer the traits of the whole**.

---

## 2. 데이터의 3가지 유형 (Types of Data)

**[KR]** 통계 분석의 대상이 되는 데이터는 그 본질적인 성질에 따라 크게 세 가지 형태로 분류됩니다.
1. **연속형 데이터 (Continuous Variables):** 특정 구간 내에서 끊어짐 없이 어떠한 실수 값이라도 가질 수 있는 데이터입니다. (예: 전구의 수명, 신생아의 몸무게, 사람의 키)
2. **이산형 데이터 (Discrete Variables):** 소수점 아래로 쪼갤 수 없으며, 뚝뚝 끊어진 특정한 정수 값만 가질 수 있는 데이터입니다. (예: 주사위를 굴린 눈의 수, 일주일 동안 공장에서 발생한 불량품의 개수)
3. **범주형 데이터 (Categorical Variables):** 수치적인 크기나 양을 나타내는 것이 아니라, 특성이나 카테고리를 분류하는 데이터입니다. (예: 가장 좋아하는 TV 프로그램, 혈액형)

**[EN]** The data subjected to statistical analysis is broadly classified into three types based on its intrinsic nature:
1. **Continuous Variables:** Data that can take any real number value within a specific interval without interruption. (e.g., the lifespan of a lightbulb, a newborn's weight, human height)
2. **Discrete Variables:** Data that cannot be divided into fractions and can only take specific, distinct integer values. (e.g., the outcome of a dice roll, the number of defective products in a factory this week)
3. **Categorical Variables:** Data that represents categories or traits rather than numerical magnitude or quantity. (e.g., favorite TV show, blood type)

---

## 3. 데이터 시각화와 히스토그램 (Data Visualization & Histograms)

**[KR]** "백문이 불여일견"이라는 말처럼, 복잡한 수식을 적용하기 전에 가장 먼저 해야 할 최우선 작업은 데이터를 눈으로 볼 수 있게 **시각화(Plotting)**하는 것입니다. 그래프를 그려보면 비정상적인 분포, 누락된 값, 혹은 전체 흐름을 벗어나는 이상치(Outlier) 등을 직관적으로 즉시 파악할 수 있습니다.

데이터의 전체적인 윤곽을 가장 빠르고 효과적으로 보여주는 도구가 바로 **히스토그램(Histogram)**입니다. 충분히 많은 양의 데이터를 모아 히스토그램을 그리면, 결국 실제 모집단이 가진 진짜 분포의 모양에 부드럽게 수렴하게 됩니다. 
단, 히스토그램을 그릴 때는 막대(Bin/Cell)의 개수를 설정하는 것이 매우 중요합니다. 막대를 너무 적게 만들면 데이터의 특징이 뭉개지고, 너무 많이 만들면 노이즈가 심해지므로, 골디락스(Goldilocks) 원칙처럼 데이터의 특성을 가장 잘 보여주는 **'딱 알맞은(Just right)' 개수**를 찾는 것이 통계적 감각의 핵심입니다.

**[EN]** As the saying goes, "A picture is worth a thousand words." Before diving into complex equations, the absolute first step is **plotting the data**. Visualizing data allows you to immediately and intuitively spot unusual distributions, missing values, or outliers that deviate from the overall trend.

The **Histogram** is the fastest and most effective tool for revealing the overall contour of your data. If you gather a sufficiently large number of observations, the histogram will eventually converge smoothly to the true shape of the population's distribution.
However, when constructing a histogram, choosing the number of bins (cells) is critical. If you use too few bins, the data's features get washed out; if you use too many, the plot becomes overly noisy. Applying the Goldilocks principle to find the **'just right' number** that best showcases the data's characteristics is the essence of good statistical intuition.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-1 Introduction to Descriptive Statistics-1" src="https://github.com/user-attachments/assets/b272e437-04c4-4253-bae9-34ea9297c982" />
    <img width="1264" height="1635" alt="2-1 Introduction to Descriptive Statistics-2" src="https://github.com/user-attachments/assets/3c3abd6b-2d59-444e-92c2-96c9d545fd8b" />
  </div>
</details>
