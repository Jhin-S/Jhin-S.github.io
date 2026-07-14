---
title: "2-2 Summarizing Data"
date: 2026-07-14 16:30:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, descriptive-statistics, mean, median, variance, standard-deviation]
math: true
---

## 1. 데이터의 시각적 요약 (Visual Summaries of Data)

**[KR]** 수집한 원본 데이터(Raw Data)가 너무 많을 때는 단순히 나열하는 것만으로는 의미를 파악하기 어렵습니다. 이때 **'줄기-잎 그림(Stem-and-Leaf Diagram)'**을 사용하면 원본 데이터의 정확한 숫자 값을 그대로 보존하면서도, 마치 옆으로 눕힌 히스토그램처럼 데이터의 전체적인 분포 모양을 한눈에 볼 수 있어 공간을 절약하고 직관성을 높일 수 있습니다. 또한 데이터 값들을 특정 구간(Interval)으로 묶어 **'도수분포표(Grouped Data Frequency Table)'**를 만들면 방대한 데이터의 흐름을 빠르게 요약할 수 있습니다.

**[EN]** When you have a massive amount of raw data, simply listing it makes it difficult to extract meaningful insights. In such cases, a **'Stem-and-Leaf Diagram'** is an excellent tool. It preserves the exact numerical values of the raw data while displaying the overall distribution shape like a sideways histogram, saving space and enhancing intuitiveness. Furthermore, organizing data into specific intervals to create a **'Grouped Data Frequency Table'** allows for a rapid summary of large datasets.

---

## 2. 중심 경향성 지표 (Measures of Central Tendency)

**[KR]** 데이터가 어디를 중심으로 모여 있는지를 나타내는 대푯값에는 크게 세 가지가 있습니다.
* **표본 평균 (Sample Mean, $\bar{X}$):** 모든 관측치를 더한 뒤 데이터의 개수 $n$으로 나눈 값입니다.
* **표본 중앙값 (Sample Median):** 데이터를 크기순으로 일렬로 세웠을 때 가장 정중앙에 위치한 값입니다. 평균과 달리 극단적인 **이상치(Outlier)의 영향을 거의 받지 않는다는 강력한 장점**이 있습니다. (예: 데이터가 7, 7, 7, 672, 7 일 때, 평균은 무려 140으로 왜곡되지만 중앙값은 7로 데이터의 진짜 중심을 잘 대변합니다.)
* **표본 최빈값 (Sample Mode):** 데이터 중에서 가장 자주(많이) 등장한 값입니다.

**[EN]** There are three primary metrics to represent where the center of mass of your data lies:
* **Sample Mean ($\bar{X}$):** The arithmetic average, calculated by summing all observations and dividing by the total count $n$.
* **Sample Median:** The exact middle value when the data is sorted in numerical order. Unlike the mean, it has the powerful advantage of being **highly robust against extreme outliers**. (e.g., For the dataset 7, 7, 7, 672, 7, the mean is heavily distorted to 140, but the median perfectly represents the true center at 7.)
* **Sample Mode:** The most frequently occurring value in the dataset.

---

## 3. 산포도 지표 (Measures of Variation / Spread)

**[KR]** 데이터가 중심(평균)으로부터 얼마나 넓게 흩어져 있는지를 나타내는 지표들입니다.
* **표본 분산 (Sample Variance, $S^2$):** 각 데이터가 평균으로부터 떨어진 거리(편차)를 제곱하여 더한 값입니다. 이때 $n$이 아닌 **$n-1$로 나누어 주는데**, 이는 모집단의 실제 분산을 편향(Bias) 없이 더 정확하게 추정하기 위한 통계학적 조치입니다. 수식을 전개하면 계산을 훨씬 빠르게 할 수 있는 변형 공식을 얻을 수 있습니다.
  
$$
S^2 = \frac{1}{n-1}\sum_{i=1}^n (X_i - \bar{X})^2 = \frac{1}{n-1}\left( \sum_{i=1}^n X_i^2 - n\bar{X}^2 \right)
$$

* **표본 표준편차 (Sample Standard Deviation, $S$):** 표본 분산에 양의 제곱근($+\sqrt{S^2}$)을 취한 값으로, 원래 데이터와 동일한 단위를 가지게 되어 직관적인 해석이 가능해집니다.
* **표본 범위 (Sample Range):** 데이터의 최댓값에서 최솟값을 뺀 단순한 간격($\max X_i - \min X_i$)입니다.

---

## 4. 그룹화된 데이터의 통계량 계산 (Calculations for Grouped Data)

**[KR]** 원본 데이터가 모두 주어지지 않고, 이미 도수분포표나 구간(Interval) 형태로 요약된 데이터만 가지고 있을 때도 통계량을 훌륭하게 근사해 낼 수 있습니다. 특정 값($X_i$)이나 구간의 중간값(Midpoint, $m_j$)에 해당 구간의 빈도수(Frequency, $f_j$)를 곱해주면 됩니다.

**[EN]** Even when you don't have access to the raw data and only possess summarized grouped data (like intervals or frequency tables), you can still brilliantly approximate the statistics. You simply multiply the specific value ($X_i$) or the midpoint of an interval ($m_j$) by its corresponding frequency ($f_j$).

* **그룹화된 표본 평균:**
  
$$
\bar{X} \approx \frac{\sum_{j=1}^c f_j m_j}{n}
$$

* **그룹화된 표본 분산:**
  
$$
S^2 \approx \frac{\sum_{j=1}^c f_j m_j^2 - n\bar{X}^2}{n-1}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-2 Summarizing Data-1" src="https://github.com/user-attachments/assets/b5f35e98-37cc-4dc3-a521-d22f6f03de43" />
    <img width="1264" height="1635" alt="2-2 Summarizing Data-2" src="https://github.com/user-attachments/assets/f058ed4c-9c89-49e9-858f-15b0771282cb" />
    <img width="1264" height="1635" alt="2-2 Summarizing Data-3" src="https://github.com/user-attachments/assets/e558b95f-2e18-4a75-874d-60c1ccd168ab" />
  </div>
</details>
