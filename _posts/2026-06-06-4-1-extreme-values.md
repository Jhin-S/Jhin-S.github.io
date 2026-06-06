---
title: "4-1 Extreme Values"
date: 2026-06-06 10:20:00 +0900
categories: ["TUDelft Mastering Calculus", "Calculus II: Multivariable Functions"]
tags: [calculus, math, multivariable, extreme-values, absolute-maximum, local-minimum]
math: true
---

## 1. 절대 극값과 지역 극값 (Absolute and Local Extreme Values)

**[KR]** 다변수 함수가 주어졌을 때, 특정 점 $p = (p_1, \dots, p_n)$에서의 함숫값이 주변이나 전체 영역에서 가지는 위치에 따라 '절대(Absolute)'와 '지역(Local)' 극값으로 구분합니다.

**[EN]** For a multivariable function, the value at a specific point $p = (p_1, \dots, p_n)$ can be classified as either an "absolute" or "local" extremum, depending on how it compares to its surroundings or the entire domain.

### 절대 극값 (Absolute Extrema)
전체 정의역(Domain) $D$ 내에 있는 **모든 점들**과 비교했을 때 가장 크거나 작은 값을 의미합니다.
* **절대 최댓값 (Absolute Maximum):** 영역 내의 모든 $x$에 대하여 $f(p) \ge f(x)$
* **절대 최솟값 (Absolute Minimum):** 영역 내의 모든 $x$에 대하여 $f(p) \le f(x)$

### 지역 극값 (Local Extrema)
전체가 아닌, 점 $p$를 중심으로 하는 **특정 반경 $R$ 이내의 아주 좁은 이웃 영역** 내에서만 비교했을 때의 최고점이나 최저점을 의미합니다.
* **지역 최댓값 (Local Maximum):** $\lVert x - p \rVert < R$ 을 만족하는 주변의 모든 $x$에 대하여 $f(p) \ge f(x)$ 가 성립하는 양수 $R$이 존재함.
* **지역 최솟값 (Local Minimum):** $\lVert x - p \rVert < R$ 을 만족하는 주변의 모든 $x$에 대하여 $f(p) \le f(x)$ 가 성립하는 양수 $R$이 존재함.

---

## 2. 닫힌 유계 영역 (Closed and Bounded Domains)

**[KR]** 극값을 보장하는 정리를 배우기 위해서는 먼저 영역의 '형태'를 정의하는 두 가지 중요한 기하학적 개념을 알아야 합니다.

**[EN]** To understand the theorem that guarantees the existence of extreme values, we must first define two important geometric properties of a domain.

* **유계 영역 (Bounded Domain):** 영역이 무한히 뻗어나가지 않고 특정한 크기 안에 쏙 들어가는 상태를 말합니다. 수학적으로는, 영역 내의 모든 점 $x$가 원점으로부터 특정 거리 $M$ 이내에 존재($\lVert x \rVert < M$)하도록 만드는 양수 $M$이 존재하면 유계 영역이라고 합니다.
* **닫힌 영역 (Closed Domain):** 영역의 내부뿐만 아니라, 영역을 둘러싸고 있는 껍질 즉 '경계선(Boundary points)'까지 모두 포함하고 있는 영역을 뜻합니다.

---

## 3. 최대·최소 정리 (The Extreme Value Theorem)

**[KR]** 일변수 미적분학에서 배웠던 최대·최소 정리는 다변수 함수에서도 매우 강력하게 작용합니다. 만약 다변수 함수 $f(x)$가 앞서 설명한 **'닫혀 있고(Closed)' 동시에 '유계인(Bounded)' 영역에서 연속(Continuous)**이라면, 이 함수는 해당 영역 내에서 **반드시 절대 최댓값과 절대 최솟값을 가집니다.**

**[EN]** The Extreme Value Theorem from single-variable calculus extends powerfully to multivariable functions. Suppose a multivariable function $f(x)$ is **continuous on a domain that is both closed and bounded**. Then, it is absolutely guaranteed that the function $f$ will attain both an absolute maximum and an absolute minimum somewhere within that domain.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-1 Extreme Values-1" src="https://github.com/user-attachments/assets/3bd1df50-f4bf-4225-8548-723f55978ae0" />
    <img width="1264" height="1635" alt="4-1 Extreme Values-2" src="https://github.com/user-attachments/assets/648094f7-a9fa-4bf9-b9b1-8b7be4baad2e" />
  </div>
</details>
