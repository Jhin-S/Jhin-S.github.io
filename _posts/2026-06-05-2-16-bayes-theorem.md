---
title: "2-16 Bayes Theorem"
date: 2026-06-05 16:38:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, bayes-theorem, prior, posterior, monty-hall]
math: true
---

## 1. 베이즈 정리 (Bayes Theorem)

**[KR]** 베이즈 정리는 전체 확률의 법칙(Law of Total Probability)을 응용하여, 특정 사건 $B$가 발생했다는 조건 하에 그것이 특정 경로 $A_j$를 통해 일어났을 확률을 역으로 추적하는 공식입니다.

**[EN]** By utilizing the Law of Total Probability, Bayes' theorem provides a way to calculate the posterior probability of an event $A_j$ given that event $B$ has already occurred.

$$
P(A_j \vert B) = \frac{P(A_j \cap B)}{P(B)} = \frac{P(A_j)P(B \vert A_j)}{\sum_{i=1}^{n} P(A_i)P(B \vert A_i)}
$$

* **$P(A_j)$ (Prior Probability, 사전 확률):** 새로운 단서인 사건 $B$를 알기 전에 우리가 설정해 둔 초기 확률입니다.
* **$P(A_j \vert B)$ (Posterior Probability, 사후 확률):** 사건 $B$가 관측되었다는 새로운 정보를 반영하여 최신화(업데이트)된 확률을 의미합니다.

---

## 2. 예제 풀이 (Examples)

### ① 정치인 토론 (Political Candidates)
**[KR]** 어떤 토론에서 후보자 A는 전체 질문의 60%를 답변하고, 후보자 B는 40%를 답변합니다. A가 엉뚱한 대답(Dumb answer)을 할 확률은 20%인 반면, B가 엉뚱한 대답을 할 확률은 50%입니다. 만약 누군가 엉뚱한 대답을 했다면, 그 사람이 후보자 A였을 확률은 얼마일까요?

**[EN]** Candidate A receives 60% of the questions, while B receives 40%. The probability of A making a dumb answer is 20%, whereas B's probability is 50%. If a dumb answer is given, what is the probability that it came from Candidate A?

$$
P(A \vert D) = \frac{0.6 \times 0.2}{(0.6 \times 0.2) + (0.4 \times 0.5)} = 0.375
$$

### ② 재판 결과 (The Trial)
**[KR]** 피고인이 실제로 유죄($G$)일 확률은 0.99, 무죄($I$)일 확률은 0.01로 주어졌습니다. 배심원이 무죄인 사람을 석방할($F$) 확률이 0.95이고, 유죄인 사람에게 유죄 판결을 내릴 확률 역시 0.95(즉, 유죄인데 석방할 확률은 0.05)입니다. 피고인이 석방되었을 때 그가 진짜로 무죄일 확률을 구해보겠습니다.

**[EN]** The probability that a defendant is guilty ($G$) is 0.99, and innocent ($I$) is 0.01. The jury frees ($F$) an innocent person with a 0.95 probability and convicts a guilty person with a 0.95 probability. Find the probability that the defendant is actually innocent given they were set free.

$$
P(I \vert F) = \frac{0.01 \times 0.95}{(0.01 \times 0.95) + (0.99 \times 0.05)} \approx 0.161
$$

### ③ 몬티 홀 문제 (Monty Hall Problem)
**[KR]** 3개의 문 중에서 하나 뒤에는 자동차가, 나머지 두 개 뒤에는 염소가 있습니다. 당신이 1번 문을 선택하자 진행자인 몬티가 2번 문을 열어 염소를 보여주며, 3번 문으로 선택을 바꿀지 묻습니다. 선택을 바꾸는 것이 확률적으로 이득일까요?

**[EN]** You initially pick Door 1. Monty, knowing what's behind the doors, opens Door 2 to reveal a goat. He then offers you the chance to switch your choice to Door 3. Should you switch?

$$
P(\text{Car 1} \vert \text{Monty 2}) = \frac{\frac{1}{2} \times \frac{1}{3}}{\frac{1}{2} \times \frac{1}{3} + 0 \times \frac{1}{3} + 1 \times \frac{1}{3}} = \frac{1}{3}
$$

$$
P(\text{Car 3} \vert \text{Monty 2}) = \frac{1 \times \frac{1}{3}}{\frac{1}{2} \times \frac{1}{3} + 0 \times \frac{1}{3} + 1 \times \frac{1}{3}} = \frac{2}{3}
$$

**💡 결론:** 3번 문에 자동차가 있을 확률($2/3$)이 1번 문에 있을 확률($1/3$)보다 두 배 높으므로, **항상 문을 바꾸는 것이 유리**합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-16 Bayes Theorem-1" src="https://github.com/user-attachments/assets/0e6fc8cd-c5ed-491b-9391-b5bef1e00ab3" />
    <img width="1264" height="1635" alt="2-16 Bayes Theorem-2" src="https://github.com/user-attachments/assets/338c0417-1d01-4c42-a71d-81f8cb4a0a94" />
    <img width="1264" height="1635" alt="2-16 Bayes Theorem-3" src="https://github.com/user-attachments/assets/8a46cf2a-ab12-4ed3-bfc0-f94995d77848" />
    <img width="1264" height="1635" alt="2-16 Bayes Theorem-4" src="https://github.com/user-attachments/assets/6e53e2ed-dad9-436a-a8e5-6f0d01ff7359" />
  </div>
</details>
