---
title: "1-6 Tensor Math and Broadcasting"
date: 2026-08-12 04:55:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, tensor-math, broadcasting]
math: true
---

## 1. Element-wise Operations (요소별 연산)

**[KR]**
* **기본 메커니즘 (Basic Mechanism):** 연산 $y = (W \cdot x) + B$
  * $x$가 여러 배달 거리를 담은 텐서일 때, $W$(스칼라 가중치)와 $B$(스칼라 편향)는 각 원소에 독립적으로 적용됩니다.
* **주요 장점 (Key Advantage):**
  * 일반 파이썬 산술 문법($W * x + B$)을 그대로 사용하지만, 백엔드(C++/CUDA)에서 병렬로 빠르게 처리됩니다.
  * 스칼라 연산뿐만 아니라 모양이 동일한 텐서 간 연산에도 동일하게 작동합니다.

**[EN]**
* **Basic Mechanism:** Operation $y = (W \cdot x) + B$
  * When $x$ is a tensor of multiple distances, $W$ (scalar weight) and $B$ (scalar bias) apply to every element independently.
* **Key Advantage:**
  * Written using standard Python arithmetic ($W * x + B$), but executes in parallel with optimized C++/CUDA backends.
  * Operates identically on scalars and tensors with matching shapes.

---

## 2. What is Broadcasting? (브로드캐스팅의 개념)

**[KR]**
* **정의 (Definition):** 산술 연산 시 작은 텐서의 차원을 큰 텐서의 모양에 맞게 자동으로 확장하는 기능입니다.
* **단순 예시 - 스칼라 + 텐서 (Simple Example - Scalar + Tensor):**
  * $[1, 3]$ 모양의 텐서에 스칼라 $5$를 더할 때:
  * PyTorch가 내부적으로 $5$를 $[5, 5, 5]$ 형태의 $[1, 3]$ 텐서로 확장하여 연산합니다.
* **$[1, 3]$과 $[1, 1]$ 텐서의 예시 (Example with $[1, 3]$ and $[1, 1]$ Tensors):**
  * 텐서 A: $[1, 3]$ (1행 3열)
  * 텐서 B: $[1, 1]$ (1행 1열)
  * 두 번째 차원이 1 대 3이므로 텐서 B의 두 번째 차원이 3으로 확장되어 $[1, 3]$으로 맞춰집니다.

**[EN]**
* **Definition:** Automatic expansion of smaller-tensor dimensions to match the shape of larger tensors during arithmetic operations.
* **Simple Example (Scalar + Tensor):**
  * Adding scalar $5$ to a tensor of shape $[1, 3]$.
  * PyTorch expands $5$ to $[5, 5, 5]$ to match $[1, 3]$.
* **Example with $[1, 3]$ and $[1, 1]$ Tensors:**
  * Tensor A: $[1, 3]$ (1 row, 3 columns)
  * Tensor B: $[1, 1]$ (1 row, 1 column)
  * Dimension 2 has size 1 vs 3. Tensor B expands along dimension 2 to $[1, 3]$.

---

## 3. Advanced Broadcasting Example (고급 브로드캐스팅 예시)

**[KR]**
* **$[1, 3]$과 $[3, 1]$ 텐서의 결합 (Combining $[1, 3]$ and $[3, 1]$ Tensors):**
  * 텐서 A 모양 (Tensor A shape): $[1, 3]$
  * 텐서 B 모양 (Tensor B shape): $[3, 1]$
* **확장 논리 (Expansion Logic):**
  * 첫 번째 차원 (Dimension 1): 1 대 3 $\rightarrow$ 텐서 A의 행이 3개로 확장됨 ($1 \rightarrow 3$)
  * 두 번째 차원 (Dimension 2): 3 대 1 $\rightarrow$ 텐서 B의 열이 3개로 확장됨 ($1 \rightarrow 3$)
* **최종 연산 결과 모양 (Resulting Operation Shape):** $[3, 3]$ 매트릭스 (grid)
* **실무적 유용성 (Practical Utility):** 명시적인 `for` 루프나 불필요한 메모리를 할당하는 `repeat()` 함수 없어도 배치별 특성 변환 및 다차원 행렬 연산을 효율적으로 수행 가능합니다.

**[EN]**
* **Combining $[1, 3]$ and $[3, 1]$ Tensors:**
  * Tensor A shape: $[1, 3]$
  * Tensor B shape: $[3, 1]$
* **Expansion Logic:**
  * Dimension 1: 1 vs 3 $\rightarrow$ Tensor A expands row-wise ($1 \rightarrow 3$).
  * Dimension 2: 3 vs 1 $\rightarrow$ Tensor B expands column-wise ($1 \rightarrow 3$).
* **Resulting Operation Shape:** $[3, 3]$ grid.
* **Practical Utility:** Enables batch-wise feature adjustments and multi-dimensional matrix operations without manual `for` loops or `repeat()` memory allocation.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-6 Tensor Math and Broadcasting-1" src="https://github.com/user-attachments/assets/21aa518f-be3c-48b5-b67d-1da53ac47100" />
    <img width="1264" height="1635" alt="1-6 Tensor Math and Broadcasting-2" src="https://github.com/user-attachments/assets/dcc2e642-985b-4cd9-ac06-70ed206f42cc" />
  </div>
</details>
