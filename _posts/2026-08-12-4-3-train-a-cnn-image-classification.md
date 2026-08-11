---
title: "4-3 Train a CNN Image Classification"
date: 2026-08-12 06:14:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, cnn, dropout, weight-decay, regularization]
math: true
---

## 1. 3-Block CNN Feature Dimensionality (3블록 CNN 차원 변화)

**[KR]**
* **공간 압축 대 채널 확장 (Spatial Compression vs Channel Expansion):**
  * Conv-Pool 블록을 거쳐 깊어질수록 공간 해상도는 축소되고 ($32\times32 \rightarrow 16\times16 \rightarrow 8\times8 \rightarrow 4\times4$), 필터 채널 수는 확장됩니다 ($3 \rightarrow 32 \rightarrow 64 \rightarrow 128$).
* **밀집 계층 연산 (Dense Layer Math):**
  * 최종 Conv 블록 출력: `[Batch, 128, 4, 4]`
  * `Flatten()` 적용 후: $128 \times 4 \times 4 = 2048$ 차원 벡터
  * 첫 번째 선형 계층: `nn.Linear(2048, 512)`

**[EN]**
* **Spatial Compression vs Channel Expansion:**
  * As the image goes deeper through Conv-Pool blocks, spatial resolution shrinks ($32\times32 \rightarrow 16\times16 \rightarrow 8\times8 \rightarrow 4\times4$) while filter channels expand ($3 \rightarrow 32 \rightarrow 64 \rightarrow 128$).
* **Dense Layer Math:**
  * Final Conv output: `[Batch, 128, 4, 4]`
  * After `Flatten()`: $128 \times 4 \times 4 = 2048$ features
  * First Linear Layer: `nn.Linear(2048, 512)`

---

## 2. Regularization: Dropout & Weight Decay (정규화 - 드롭아웃 및 가중치 감쇄)

**[KR]**
* **드롭아웃 (`nn.Dropout(p=0.5)`):**
  * 학습 중 무작위로 뉴런의 활성화 값을 0으로 만들어 뉴런 간의 공동 적응(Co-adaptation)을 깨뜨립니다.
  * 신뢰할 수 없는 지름길(예: 눈 덮인 배경) 대신 본질적이고 일반화된 특성(예: 신체 구조/얼굴 형상)을 학습하도록 강제합니다.
* **가중치 감쇄 (Adam 옵티마이저의 `weight_decay` 파라미터):**
  * 손실 함수에 가중치 크기에 비례하는 L2 페널티를 더해 훈련 데이터의 노이즈를 암기하는 현상을 방지합니다.
  * 모델이 더 작고 단순한 가중치 분포를 유지하도록 유도합니다.

**[EN]**
* **Dropout (`nn.Dropout(p=0.5)`):**
  * Randomly zeroes out activations during training to break co-adaptation between neurons.
  * Forces the network to learn robust, generalized features (e.g., body shape/face structure) rather than unreliable shortcuts (e.g., snowy backgrounds).
* **Weight Decay (`weight_decay` parameter in Adam):**
  * Adds an L2 penalty on large weights to prevent memorization of training data noise.
  * Encourages smaller, simpler weight magnitudes.

---

## 3. Complete Advanced PyTorch CNN Code (완성형 PyTorch CNN 코드)

**[KR]**
* 앞서 설명한 구조와 정규화 기법을 적용한 완성형 PyTorch 모델과 최적화 코드입니다.

**[EN]**
* The complete PyTorch model and optimizer code applying the architecture and regularization techniques described above.

```python
import torch 
import torch.nn as nn 
import torch.optim as optim 

class NatureClassifier(nn.Module): 
    def __init__(self, num_classes=15): 
        super().__init__() 
        
        # 블록 1: 3 -> 32 채널
        self.block1 = nn.Sequential( 
            nn.Conv2d(3, 32, kernel_size=3, padding=1), 
            nn.ReLU(), 
            nn.MaxPool2d(2, 2) # 32x32 -> 16x16
        ) 
        
        # 블록 2: 32 -> 64 채널
        self.block2 = nn.Sequential( 
            nn.Conv2d(32, 64, kernel_size=3, padding=1), 
            nn.ReLU(), 
            nn.MaxPool2d(2, 2) # 16x16 -> 8x8
        ) 
        
        # 블록 3: 64 -> 128 채널
        self.block3 = nn.Sequential( 
            nn.Conv2d(64, 128, kernel_size=3, padding=1), 
            nn.ReLU(), 
            nn.MaxPool2d(2, 2) # 8x8 -> 4x4
        ) 
        
        self.flatten = nn.Flatten() 
        
        # 완전 연결 분류기 (Fully Connected Classifier)
        self.fc_layers = nn.Sequential( 
            nn.Linear(128 * 4 * 4, 512), 
            nn.ReLU(), 
            nn.Dropout(p=0.5), 
            nn.Linear(512, num_classes) 
        ) 

    def forward(self, x): 
        x = self.block1(x) 
        x = self.block2(x) 
        x = self.block3(x) 
        x = self.flatten(x) 
        x = self.fc_layers(x) 
        return x 

# 가중치 감쇄(Weight Decay)를 적용한 초기화
model = NatureClassifier(num_classes=15) 
criterion = nn.CrossEntropyLoss() 
optimizer = optim.Adam(model.parameters(), lr=0.001, weight_decay=1e-4) # L2 규제화 적용
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-3 Train a CNN Image Classification-1" src="https://github.com/user-attachments/assets/d1e12080-67f3-4059-9273-afe4425d13b9" />
    <img width="1264" height="1635" alt="4-3 Train a CNN Image Classification-2" src="https://github.com/user-attachments/assets/72b57a2d-0337-4ad7-9234-fbfcb696a1ee" />
    <img width="1264" height="1635" alt="4-3 Train a CNN Image Classification-3" src="https://github.com/user-attachments/assets/e901e61f-4169-448b-a7f7-1efdadbee814" />
  </div>
</details>
