---
title: "4-6 Model Inspecting and Debugging"
date: 2026-08-12 06:25:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, model-inspection, debugging, shape-mismatch]
math: true
---

## 1. Parameter Counting & Weight Structure (파라미터 집계 및 가중치 구조)

**[KR]**
* **제네레이터를 사용하는 이유 (Why Generators):**
  * `model.parameters()`는 거대한 가중치 텐서를 한 번에 메모리에 올리지 않고 필요할 때 순회할 수 있도록 효율적 제네레이터를 반환합니다 (returns a generator to prevent loading large parameter tensors into memory simultaneously).
* **전체 학습 가능 파라미터 수 집계 (Counting Total Trainable Parameters):**
  * `total_params = sum(p.numel() for p in model.parameters())`
* **선형 계층 가중치 모양 원리 (Linear Weight Shape Logic: Out x In):**
  * `fc1 = nn.Linear(2048, 512)`
  * `fc1.weight.shape` $\Rightarrow$ `torch.Size([512, 2048])` (Out/출력 차원, In/입력 차원)
  * `fc1.bias.shape` $\Rightarrow$ `torch.Size([512])`

**[EN]**
* **Why Generators:**
  * `model.parameters()` returns a generator to prevent loading large parameter tensors into memory simultaneously.
* **Counting Total Trainable Parameters:**
  * `total_params = sum(p.numel() for p in model.parameters())`
* **Linear Weight Shape Logic (Out x In):**
  * `fc1 = nn.Linear(2048, 512)`
  * `fc1.weight.shape` $\Rightarrow$ `torch.Size([512, 2048])` (Out, In)
  * `fc1.bias.shape` $\Rightarrow$ `torch.Size([512])`

---

## 2. Model Hierarchy: `children()` vs `modules()` (모델 계층 구조 검사)

**[KR]**
* **`model.children()`:**
  * 모델의 직속 하위 서브 모듈만 반환합니다 (Returns an iterator over immediate child modules).
  * `nn.Sequential`이나 커스텀 블록 내부로 파고들지 않습니다 (Does NOT unpack nested layers inside `nn.Sequential` or custom sub-blocks).
* **`model.modules()`:**
  * 자기 자신을 포함하여 중첩된 모든 서브 레이어를 재귀적으로 전수 탐색하여 반환합니다 (Returns an iterator over all modules in the network recursively, including self and nested sub-layers).

**[EN]**
* **`model.children()`:**
  * Returns an iterator over immediate child modules.
  * Does NOT unpack nested layers inside `nn.Sequential` or custom sub-blocks.
* **`model.modules()`:**
  * Returns an iterator over all modules in the network recursively, including self and nested sub-layers.

---

## 3. Debugging Shape Mismatches via Forward Tracing (`forward` 트레이싱을 통한 에러 디버깅)

**[KR]**
* **체계적인 디버깅 워크플로우 (Systematic Debugging Workflow):**
  1) 대상 레이어가 기대하는 입력 차원을 확인합니다 (Inspect the target layer's expected input shape).
     * `print(model.classifier[0].weight.shape)`
  2) Flatten 및 선형 계층 바로 직전의 `forward()` 내부에 형태(shape) 추적 프린트문을 삽입합니다 (Insert shape trace print statements inside `forward()` right before flattening and linear layers).

**[EN]**
* **Systematic Debugging Workflow:**
  1) Inspect the target layer's expected input shape.
     * `print(model.classifier[0].weight.shape)`
  2) Insert shape trace print statements inside `forward()` right before flattening and linear layers.

### 형태 추적 디버깅 예시 코드 (Shape Tracing Code Example)

```python
import torch 
import torch.nn as nn 

class DebuggableCNN(nn.Module): 
    def __init__(self, num_classes=15): 
        super().__init__() 
        
        self.features = nn.Sequential( 
            nn.Conv2d(3, 32, kernel_size=3, padding=1), 
            nn.ReLU(), 
            nn.MaxPool2d(2, 2) # 32x32 -> 16x16
        ) 
        
        self.flatten = nn.Flatten() 
        self.fc = nn.Linear(32 * 16 * 16, num_classes) 

    def forward(self, x): 
        x = self.features(x) 
        
        # SHAPE TRACING 디버깅
        print(f"[디버그] Conv 블록 통과 후 텐서 모양: {x.shape}") 
        
        x = self.flatten(x) 
        print(f"[디버그] Flatten 통과 후 텐서 모양: {x.shape}") 
        
        x = self.fc(x) 
        return x 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-6 Model Inspecting and Debugging-1" src="https://github.com/user-attachments/assets/3c6754f0-3f65-4ffb-af51-8483e59708a9" />
    <img width="1264" height="1635" alt="4-6 Model Inspecting and Debugging-2" src="https://github.com/user-attachments/assets/5549e1dd-47c7-4061-86f9-0203740740d6" />
  </div>
</details>
