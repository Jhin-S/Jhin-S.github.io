---
title: "4-4 Dynamic Graphs"
date: 2026-08-12 06:17:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, dynamic-graphs, computation-graph]
math: true
---

## 1. Static Graph vs Dynamic Graph (정적 그래프 vs 동적 그래프)

**[KR]**
* **정적 그래프 - 과거 프레임워크 (Static Graph - Older Frameworks):**
  * **철학 (Philosophy):** "선정의 후 실행 (Define-and-Run)"
  * 연산이 시작되기 전에 전체 수학적 구조를 미리 컴파일합니다 (Compiles the mathematical equation before execution).
  * 경직되어 유연성이 떨어지지만, 메모리 최적화 및 연산 속도 측면에서 유리합니다 (Rigid and inflexible, but highly optimized for memory and speed).
* **동적 그래프 - PyTorch 기본 작동 방식 (Dynamic Graph - PyTorch Default):**
  * **철학 (Philosophy):** "실행하며 정의 (Define by Run)"
  * `forward()`를 통해 데이터가 흘러갈 때 각 연산 단계를 추적하여 실시간으로 사용자 정의 연산 그래프를 구축합니다 (Builds a custom computation graph step-by-step as data passes through `forward()`).
  * 생성된 그래프는 역전파(Backpropagation)에 사용된 후 파기되며, 다음 반복(Iteration)의 순전파 시 새로 구축됩니다 (The graph is used for backpropagation, discarded, and rebuilt on the next iteration).

**[EN]**
* **Static Graph (Older Frameworks):**
  * **Philosophy:** "Define-and-Run"
  * Compiles the mathematical equation before execution.
  * Rigid and inflexible, but highly optimized for memory and speed.
* **Dynamic Graph (PyTorch Default):**
  * **Philosophy:** "Define by Run"
  * Builds a custom computation graph step-by-step as data passes through `forward()`.
  * The graph is used for backpropagation, discarded, and rebuilt on the next iteration.

---

## 2. Why Dynamic Graphs Changes the Game (동적 그래프가 강력한 이유)

**[KR]**
* 동적 그래프는 다음과 같은 유연한 파이썬 코딩을 가능하게 합니다.

**[EN]**
* Dynamic graphs enable flexible Pythonic coding as follows:

```python
def forward(self, x, is_flower=True): 
    if is_flower: 
        x = self.flower_branch(x) 
    else: 
        x = self.butterfly_branch(x) 
    return x 
```

**[KR]**
1) **파이썬 다운 분기 사용 (Pythonic Branching):** `forward` 내부에 `if`/`else` 문을 자연스럽게 사용할 수 있습니다.
2) **자연스러운 디버깅 (Native Debugging):** `forward` 메서드 내부에 일반 파이썬 `print(x.shape)`나 `pdb`를 삽입하여 중간 활성화(activation) 값을 바로 출력하고 확인할 수 있습니다.
3) **가변 입력 크기 처리 (Variable Input Shapes):** 길이가 제각각인 텍스트 문장이나 가변 해상도 입력과 같은 동적 시퀀스를 매끄럽게 처리합니다.

**[EN]**
1) **Pythonic Branching:** `if`/`else` inside `forward`.
2) **Native Debugging:** Simply insert standard Python `print(x.shape)` or `pdb` inside the `forward` method to inspect intermediate activations.
3) **Variable Input Shapes:** Handles dynamic sequence lengths (e.g., text sentences of varying lengths) seamlessly.

---

## 3. Dynamic Computation Graph Code Example (동적 연산 그래프 모델 예시)

**[KR]**
* 순전파(`forward`) 과정에서 입력 조건에 따라 실시간으로 다른 경로(Branch)를 선택하고 텐서를 슬라이싱하는 동적 그래프의 활용 예시입니다.

**[EN]**
* An example of leveraging dynamic graphs to select different branches and slice tensors on-the-fly based on input conditions during the `forward` pass.

```python
import torch 
import torch.nn as nn 

class DynamicNatureCNN(nn.Module): 
    def __init__(self, num_classes=15): 
        super().__init__() 
        
        self.feature_extractor = nn.Sequential( 
            nn.Conv2d(3, 32, kernel_size=3, padding=1), 
            nn.ReLU(), 
            nn.MaxPool2d(2, 2) 
        ) 
        
        self.complex_path = nn.Linear(32 * 16 * 16, 512) 
        self.simple_path = nn.Linear(32 * 16 * 16, 128) 
        self.classifier = nn.Linear(128, num_classes) 

    def forward(self, x, use_complex_branch=False): 
        x = self.feature_extractor(x) 
        x = torch.flatten(x, 1) 
        
        # 디버깅을 위한 일반 파이썬 print 사용 가능 (Native Debugging)
        # print("Flattened shape: ", x.shape) 
        
        # 실시간 동적 분기 로직 (Dynamic Branching)
        if use_complex_branch: 
            x = self.complex_path(x) 
            x = x[:, :128] # 슬라이싱 연산도 동적으로 그래프에 기록됨
        else: 
            x = self.simple_path(x) 
            
        out = self.classifier(x) 
        return out 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-4 Dynamic Graphs-1" src="https://github.com/user-attachments/assets/a632570c-2e86-43d0-9d2e-95cf7e0d4128" />
    <img width="1264" height="1635" alt="4-4 Dynamic Graphs-2" src="https://github.com/user-attachments/assets/85f455ed-b7a4-4fee-bb02-71188fd2e7b2" />
  </div>
</details>
