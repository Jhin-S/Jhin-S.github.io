---
title: "Hand-Calculated Linear Regression with Matrix Operations"
date: 2026-07-26 12:42:00 +0900
categories: ["Machine Learning & Deep Learning"]
tags: [machine-learning, linear-regression, matrix-operations, forward-pass, backpropagation, gradient-descent]
math: true
---

## 1. 행렬 차원 및 상황 설정 (Setup and Matrix Dimensions)

**[KR]** 선형 회귀 모델인 $Y = wX + b$ 가 어떻게 학습되는지 행렬 계산을 손으로 직접 풀어보겠습니다. 먼저 연산에 필요한 데이터와 가중치들의 초기 조건을 다음과 같이 설정합니다.

**[EN]** Let's manually calculate how the linear regression model $Y = wX + b$ is trained using matrix operations. First, we set up the initial conditions for the data and weights required for the computation as follows.

*   **입력 데이터 행렬 (Input Data Matrix $X$):** 샘플 2개, 특성 2개
    $$ X = \begin{bmatrix} 1 & 2 \\ 3 & 1 \end{bmatrix} $$
  
*   **실제 정답 행렬 (Target Matrix $Y$):** 각 샘플당 타깃 1개 ($2 \times 1$ 행렬)
    $$ Y = \begin{bmatrix} 5 \\ 7 \end{bmatrix} $$
  
*   **가중치 행렬 (Weight Matrix $W$):** $1 \times 2$ 행렬
    $$ W = [1.0, 0.5] $$
  
*   **편향 (Bias $b$):** 스칼라 값 0.0 (행렬 연산 시 브로드캐스팅 적용)
*   **학습률 (Learning Rate $\alpha$):** 0.1
*   **연산식 구조 (Equation Structure):** $P = XW^T + b$ (차원: $[2 \times 2] \times [2 \times 1] + [1] = [2 \times 1]$)

---

## 2. Step 1: 순전파 (Forward Pass)

**[KR]** 행렬 곱을 이용하여 예측값 $P$를 구합니다.

**[EN]** Calculate the predicted value $P$ using matrix multiplication.

$$ P = XW^T + b = \begin{bmatrix} 1 & 2 \\ 3 & 1 \end{bmatrix} \begin{bmatrix} 1.0 \\ 0.5 \end{bmatrix} + 0.0 = \begin{bmatrix} 2.0 \\ 3.5 \end{bmatrix} $$


---

## 3. Step 2: 오차(Error) 및 손실(Loss) 계산

**[KR]** 실제 정답 $Y$와의 차이인 오차 벡터 $E = P - Y$ 를 구합니다.

**[EN]** Calculate the error vector $E$, which is the difference from the actual target $Y$, using $E = P - Y$.

$$ E = \begin{bmatrix} 2.0 \\ 3.5 \end{bmatrix} - \begin{bmatrix} 5.0 \\ 7.0 \end{bmatrix} = \begin{bmatrix} -3.0 \\ -3.5 \end{bmatrix} $$


**[KR]** 손실 $L$은 2개 샘플의 평균 제곱 오차(MSE)입니다. (참고: 손실 $L$은 벡터 $E$와 스칼라 $N$의 함수입니다).

**[EN]** The loss $L$ is the Mean Squared Error (MSE) of the 2 samples. (Note: The loss $L$ is a function of the vector $E$ and the scalar $N$).

$$ L = \frac{1}{2N} \sum E^2 = \frac{1}{2 \times 2} \left( (-3)^2 + (-3.5)^2 \right) = \frac{1}{4} (9.0 + 12.25) \approx 5.3 $$


---

## 4. Step 3: 미분 및 기울기(Gradient) 계산

**[KR]** 스칼라 값인 $L$을 $1 \times 2$ 행렬인 $W$로 미분하는 방법은 연쇄 법칙(Chain Rule)을 적용하는 것입니다. 

