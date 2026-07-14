---
title: "1-14 Computer Stuff, including Box-Muller Proof"
date: 2026-07-14 15:30:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, math, simulation, box-muller, normal-distribution, jacobian]
math: true
---

## 1. 통계 소프트웨어와 난수 생성 (Statistical Software and Simulation)

**[KR]** 실제 현실의 복잡한 시스템(예: 은행의 대기열, 공장의 재고 관리 등)을 수학적으로 분석할 때, 컴퓨터 시뮬레이션은 필수적인 도구입니다. 엑셀이나 프로그래밍 언어들은 내장 함수를 통해 특정 확률 분포의 값을 쉽게 계산해 줍니다. 
더 나아가 0과 1 사이의 단순한 균등 분포 난수 $U \sim Unif(0, 1)$를 생성한 뒤 '역변환 정리(Inverse Transform Theorem)' 등을 적용하면, 컴퓨터는 이를 바탕으로 지수 분포나 기하 분포 같은 복잡한 확률 변수들의 데이터를 끝없이 시뮬레이션해 낼 수 있습니다.

**[EN]** When mathematically analyzing complex real-world systems (e.g., bank queues, factory inventory management), computer simulation is an indispensable tool. Software like Excel or various programming languages provide built-in functions to easily evaluate probability distributions. 
Furthermore, by generating simple uniform random numbers $U \sim Unif(0, 1)$ and applying techniques like the 'Inverse Transform Theorem', computers can infinitely simulate data for complex random variables such as exponential or geometric distributions.

---

## 2. 박스-뮬러 변환 (The Box-Muller Transformation)

**[KR]** 컴퓨터로 완벽한 정규 분포 데이터를 만들어내는 가장 놀랍고 우아한 방법이 바로 **박스-뮬러 변환(Box-Muller Transformation)**입니다. 이 정리는 서로 독립인 2개의 균등 분포 난수($U_1, U_2$)를 입력으로 받아, 삼각함수와 자연로그를 거쳐 완벽하게 독립적인 2개의 표준 정규 분포 난수($Z_1, Z_2$)를 동시에 뱉어내는 마법 같은 공식을 제공합니다.

**[EN]** The most remarkable and elegant method for generating perfect normal distribution data computationally is the **Box-Muller Transformation**. This theorem takes two independent uniform random numbers ($U_1, U_2$) as inputs and, passing them through trigonometric and natural logarithmic functions, simultaneously produces two perfectly independent standard normal random variables ($Z_1, Z_2$).

* **박스-뮬러 공식 (Formulas):** (단, 삼각함수의 각도는 반드시 라디안 단위여야 합니다.)
  
$$
Z_1 = \sqrt{-2\ln(U_1)} \cos(2\pi U_2)
$$
  
$$
Z_2 = \sqrt{-2\ln(U_1)} \sin(2\pi U_2)
$$

(만약 특정한 평균 $\mu$와 분산 $\sigma^2$을 가지는 정규 분포를 원한다면, 도출된 $Z$에 표준화의 역과정인 $X = \mu + \sigma Z$를 적용해주면 됩니다.)

---

## 3. 박스-뮬러 증명과 자코비안 (Proof via Jacobian)

**[KR]** 이 변환이 수학적으로 완벽하게 성립하는 이유는 다변수 미적분학의 **자코비안(Jacobian)** 행렬식을 이용한 결합 확률 밀도 함수(Joint PDF)의 변환 원리 덕분입니다. 
우선 역함수를 취해 $U_1$과 $U_2$를 $Z_1, Z_2$에 대한 수식으로 정리합니다. 그 다음, 각 변수에 대해 편미분(Partial Derivative)을 수행하여 자코비안 행렬식을 구성하고 절댓값을 구합니다. 복잡한 미분 연산 끝에 남는 최종 결과물은 놀랍게도 정확히 두 개의 독립적인 표준 정규 분포 확률 밀도 함수가 곱해진 형태가 되며, 이로써 증명이 아름답게 완성됩니다.

**[EN]** The reason this transformation holds mathematically perfect is due to the transformation principle of joint probability density functions utilizing the **Jacobian** determinant from multivariable calculus. 
First, we use inverse functions to express $U_1$ and $U_2$ in terms of $Z_1$ and $Z_2$. Next, we compute the partial derivatives for each variable to construct the Jacobian matrix and find its absolute determinant. After complex differentiation, the final remaining expression surprisingly emerges as the exact product of two independent standard normal probability density functions, thereby completing the proof beautifully.

* **결합 확률 밀도 함수의 도출 (Derivation of Joint PDF):**
  
$$
g(z_1, z_2) = \left| \frac{\partial u_1}{\partial z_1}\frac{\partial u_2}{\partial z_2} - \frac{\partial u_2}{\partial z_1}\frac{\partial u_1}{\partial z_2} \right|
$$

$$
= \left( \frac{1}{\sqrt{2\pi}} e^{-z_1^2/2} \right) \left( \frac{1}{\sqrt{2\pi}} e^{-z_2^2/2} \right)
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-14 Computer Stuff, including Box-Muller Proof-1" src="https://github.com/user-attachments/assets/ec5b0023-eec2-46c8-b3d3-10ae9051e715" />
    <img width="1264" height="1635" alt="1-14 Computer Stuff, including Box-Muller Proof-2" src="https://github.com/user-attachments/assets/7df41998-13c3-4c71-b3df-c10cef635b54" />
    <img width="1264" height="1635" alt="1-14 Computer Stuff, including Box-Muller Proof-3" src="https://github.com/user-attachments/assets/924079ee-2ecf-4544-b663-f965a9e78a9c" />
    <img width="1264" height="1635" alt="1-14 Computer Stuff, including Box-Muller Proof-4" src="https://github.com/user-attachments/assets/ee6a364f-e5ce-45d2-a1d2-89d42a3051ed" />
  </div>
</details>
