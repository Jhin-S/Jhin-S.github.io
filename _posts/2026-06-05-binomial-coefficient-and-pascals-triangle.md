---
title: "Binomial Coefficient and 파스칼의 삼각형"
date: 2026-06-05 17:08:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, binomial-coefficient, pascals-triangle, binomial-theorem]
math: true
---

간단한 개념정리입니다.

## 1. 파스칼의 삼각형과 이항계수 (Pascal's Triangle & Binomial Coefficients)

**[KR]** 파스칼의 삼각형은 이항계수 $\binom{n}{r}$ (또는 $_nC_r$)의 값들을 기하학적인 삼각형 형태로 배열한 것입니다. 각 행(Row)은 $n$의 값에 대응하며, 양 끝의 값은 항상 1이고 내부의 숫자들은 위 행의 인접한 두 숫자를 더한 값으로 구성됩니다.

**[EN]** Pascal's triangle is a triangular array of binomial coefficients $\binom{n}{r}$ (or $_nC_r$). Each row corresponds to a specific value of $n$. The numbers at the edges are always 1, and each interior number is the sum of the two numbers directly above it.

* **Row 0 ($n=0$):** $1 \implies \binom{0}{0}$
* **Row 1 ($n=1$):** $1 \quad 1 \implies \binom{1}{0} \quad \binom{1}{1}$
* **Row 2 ($n=2$):** $1 \quad 2 \quad 1 \implies \binom{2}{0} \quad \binom{2}{1} \quad \binom{2}{2}$
* **Row 3 ($n=3$):** $1 \quad 3 \quad 3 \quad 1 \implies \binom{3}{0} \quad \binom{3}{1} \quad \binom{3}{2} \quad \binom{3}{3}$
* **Row 4 ($n=4$):** $1 \quad 4 \quad 6 \quad 4 \quad 1 \implies \binom{4}{0} \quad \binom{4}{1} \quad \binom{4}{2} \quad \binom{4}{3} \quad \binom{4}{4}$

---

## 2. 대수적 관점에서의 이해 (Algebraic Perspective)

**[KR]** 도대체 왜 조합을 계산하는 이항계수가 다항식의 전개와 깊은 연관이 있을까요? $(a+b)^3$을 직접 전개해보면 그 이유를 명확하게 알 수 있습니다. 이 식을 풀어서 쓰면 각각의 괄호 안에서 $a$ 또는 $b$ 중 하나를 선택하여 곱하는 모든 경우의 수가 나열됩니다.

**[EN]** Why are binomial coefficients deeply related to polynomial expansion? We can clearly see the reason by expanding $(a+b)^3$. Expanding this expression lists all possible combinations of choosing either $a$ or $b$ from each parenthesis.

$$
(a+b)^3 = (a+b)(a+b)(a+b)
$$

위 식을 전개하면 다음과 같은 8가지($2^3$) 항이 생성됩니다.

$$
= aaa + aab + aba + abb + baa + bab + bba + bbb
$$

* 여기서 $a^2b^1$이 되는 경우는 $aab, aba, baa$로 총 3가지입니다. 이는 3개의 괄호 중 $b$를 선택할 1개의 괄호를 고르는 조합의 수 $\binom{3}{1} = 3$과 완벽하게 일치합니다.

---

## 3. 이항 정리 (The Binomial Theorem)

**[KR]** 이러한 대수적 원리를 바탕으로 시그마($\sum$) 기호를 사용하여 식을 일반화할 수 있습니다. 다항식을 전개했을 때 각 항의 계수는 파스칼의 삼각형에서 얻은 이항계수와 정확히 일치하게 됩니다. 이를 이항 정리라고 부릅니다.

**[EN]** Based on this algebraic principle, we can generalize the equation using the Sigma ($\sum$) notation. The coefficient of each term in the expanded polynomial perfectly matches the binomial coefficient from Pascal's triangle. This is known as the Binomial Theorem.

$$
(a+b)^3 = \binom{3}{0}a^3b^0 + \binom{3}{1}a^2b^1 + \binom{3}{2}a^1b^2 + \binom{3}{3}a^0b^3
$$

이를 $n$차승으로 일반화하면 다음과 같은 아름다운 공식이 완성됩니다.

$$
(a+b)^n = \sum_{r=0}^{n} \binom{n}{r} a^{n-r} b^r
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Binomial Coefficient and 파스칼의 삼각형-1" src="https://github.com/user-attachments/assets/b9aeceeb-8135-4ae1-9424-1f377aeeb96a" />
  </div>
</details>