**[EN]** The way to differentiate the scalar $L$ with respect to the $1 \times 2$ matrix $W$ is by applying the Chain Rule.

*   **가중치 기울기 (Gradient w.r.t Weights):**
    $$ \frac{\partial L}{\partial W} = \left[ \frac{\partial L}{\partial w_1}, \frac{\partial L}{\partial w_2} \right] $$
  
    오차 벡터의 요소가 $e_1 = p_1 - y_1 = (x_{11}w_1 + x_{12}w_2) - y_1$ 이고 $e_2 = p_2 - y_2 = (x_{21}w_1 + x_{22}w_2) - y_2$ 이므로, 이를 연쇄 법칙으로 전개합니다.
    $$ \frac{\partial L}{\partial w_1} = \frac{\partial L}{\partial e_1}\frac{\partial e_1}{\partial w_1} + \frac{\partial L}{\partial e_2}\frac{\partial e_2}{\partial w_1} $$
  
    최종적으로 정리하면 가중치의 미분값은 다음과 같습니다.
    $$ \frac{\partial L}{\partial W} = \frac{1}{N} E^T X = \frac{1}{2} [-3.0, -3.5] \begin{bmatrix} 1 & 2 \\ 3 & 1 \end{bmatrix} = [-6.75, -4.75] $$
  

*   **편향 기울기 (Gradient w.r.t Bias):**
    편향 $b$에 대한 기울기는 단순히 오차들의 평균이 됩니다.
    $$ \frac{\partial L}{\partial b} = \frac{1}{N} \sum E = \frac{-3.0 + (-3.5)}{2} = -3.25 $$
  

---

## 5. Step 4 & 5: 파라미터 업데이트 및 결과 확인 (Update and Verify)

**[KR]** 도출된 기울기와 학습률 $\alpha$를 사용하여 행렬 $W$와 편향 $b$를 업데이트합니다.

**[EN]** Update the matrix $W$ and bias $b$ using the derived gradients and the learning rate $\alpha$.

$$ W_{new} = W_{old} - \alpha \frac{\partial L}{\partial W} = [1.0, 0.5] - 0.1 \times [-6.75, -4.75] = [1.675, 0.975] $$

$$ b_{new} = b_{old} - \alpha \frac{\partial L}{\partial b} = 0.0 - 0.1 \times (-3.25) = 0.325 $$


**[KR]** 업데이트가 잘 되었는지 최종적으로 확인해 봅니다.

**[EN]** Finally, let's verify if the update was successful.

$$ P_{new} = \begin{bmatrix} 1 & 2 \\ 3 & 1 \end{bmatrix} \begin{bmatrix} 1.675 \\ 0.975 \end{bmatrix} + 0.325 = \begin{bmatrix} 3.95 \\ 6.325 \end{bmatrix} $$


**[결론 / Conclusion]**
**[KR]** 이전 예측값이 $P = [2.0, 3.5]^T$ (손실 $L = 5.3125$) 였던 것에 반해, 새로운 예측값은 손실이 $L \approx 0.389$ 로 크게 줄어들며 두 샘플 모두 실제 정답인 $[5, 7]^T$ 에 훨씬 가까워진 것을 확인할 수 있습니다!
**[EN]** Compared to the previous prediction $P = [2.0, 3.5]^T$ (Loss $L = 5.3125$), the new prediction's loss drastically decreased to $L \approx 0.389$, and we can see that both samples have moved much closer to the actual target $[5, 7]^T$!

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Hand-Calculated Linear Regression with Matrix Operations-1" src="https://github.com/user-attachments/assets/751b30e6-9d55-4838-bf84-32f708cbc3c9" />
    <img width="1264" height="1635" alt="Hand-Calculated Linear Regression with Matrix Operations-2" src="https://github.com/user-attachments/assets/5e663539-d346-4c8d-b6c1-7644ccc7bea3" />
  </div>
</details>
