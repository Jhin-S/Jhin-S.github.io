---
title: "4-2 CNNs - Part 2: The Full Architecture"
date: 2026-08-12 06:10:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, cnn, maxpool, architecture]
math: true
---

## 1. The Role of Max Pooling (`nn.MaxPool2d`의 역할)

**[KR]**
* **작동 메커니즘 (Mechanism):**
  * 특징 지도(Feature Map) 상에서 2x2 창(Window)을 슬라이딩하며 가장 큰(최대값) 입력값만 보존합니다 (Selects a 2x2 window across the feature map and retains only the maximum value).
  * 지배적인 시각적 특성은 유지하면서 불필요한 값은 버려 공간 해상도를 압축합니다 (Discards lower values to compress spatial resolution while preserving dominant visual features).
* **장점 (Benefits):**
  1) **데이터 압축 (Data Compression):** 각 축의 공간적 해상도를 절반으로 줄입니다 ($28 \times 28 \rightarrow 14 \times 14$).
  2) **연산 효율성 (Efficiency):** 후속 계층으로 전달되는 데이터 양을 줄여 학습 및 추론 속도를 향상시킵니다 (Reduces computational burden for subsequent layers).
  3) **위치 변이 불변성 (Translation Invariance):** 이미지 내 미세한 위치 변화나 노이즈에 모델이 둔감해지도록(견고해지도록) 돕습니다 (Makes the network robust to small shifts or noise in input images).

**[EN]**
* **Mechanism:**
  * Selects a 2x2 window across the feature map and retains only the maximum value.
  * Discards lower values to compress spatial resolution while preserving dominant visual features.
* **Benefits:**
  1) **Data Compression:** Reduces spatial dimensions by half on each axis ($28 \times 28 \rightarrow 14 \times 14$).
  2) **Efficiency:** Reduces computational burden for subsequent layers.
  3) **Translation Invariance:** Makes the network robust to small shifts or noise in input images.

---

## 2. Full CNN Architecture & Linear Layer Math (전체 CNN 구조 및 차원 계산)

**[KR]**
* **계층별 데이터 차원 흐름 분석 (Layer Flow Breakdown - Input: $1 \times 28 \times 28$):**
  1) `Conv2d(1, 32, kernel_size=3, padding=1)` $\Rightarrow$ Shape: `[32, 28, 28]`
  2) `ReLU()` $\Rightarrow$ Shape: `[32, 28, 28]`
  3) `MaxPool2d(2, 2)` $\Rightarrow$ Shape: `[32, 14, 14]`
  4) `Conv2d(32, 64, kernel_size=3, padding=1)` $\Rightarrow$ Shape: `[64, 14, 14]`
  5) `ReLU()` $\Rightarrow$ Shape: `[64, 14, 14]`
  6) `MaxPool2d(2, 2)` $\Rightarrow$ Shape: `[64, 7, 7]`
  7) `Flatten()` $\Rightarrow$ Converts `[64, 7, 7]` tensor to 1D vector of length $64 \times 7 \times 7 = 3136$
  8) `Linear(64*7*7, num_classes)` $\Rightarrow$ Final Class Logits

**[EN]**
* **Layer Flow Breakdown (Input: $1 \times 28 \times 28$):**
  *(See the flow above)*

---

## 3. Complete PyTorch CNN Implementation (완성형 PyTorch CNN 모델 코드)

**[KR]**
* 앞서 설명한 구조를 PyTorch 클래스로 구현한 완성형 코드입니다.

**[EN]**
* The complete PyTorch class implementation based on the architecture described above.

```python
import torch 
import torch.nn as nn 

class SimpleCNN(nn.Module): 
    def __init__(self, num_classes=10): 
        super().__init__() 
        
        # 특성 추출기 (Feature Extractor)
        self.conv1 = nn.Conv2d(in_channels=1, out_channels=32, kernel_size=3, padding=1) 
        self.relu = nn.ReLU() 
        self.pool = nn.MaxPool2d(kernel_size=2, stride=2) 
        
        self.conv2 = nn.Conv2d(in_channels=32, out_channels=64, kernel_size=3, padding=1) 
        self.flatten = nn.Flatten() 
        
        # 분류기 (Classifier)
        self.fc = nn.Linear(64 * 7 * 7, num_classes) 

    def forward(self, x): 
        # 1번째 블록: Conv -> ReLU -> Pool
        # [B, 1, 28, 28] -> [B, 32, 14, 14]
        x = self.pool(self.relu(self.conv1(x))) 
        
        # 2번째 블록: Conv -> ReLU -> Pool
        # [B, 32, 14, 14] -> [B, 64, 7, 7]
        x = self.pool(self.relu(self.conv2(x))) 
        
        # 평탄화 및 선형 계층 연산
        x = self.flatten(x) # [B, 64, 7, 7] -> [B, 3136]
        x = self.fc(x)      # [B, 3136] -> [B, num_classes]
        
        return x 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-2 CNNs - Part 2_ The Full Architecture-1" src="https://github.com/user-attachments/assets/7655b529-9d38-4b26-ad81-a3e43a16e514" />
    <img width="1264" height="1635" alt="4-2 CNNs - Part 2_ The Full Architecture-2" src="https://github.com/user-attachments/assets/ec9d9e07-2c0a-40d8-a84e-0c0ccce5db1f" />
  </div>
</details>
