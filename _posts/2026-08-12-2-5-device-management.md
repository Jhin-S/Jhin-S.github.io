---
title: "2-5 Device Management"
date: 2026-08-12 05:26:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, device-management, cuda, oom, gpu]
math: true
---

## 1. Why Device Management Matters (장치 관리의 중요성)

**[KR]**
* **CPU VS GPU:**
  * **CPU:** 범용 목적, 순차적 연산 처리 (PyTorch 기본 설정 장치).
  * **GPU (가속기 - Accelerator):** 행렬/텐서 연산의 대규모 병렬 처리 (CPU 대비 10배~15배 빠른 학습 속도).
* **제약 조건 (The Constraint):**
  * PyTorch는 텐서나 모델을 CPU와 GPU 사이로 자동 이동(auto-moves)시켜주지 않습니다.
  * 입력 데이터, 정답 레이블(targets), 모델 파라미터는 **반드시 동일한 장치**에 있어야 합니다.

**[EN]**
* **CPU VS GPU:**
  * **CPU:** General-purpose, Sequential execution (PyTorch default device).
  * **GPU (Accelerator):** Massively parallel processing for matrix/tensor operations (10x to 15x faster training).
* **The Constraint:**
  * PyTorch never auto-moves tensors or models between CPU and GPU.
  * Inputs, targets, and model parameters must reside on the **same device**.

---

## 2. Device Code Setup & Assignment Rules (장치 설정 및 할당 규칙)

**[KR]**
* **표준 장치 설정 코드 (Standard Device Setup):**

```python
import torch 

# 안전한 기본 선택기 (Safe default selector)
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu') 
```

* **모델 및 데이터 이동 코드 (Moving models and data):**

```python
# 1. 학습 루프 전, 모델을 "한 번만" 이동
model = MyModel().to(device) 

# 2. 학습 루프 내부에서 각 배치 데이터를 이동
for inputs, targets in dataloader: 
    inputs = inputs.to(device)   # 텐서는 반드시 재할당 해야 함!
    targets = targets.to(device) # 텐서는 반드시 재할당 해야 함!
    outputs = model(inputs) 
```

* **장치 위치 확인법 (Checking Device Location):**
  * 텐서 (tensor): `tensor.device`
  * 모델 (model): `next(model.parameters()).device`

**[EN]**
* **Standard Device Setup:**
  *(See the Python code above)*
* **Moving models and data:**
  *(See the Python code above)*
* **Checking Device Location:**
  * tensor: `tensor.device`
  * model: `next(model.parameters()).device`

---

## 3. GPU Memory Management & OOM Debugging (GPU 메모리 및 OOM 디버깅)

**[KR]**
* **CUDA Out-of-Memory (OOM) Error:**
  * 모델 크기 + 배치 데이터 용량이 GPU VRAM 크기를 초과할 때 발생합니다.
* **OOM 해결책 (Fixing OOM):**
  * **배치 크기 축소 (Reduce Batch Size):** 64에서 32 또는 16으로 줄입니다.
  * **캐시 비우기 (Clear Cache):** 사용되지 않는 VRAM 해제를 위해 `torch.cuda.empty_cache()`를 활용합니다.

**[EN]**
* **CUDA Out-of-Memory Error:**
  * Occurs when Model Size + Batch Data size exceeds GPU VRAM.
* **Fixing OOM:**
  * **Reduce Batch Size:** Decrease from 64 to 32 or 16.
  * **Clear Cache:** Use `torch.cuda.empty_cache()` if unreferenced VRAM isn't freed.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-5 Device Management-1" src="https://github.com/user-attachments/assets/5ed8c2dc-a00e-4e56-bda4-088b3fb6c83f" />
    <img width="1264" height="1635" alt="2-5 Device Management-2" src="https://github.com/user-attachments/assets/fe84d6f1-1ac0-42fd-a5b6-36eefcb663c2" />
  </div>
</details>
