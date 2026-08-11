---
title: "4-5 Modular Architectures"
date: 2026-08-12 06:21:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, cnn, modular-architecture, sequential]
math: true
---

## 1. The Problem of Redundancy & Manual Layer Stacking (코드 중복과 하드코딩의 문제점)

**[KR]**
* **단일 구조 하드코딩 방식의 함정 (Monolithic Approach Pitfalls):**
  * `__init__()`에서 모든 레이어를 일일이 선언하고, `forward()`에서도 개별 호출해야 합니다.
  * 4번째 블록 추가 시 변수명 충돌(예: `relu4` 대 `relu5`)이 일어나고, `forward()`에서 호출을 누락하여 에러 없이 학습이 망가지는 버그(silent bugs)가 빈번하게 발생합니다.
* **해결책 (Solution):**
  * 순차적인 서브시퀀스(Strictly linear sub-sequences)는 `nn.Sequential`로 묶어 `__init__()`과 `forward()` 이중 수정의 번거로움을 제거합니다.

**[EN]**
* **Monolithic Approach Pitfalls:**
  * Requires manually declaring every layer in `__init__()` AND calling every layer in `forward()`.
  * Adding a 4th block causes variable naming conflicts (e.g., `relu4` vs `relu5`) and frequent silent bugs when forgotten in `forward()`.
* **Solution:**
  * Group strictly linear sub-sequences with `nn.Sequential` to eliminate dual-file/dual-method updates.

---

## 2. Modular Architecture with Custom Sub-Modules (커스텀 서브 모듈을 통한 모듈화)

**[KR]**
* **재사용 가능한 빌딩 블록 생성 (Creating Reusable Building Blocks - `ConvBlock`):** 모듈화를 통해 중복 코드를 방지합니다.
* **모듈화의 장점 (Benefits):** 전체 블록에 배치 정규화(Batch Normalization)를 추가하고 싶다면 `ConvBlock` 한 곳만 수정하면 됩니다.

**[EN]**
* **Creating Reusable Building Blocks (`ConvBlock`):** Prevents code redundancy through modularization.
* **Benefits:** To add BatchNorm to all blocks, simply update `ConvBlock` once.

```python
import torch.nn as nn 

# 재사용 가능한 커스텀 서브 모듈 (Reusable Custom Sub-Module)
class ConvBlock(nn.Module): 
    def __init__(self, in_channels, out_channels): 
        super().__init__() 
        self.block = nn.Sequential( 
            nn.Conv2d(in_channels, out_channels, kernel_size=3, padding=1), 
            nn.BatchNorm2d(out_channels), # 전체 모델에 배치 정규화를 일괄 적용하기 쉬움
            nn.ReLU(), 
            nn.MaxPool2d(2, 2) 
        ) 

    def forward(self, x): 
        return self.block(x) 
```

---

## 3. Complete Refactored Model Architecture (완성형 리팩토링 모델 코드)

**[KR]**
* 앞서 만든 `ConvBlock`을 활용하여 작성한 깔끔하고 확장 가능한 모듈형 CNN(Modular CNN) 코드입니다.

**[EN]**
* A clean and scalable Modular CNN code using the previously created `ConvBlock`.

```python
import torch 
import torch.nn as nn 

# 깔끔하고 확장 가능한 모듈형 CNN (Clean and scalable modular CNN)
class ModularCNN(nn.Module): 
    def __init__(self, num_classes=15): 
        super().__init__() 
        
        # 재사용 가능한 블록으로 구축된 특성 추출기 (Feature Extractor built with reusable blocks)
        self.features = nn.Sequential( 
            ConvBlock(3, 32),   # 32x32 -> 16x16
            ConvBlock(32, 64),  # 16x16 -> 8x8
            ConvBlock(64, 128), # 8x8 -> 4x4
            # ConvBlock(128, 256) 네 번째 블록 추가는 단 1줄이면 끝! (Adding a 4th block is just 1 line!)
        ) 
        
        self.flatten = nn.Flatten() 
        
        self.classifier = nn.Sequential( 
            nn.Linear(128 * 4 * 4, 512), 
            nn.ReLU(), 
            nn.Dropout(p=0.5), 
            nn.Linear(512, num_classes) 
        ) 

    def forward(self, x): 
        x = self.features(x) 
        x = self.flatten(x) 
        x = self.classifier(x) 
        return x 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-5 Modular Architectures-1" src="https://github.com/user-attachments/assets/13bfdaf0-fba0-4dd9-a507-0897aa25ab60" />
    <img width="1264" height="1635" alt="4-5 Modular Architectures-2" src="https://github.com/user-attachments/assets/3c5d9aaf-a842-40a3-9c74-567ae7bf672a" />
  </div>
</details>
