---
title: "2-6 Image Classification - Part 1: Preparing the Data and Building the Model"
date: 2026-08-12 05:30:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, image-classification, mnist, dataloader, flatten]
math: true
---

## 1. Data Pipeline Setup with TorchVision (TorchVision을 활용한 데이터 파이프라인)

**[KR]**
* **학습 시 `shuffle=True`를 설정하는 이유 (Why `shuffle=True` for Training):**
  * 클래스 순서에 따른 편향(예: 0만 연속으로 6000개 학습하는 현상)을 방지합니다.
  * 각 미니배치가 다양한 숫자 클래스를 골고루 포함하도록 유도합니다.

**[EN]**
* **Why `shuffle=True` for Training:**
  * Prevents class-ordering bias (e.g., training on 6000 zeros continuously).
  * Ensures each mini-batch contains a diverse mix of digit classes.

### 변환 파이프라인 및 데이터로더 초기화 (Transforms Pipeline, Dataset & DataLoader Initialization)

```python
from torchvision import transforms 
from torchvision.datasets import MNIST 
from torch.utils.data import DataLoader 

# 변환 파이프라인 (Transforms Pipeline)
transform = transforms.Compose([ 
    transforms.ToTensor(), # PIL 이미지를 텐서로 변환 및 [0, 255] -> [0.0, 1.0] 스케일링
    transforms.Normalize((0.1307,), (0.3081,)) # MNIST 데이터셋의 전체 평균 및 표준편차
]) 

# 데이터셋 초기화 (Dataset Initialization)
train_dataset = MNIST(root='./data', train=True, download=True, transform=transform) 
test_dataset = MNIST(root='./data', train=False, download=True, transform=transform) 

# 데이터로더 초기화 (DataLoader Initialization)
train_loader = DataLoader(train_dataset, batch_size=64, shuffle=True) 
test_loader = DataLoader(test_dataset, batch_size=1000, shuffle=False) 
```

---

## 2. Model Architecture & `nn.Flatten()` (모델 아키텍처 및 `nn.Flatten()`)

**[KR]**
* **`Flatten`을 통한 차원 변환 (Shape Transformation via Flatten):**
  * 원시 이미지 배치 (Raw Image Batch): `[64, 1, 28, 28]` (배치 크기, 채널 수, 세로, 가로)
  * `nn.Flatten()` 적용 후: `[64, 784]` ($28 \times 28 = 784$ 크기의 1차원 벡터)
  * **이유 (Reason):** `nn.Linear` 레이어는 샘플당 1차원 특성 벡터 형태의 입력을 요구하기 때문입니다.

**[EN]**
* **Shape Transformation via Flatten:**
  * Raw Image Batch: `[64, 1, 28, 28]` (Batch, Channel, Height, Width)
  * After `nn.Flatten()`: `[64, 784]` ($28 \times 28 = 784$ Vector)
  * **Reason:** `nn.Linear` layers require 1D feature vectors per sample.

### 커스텀 모델 클래스 (Custom Model Class - `nn.Module`)

```python
import torch.nn as nn 

class DigitClassifier(nn.Module): 
    def __init__(self): 
        super().__init__() 
        self.flatten = nn.Flatten() 
        
        self.layers = nn.Sequential( 
            nn.Linear(784, 128), # 784개 픽셀 -> 128개 은닉 특성
            nn.ReLU(),           # 비선형 활성화 함수
            nn.Linear(128, 10)   # 128개 은닉 특성 -> 10개 출력 클래스 (0~9)
        ) 

    def forward(self, x): 
        x = self.flatten(x) 
        x = self.layers(x) 
        return x 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-6 Image Classification - Part 1_ Preparing the Data and Building the Model-1" src="https://github.com/user-attachments/assets/aaf0e10e-a238-42ad-8ecc-dfc2a94b0b1b" />
    <img width="1264" height="1635" alt="2-6 Image Classification - Part 1_ Preparing the Data and Building the Model-2" src="https://github.com/user-attachments/assets/2879eb2f-aea7-425d-a94e-f707d0625336" />
  </div>
</details>
