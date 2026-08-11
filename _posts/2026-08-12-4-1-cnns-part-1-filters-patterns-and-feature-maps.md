---
title: "4-1 CNNs - Part 1: Filters, Patterns, and Feature Maps"
date: 2026-08-12 06:05:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, cnn, convolution, feature-map]
math: true
---

## 1. Intuition of Convolution Operations (합성곱 연산의 직관)

**[KR]**
* **선형 계층이 컴퓨터 비전에 불리한 이유 (Why Linear Layers Fail for Vision):**
  * 2차원 이미지를 1차원 벡터로 펼치기 때문에 이웃 픽셀 간의 공간적 위치 관계를 잃어버립니다 (Flattens 2D images into 1D vectors, losing spatial relationships between neighboring pixels).
* **생물학적 영감 (Biological Inspiration):**
  * 특정 시각 자극 패턴에만 반응하는 시각 피질 뉴런의 원리를 모방했습니다 (Inspired by the visual cortex where individual neurons respond to specific local patterns).
* **합성곱의 작동 메커니즘 (Mechanism of Convolution):**
  * 작은 격자(예: 3x3 필터)가 이미지 위를 이동합니다 (A small grid (3x3 filter) slides across the image).
  * 필터 가중치와 하단 픽셀값을 곱한 후 더하여 특성 지도(Feature Map)를 형성합니다 (Multiplies underlying pixel values by filter weights and sums them up to create feature maps).
  * 필터의 가중치 조합에 따라 추출되는 시각적 특징이 달라집니다 (Different filters highlight different visual aspects).
    * **수직 경계선 필터 (Vertical Edge Filters):** 수직 가장자리 검출 (Detects vertical boundaries).
    * **수평 경계선 필터 (Horizontal Edge Filters):** 수평 가장자리 검출 (Detects horizontal lines).

**[EN]**
* **Why Linear Layers Fail for Vision:**
  * Flattens 2D images into 1D vectors, losing spatial relationships between neighboring pixels.
* **Biological Inspiration:**
  * Inspired by the visual cortex where individual neurons respond to specific local patterns.
* **Mechanism of Convolution:**
  * A small grid (3x3 filter) slides across the image.
  * Multiplies underlying pixel values by filter weights and sums them up to create feature maps.
  * Different filters highlight different visual aspects.
    * **Vertical Edge Filters:** Detects vertical boundaries.
    * **Horizontal Edge Filters:** Detects horizontal lines.

---

## 2. PyTorch `nn.Conv2d` Parameter Breakdown (`nn.Conv2d` 파라미터 분석)

**[KR]**
* **코드 구현 (Code Implementation):**

```python
import torch.nn as nn 

conv_layer = nn.Conv2d( 
    in_channels=3,  # RGB 입력 채널
    out_channels=16, # 16개의 서로 다른 필터 적용
    kernel_size=3,   # 3x3 크기의 필터
    stride=1,        # 한 번에 1픽셀 이동
    padding=1        # 공간적 해상도(가로/세로)를 유지하는 동일 패딩 (Same Padding)
) 
```

**[EN]**
* **Code Implementation:**
  *(See the Python code above)*

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-1 CNNs - Part 1_ Filters, Patterns, and Feature Maps-1" src="https://github.com/user-attachments/assets/53d4b045-2fe6-4dc7-a5db-41ae04fd6048" />
  </div>
</details>
