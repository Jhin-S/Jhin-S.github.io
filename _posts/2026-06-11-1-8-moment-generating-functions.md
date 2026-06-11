---
title: "1-8 Moment Generating Functions"
date: 2026-06-11 11:05:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, mgf, moment, skewness, kurtosis]
math: true
---

## 1. 적률의 통계적 의미 (Concept of Moments)

**[KR]** 통계학에서 확률 변수의 분포 형태를 파악하기 위해 사용하는 지표가 바로 **적률(Moment)**입니다. 기준점에 따라 원점 적률(Raw moment, $E[X^k]$)과 중심 적률(Central moment, $E[(X-\mu)^k]$)로 나뉩니다. 차수 $k$가 커질수록 분포의 미세한 형태적 특징을 잡아냅니다.

**[EN]** In statistics, **Moments** are quantitative measures used to describe the shape of a probability distribution. They are categorized into raw moments (calculated from zero, $E[X^k]$) and central moments (calculated from the mean, $E[(X-\mu)^k]$). As the order $k$ increases, moments capture more specific shape characteristics of the distribution.

* **1차 원점 적률 ($k=1$): 평균 (Mean).** 확률 분포의 무게 중심이 어디에 위치하는지를 나타냅니다.
* **2차 중심 적률 ($k=2$): 분산 (Variance).** 값들이 평균을 중심으로 좌우로 얼마나 넓게 퍼져 있는지를 측정합니다.
* **3차 중심 적률 ($k=3$): 왜도 (Skewness).** 분포의 비대칭성을 나타냅니다. 양수나 음수 값을 가지며, 한쪽 꼬리가 얼마나 더 길게 늘어져 있는지를 보여줍니다.
* **4차 중심 적률 ($k=4$): 첨도 (Kurtosis).** 분포의 꼬리(tail) 부분에 극단적인 값(이상치)이 얼마나 두껍게 존재하는지, 즉 뾰족한 정도를 나타냅니다.

---

## 2. 적률 생성 함수 (Moment Generating Function, MGF)

**[KR]** 복잡한 적분이나 급수 계산 없이, 단순히 미분만 여러 번 수행하여 원하는 차수의 적률을 쉽게 뽑아낼 수 있도록 고안된 마법 같은 함수가 바로 **적률 생성 함수(MGF)**입니다. 확률 변수 $X$에 대한 함수가 아니라, 새로운 매개변수 $t$에 대한 함수로 정의됩니다.

**[EN]** The **Moment Generating Function (MGF)** is an ingenious mathematical tool designed to easily extract moments of any order by simply differentiating the function, bypassing complex integrals or sums. It is defined as a function of a new parameter $t$, not $X$.

$$
M_X(t) \equiv E[e^{tX}]
$$

### 대표적인 확률 분포의 MGF 도출 (Examples)
1. **베르누이 분포 (Bernoulli Distribution):** $X \sim Bern(p)$
   성공(1) 확률이 $p$, 실패(0) 확률이 $q$일 때 기댓값의 정의를 적용합니다.
   $$M_X(t) = E[e^{tX}] = e^{t \cdot 1}p + e^{t \cdot 0}q = pe^t + q$$

2. **지수 분포 (Exponential Distribution):** $X \sim Exp(\lambda)$
   $$M_X(t) = \int_{0}^{\infty} e^{tx} \lambda e^{-\lambda x} \,dx = \lambda \int_{0}^{\infty} e^{(t-\lambda)x} \,dx = \frac{\lambda}{\lambda - t} \quad (\text{단, } t < \lambda)$$

---

## 3. MGF의 대정리: 미분을 통한 적률 추출 (The Big Theorem)

**[KR]** 적률 생성 함수를 매개변수 $t$에 대해 $k$번 미분한 뒤 $t=0$을 대입하면, 정확하게 $X$의 $k$차 원점 적률($E[X^k]$)이 도출됩니다. 이 원리는 자연 상수 $e^{tx}$의 테일러(매클로린) 급수 전개와 기댓값의 선형성을 통해 수학적으로 아름답게 증명됩니다.

