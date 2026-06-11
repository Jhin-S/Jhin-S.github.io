---
title: "1-9 Some Probability Inequalities"
date: 2026-06-11 11:23:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, markov-inequality, chebyshev-inequality, chernoff-bound]
math: true
---

## 1. 마르코프 부등식 (Markov's Inequality)

**[KR]** 마르코프 부등식은 확률 변수가 가질 수 있는 값이 항상 양수일 때, 특정 기준치를 넘어서는 극단적인 값의 비율이 상한선을 가진다는 것을 보여주는 가장 기본적인 부등식입니다. 

예를 들어, 학생들의 평균 용돈이 100만 원이라고 할 때(마이너스 용돈은 없음), 용돈을 평균의 2배인 200만 원 이상 받는 학생은 아무리 많아도 전체의 $\frac{1}{2}$을 절대 넘을 수 없습니다. 만약 넘는다면 애초에 평균이 100만 원이 될 수 없기 때문입니다.

**[EN]** Markov's Inequality provides a fundamental upper bound for the probability that a non-negative random variable exceeds a certain positive value. 

For instance, if the average allowance of a group of students is 1 million won (and allowance cannot be negative), the proportion of students receiving 2 million won or more can never exceed 50%. If it did, the overall average would mathematically have to be higher than 1 million won.

* **조건:** $X \ge 0$, $c > 0$
* **공식:**
  
$$
P(X \ge c) \le \frac{E[X]}{c}
$$

---

## 2. 체비셰프 부등식 (Chebyshev's Inequality)

**[KR]** 체비셰프 부등식은 분산($\sigma^2$)의 개념을 도입하여, 데이터가 평균($\mu$)으로부터 특정 거리($c$) 이상 멀어질 확률의 최댓값을 규정합니다. 마르코프 부등식의 변수에 $(X - \mu)^2$를 대입하여 유도됩니다.

평균대(시소)에 100명의 학생이 앉아있다고 상상해 봅시다. 전체의 분산이 이미 고정되어 있다면, 중심(평균)에서 아주 멀리 떨어진 곳에 많은 학생이 앉을 수 없습니다. 조금만 멀리 앉아도 거리의 제곱에 비례하여 분산이 폭발적으로 커지기 때문입니다. 즉, 체비셰프 부등식은 **"분산이 일정할 때, 평균에서 멀리 떨어진 데이터의 비율은 철저히 제한된다"**는 것을 수학적으로 증명합니다.

**[EN]** Chebyshev's Inequality uses the variance ($\sigma^2$) to bound the probability that a random variable deviates from its mean ($\mu$) by more than a specific distance ($c$). It is derived by applying Markov's Inequality to $(X - \mu)^2$.

Imagine a balance beam with fixed variance. Students cannot sit too far from the center in large numbers, because variance scales with the square of the distance. Thus, Chebyshev guarantees that **"as long as the variance is fixed, the proportion of data located far from the mean is strictly capped."**

* **공식:**
  
$$
P(|X - \mu| \ge c) \le \frac{\sigma^2}{c^2}
$$

### 체비셰프 부등식의 보수성 (Conservative Nature)
$X \sim Unif(0, 1)$인 균등 분포를 예로 들어봅시다. (평균 $\mu = \frac{1}{2}$, 분산 $\sigma^2 = \frac{1}{12}$)
만약 $c = \frac{1}{3}$ 이상 떨어질 확률을 구한다면, 체비셰프 부등식에 따른 상한선은 $\frac{1/12}{(1/3)^2} = \frac{3}{4}$ (75%)가 됩니다.
하지만 실제 적분을 통해 구한 정확한 확률은 $\frac{1}{3}$ (약 33.3%)입니다. 이처럼 체비셰프 부등식은 어떤 분포에서든 무조건 성립하는 절대적인 상한을 제공하지만, 실제 값보다는 다소 높게(보수적으로) 측정되는 경향이 있습니다.

---

## 3. 체르노프 부등식 (Chernoff's Inequality)

**[KR]** 체르노프 부등식은 적률 생성 함수(MGF, $M_X(t)$)를 활용하여 마르코프나 체비셰프보다 훨씬 더 정교하고 타이트한 꼬리 확률(Tail probability) 상한선을 도출하는 방법입니다. 마르코프 부등식의 양변에 지수 함수 $e^{tX}$를 취하는 방식으로 증명됩니다.

**[EN]** Chernoff's Inequality leverages the Moment Generating Function (MGF) to provide a much tighter and more exponentially decaying upper bound for tail probabilities compared to Markov or Chebyshev. It is derived by exponentiating the variable in Markov's Inequality.

* **공식:** 임의의 $t > 0$에 대하여,
  
$$
P(X \ge c) \le e^{-ct} M_X(t)
$$

### 체르노프 부등식 최적화 (Optimizing the Bound)
표준 정규 분포 $X \sim N(0, 1)$의 MGF는 $M_X(t) = e^{t^2/2}$ 입니다. 이를 체르노프 공식에 대입하면 다음과 같은 부등식이 성립합니다.

$$
P(X \ge c) \le e^{-ct + t^2/2}
$$

우리의 목표는 우변의 상한선을 최대한 작고 정교하게 만드는 것입니다. 지수 부분인 $-ct + \frac{t^2}{2}$를 미분하여 최솟값을 찾으면 $t = c$일 때 가장 최적화된 결과가 나옵니다. $t$ 자리에 $c$를 대입하면 다음과 같은 최종 형태를 얻습니다.

$$
P(X \ge c) \le e^{-c^2 + c^2/2} = e^{-c^2/2}
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-1" src="https://github.com/user-attachments/assets/ca8558c2-fc0c-4b68-8d27-df7c1926c530" />
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-2" src="https://github.com/user-attachments/assets/711d4ea2-d91d-439f-b09a-9ca71f70f7e9" />
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-3" src="https://github.com/user-attachments/assets/d0a8ea29-ac68-49ba-ad02-f0c5aadd085d" />
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-4" src="https://github.com/user-attachments/assets/3840e70c-ef82-4ffc-8963-21642c9468e6" />
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-5" src="https://github.com/user-attachments/assets/8fd98fa8-36c8-4e56-94bd-8a985cfc8975" />
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-6" src="https://github.com/user-attachments/assets/0ba3900f-f4ff-4615-923c-ced868222985" />
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-7" src="https://github.com/user-attachments/assets/a753647e-ab5a-4471-b4a6-049f32558b0e" />
    <img width="1264" height="1635" alt="1-9 Some Probability Inequalities-8" src="https://github.com/user-attachments/assets/bde86000-58c9-46cb-8fd7-2915fd999619" />
  </div>
</details>
