---
title: "4-3 Finding Extreme Values"
date: 2026-06-06 10:35:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, extreme-values, optimization, boundary-check]
math: true
---

## 1. 닫힌 영역에서의 최대·최소 구하기 (Finding Extrema on Closed Regions)

**[KR]** 다변수 함수가 닫혀 있고 유계인(Closed and bounded) 영역에서 주어졌을 때, 절대 최댓값과 절대 최솟값을 찾는 과정은 일변수 함수의 극값 찾기 논리를 확장한 것입니다. 다음의 3단계를 거쳐 가장 큰 값과 가장 작은 값을 가려냅니다.

**[EN]** Finding the absolute maximum and minimum values of a multivariable function on a closed and bounded domain is a direct extension of the single-variable method. We systematically track down the highest and lowest points using a three-step process:

1. **내부 임계점 탐색 (Interior Critical Points):** 주어진 영역 내부에서 편미분 계수 $f_x$와 $f_y$가 모두 0이 되는 임계점들을 찾고, 그곳에서의 함숫값을 계산합니다.
2. **경계선 탐색 (Boundary Check):** 영역을 둘러싸고 있는 경계선들(보통 $x=0$, $y=0$, 혹은 특정 직선이나 곡선 방정식)을 원래 함수에 대입하여 변수를 하나로 줄인 뒤, 해당 경계선 위에서의 극값과 꼭짓점(Vertices)에서의 함숫값들을 모두 구합니다.
3. **최종 비교 (Compare All Values):** 1단계와 2단계에서 수집한 모든 함숫값들을 나열한 뒤, 가장 큰 값이 '절대 최댓값', 가장 작은 값이 '절대 최솟값'이 됩니다.

---

## 2. 실전 예제 풀이 (Practice Exercises)

### Exercise 1: 제약 조건이 있는 부피 최적화 (Optimizing Volume with Constraints)
**[KR]** 가로 $a$, 세로 $b$, 높이 $c$인 직육면체 상자가 있습니다. 상자의 길이와 둘레의 합($a + 2b + 2c$)이 120을 넘지 않는다는 조건 하에, 상자의 부피($V = abc$)를 최대로 만드는 치수를 구해봅시다.
**[EN]** Consider a rectangular box with dimensions $a, b, c$. We want to maximize its volume $V = abc$, subject to the constraint that the sum of its length and girth ($a + 2b + 2c$) equals 120.

제약 조건을 이용해 변수 하나를 소거합니다.
$$a = 120 - 2b - 2c$$

이를 부피 공식에 대입하여 $b$와 $c$에 대한 이변수 함수로 만듭니다.
$$V(b, c) = (120 - 2b - 2c)bc = 120bc - 2b^2c - 2bc^2$$

부피가 최대가 되는 지점을 찾기 위해 $b$와 $c$에 대해 각각 편미분하여 0이 되는 지점을 찾습니다.
* $V_b = 120c - 4bc - 2c^2 = c(120 - 4b - 2c) = 0$
* $V_c = 120b - 2b^2 - 4bc = b(120 - 2b - 4c) = 0$

상자의 치수인 $b$와 $c$는 0이 될 수 없으므로, 괄호 안의 식이 0이 되어야 합니다.
$$2b + c = 60$$
$$b + 2c = 60$$

위 연립방정식을 풀면 $b = 20, c = 20$ 이 도출됩니다. 이를 원래의 제약 조건에 대입하면 $a = 40$ 이 됩니다.
**결론:** 최대 부피는 $V = 40 \times 20 \times 20 = 16000$ 입니다.

---

### Exercise 2: 직사각형 영역에서의 절대 최대·최소 (Extrema on a Rectangular Region)
**[KR]** 꼭짓점이 $(0,0), (0,1), (2,1), (2,0)$인 닫힌 직사각형 영역 $R$ 위에서, 함수 $f(x, y) = xe^y - x^2 - e^y$ 의 절대 극값들을 찾아봅시다.
**[EN]** Find the absolute maximum and minimum values of $f(x, y) = xe^y - x^2 - e^y$ on the closed rectangular region $R$ with vertices at $(0,0), (0,1), (2,1),$ and $(2,0)$.

**Step 1. 내부 임계점 찾기**
* $f_x = e^y - 2x = 0 \implies e^y = 2x$
* $f_y = xe^y - e^y = e^y(x - 1) = 0$

지수함수 $e^y$는 0이 될 수 없으므로 $x = 1$ 이어야 합니다. $x=1$을 첫 번째 식에 대입하면 $e^y = 2$가 되어 $y = \ln 2$ 가 됩니다.
따라서 내부 임계점은 $(1, \ln 2)$ 이며, 이때의 함숫값은 $f(1, \ln 2) = 2 - 1 - 2 = -1$ 입니다.

**Step 2. 4개의 경계선(Boundary) 확인하기**
1. **$x = 0$ 인 선분:** $f(0, y) = -e^y$. 미분해도 $0$이 되지 않아 극점이 없으며, 양 끝점의 값은 $f(0,0) = -1$, $f(0,1) = -e$ 입니다.
2. **$y = 0$ 인 선분:** $f(x, 0) = x - x^2 - 1$. 미분하면 $1 - 2x = 0 \implies x = \frac{1}{2}$. 이때의 값은 $f(\frac{1}{2}, 0) = -\frac{3}{4}$ 입니다. 끝점 값은 $f(2,0) = -3$ 입니다.
3. **$y = 1$ 인 선분:** $f(x, 1) = ex - x^2 - e$. 미분하면 $e - 2x = 0 \implies x = \frac{e}{2}$. 이때의 값은 $f(\frac{e}{2}, 1) = \frac{e^2}{4} - e$ 입니다. 끝점 값은 $f(2,1) = e - 4$ 입니다.
4. **$x = 2$ 인 선분:** $f(2, y) = e^y - 4$. 극점이 없으며 기존에 구한 끝점 값들만 가집니다.

**Step 3. 결과 비교**
구해진 모든 후보 함숫값들 ($-1, -e, -3, -\frac{3}{4}, \frac{e^2}{4} - e, e - 4$) 을 실수 크기로 비교하여, 이 중 가장 큰 값이 절대 최댓값, 가장 작은 값이 절대 최솟값이 됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-3 Finding Extreme Values-1" src="https://github.com/user-attachments/assets/29cf9b73-3e0c-4912-a8af-f81586b671c3" />
    <img width="1264" height="1635" alt="4-3 Finding Extreme Values-2" src="https://github.com/user-attachments/assets/54ab495a-5497-4969-88fd-065a424395a2" />
    <img width="1264" height="1635" alt="4-3 Finding Extreme Values-3" src="https://github.com/user-attachments/assets/51c426cc-c226-4805-b158-a6398bfa7ef3" />
    <img width="1264" height="1635" alt="4-3 Finding Extreme Values-4" src="https://github.com/user-attachments/assets/68f7afe0-abfe-4c9c-96cd-772cc3a67d34" />
    <img width="1264" height="1635" alt="4-3 Finding Extreme Values-5" src="https://github.com/user-attachments/assets/ebf956a7-5a02-4577-8bf6-29c38d4d668e" />
  </div>
</details>