**[EN]** By differentiating the MGF $k$ times with respect to $t$ and then evaluating it at $t=0$, we obtain exactly the $k$-th raw moment of $X$ ($E[X^k]$). This elegant principle is proven using the Taylor (Maclaurin) series expansion of $e^{tx}$ combined with the linearity of expectation.

$$
E[X^k] = \left. \frac{d^k}{dt^k} M_X(t) \right|_{t=0} = M_X^{(k)}(0)
$$

**[증명 과정 요약 / Proof Sketch]**
1. $e^{tX} = 1 + tX + \frac{(tX)^2}{2!} + \frac{(tX)^3}{3!} + \dots$ 로 급수 전개합니다.
2. 양변에 기댓값 $E[\cdot]$를 취하고, 상수인 $t$를 기댓값 밖으로 빼냅니다.
   $M_X(t) = 1 + tE[X] + \frac{t^2}{2!}E[X^2] + \frac{t^3}{3!}E[X^3] + \dots$
3. 이 식을 $t$에 대해 미분하면 상수항은 사라지고, $t=0$을 대입하면 첫 번째 항인 $E[X^k]$만 오롯이 남게 됩니다.

### MGF를 활용한 지수 분포의 분산 계산
앞서 구한 지수 분포의 MGF $M_X(t) = \lambda(\lambda - t)^{-1}$ 를 연속으로 미분해 봅니다.
* $E[X] = M_X'(0) = \left. \frac{\lambda}{(\lambda - t)^2} \right|_{t=0} = \frac{1}{\lambda}$
* $E[X^2] = M_X''(0) = \left. \frac{2\lambda}{(\lambda - t)^3} \right|_{t=0} = \frac{2}{\lambda^2}$
* $Var(X) = E[X^2] - (E[X])^2 = \frac{2}{\lambda^2} - \frac{1}{\lambda^2} = \frac{1}{\lambda^2}$

---

## 4. 선형 변환과 MGF의 성질 (MGF of a Linear Function)

**[KR]** 확률 변수 $X$에 상수배를 하거나 더하는 선형 변환($Y = aX + b$)을 취했을 때, 새로운 변수 $Y$의 MGF는 원래 $X$의 MGF를 변형하여 아주 쉽게 구할 수 있습니다.

**[EN]** When a linear transformation ($Y = aX + b$) is applied to a random variable $X$, the MGF of the new variable $Y$ can be easily expressed in terms of the original MGF of $X$.

$$
M_{aX+b}(t) = E[e^{t(aX+b)}] = e^{tb} E[e^{(at)X}] = e^{tb} M_X(at)
$$

* **예제:** $X \sim Exp(\lambda)$ 일 때, $Y = 3X + 2$ 의 MGF를 구해보면 다음과 같습니다.
  $$M_Y(t) = e^{2t} M_X(3t) = e^{2t} \frac{\lambda}{\lambda - 3t}$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-8 Moment Generating Functions-1" src="https://github.com/user-attachments/assets/7be04ce1-fcb0-4ccf-9fb4-09e3640b78cd" />
    <img width="1264" height="1635" alt="1-8 Moment Generating Functions-2" src="https://github.com/user-attachments/assets/eeae05c9-1091-49a2-801f-56a7dd6d68b8" />
    <img width="1264" height="1635" alt="1-8 Moment Generating Functions-3" src="https://github.com/user-attachments/assets/a7a8f361-f297-4c78-9a2c-7ead75c3db74" />
    <img width="1264" height="1635" alt="1-8 Moment Generating Functions-4" src="https://github.com/user-attachments/assets/434dced5-2203-4b21-8979-5271ef46ac3a" />
    <img width="1264" height="1635" alt="1-8 Moment Generating Functions-5" src="https://github.com/user-attachments/assets/b0c0c9e0-1b65-41e1-9fbe-916bd24050fc" />
    <img width="1264" height="1635" alt="1-8 Moment Generating Functions-6" src="https://github.com/user-attachments/assets/193519d1-d7bf-4fc0-ab2b-9779b2bd8872" />
    <img width="1264" height="1635" alt="1-8 Moment Generating Functions-7" src="https://github.com/user-attachments/assets/79d63006-ba62-4a01-8260-76e1294902c4" />
  </div>
</details>
