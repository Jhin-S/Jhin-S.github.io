---
title: "3-2 Transform Pipelines"
date: 2026-08-12 05:48:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, transform, dataloader, normalization]
math: true
---

## 1. The Batch Stacking Error & Solution (배치 적재 에러 및 해결책)

**[KR]**
* **배치 실패의 근본 원인 (Root Cause of Batch Failure):**
  * 원시 데이터셋 이미지들의 해상도/크기가 제각각입니다 (Raw dataset images have varying resolutions/dimensions).
  * 차원이 다르면 DataLoader가 $[N, C, H, W]$ 차원의 텐서 그리드로 이미지를 쌓아 올리지 못합니다 (DataLoader fails to stack images into $[N, C, H, W]$ tensor grids if dimensions mismatch).
* **종횡비 유지 전처리 패턴 (Aspect Ratio Preserving Transforms):**
  * **권장하지 않는 패턴 (Bad):** `transforms.Resize((224, 224))` $\rightarrow$ 직사각형 이미지가 찌그러집니다 (Squishes/distorts rectangular images).
  * **권장 패턴 (Good):** `transforms.Resize(256)` + `transforms.CenterCrop(224)` $\rightarrow$ 짧은 변 기준으로 비율을 유지하며 축소한 뒤, 중앙부 정사각형을 크롭합니다 (scales shorter edge + crops middle square).

**[EN]**
* **Root Cause of Batch Failure:**
  * Raw dataset images have varying resolutions/dimensions.
  * DataLoader fails to stack images into $[N, C, H, W]$ tensor grids if dimensions mismatch.
* **Aspect Ratio Preserving Transforms:**
  * **Bad:** `transforms.Resize((224, 224))` $\rightarrow$ Squishes/distorts rectangular images.
  * **Good:** `transforms.Resize(256)` + `transforms.CenterCrop(224)` $\rightarrow$ Scales shorter edge + crops middle square.

---

## 2. The "ToTensor Bridge" & Normalization (ToTensor 다리와 정규화)

**[KR]**
* **`transforms.ToTensor()`의 3대 내부 메커니즘 (Mechanics of `transforms.ToTensor()`):**
  1) **포맷 변환 (Format Conversion):** PIL 이미지를 `torch.Tensor`로 변환합니다.
  2) **차원 순서 재배치 (Dimension Reordering):** $[H, W, C] \rightarrow [C, H, W]$
  3) **값 스케일링 (Value Scaling):** $[0, 255]$ 범위의 픽셀 정수값을 $255.0$으로 나누어 $[0.0, 1.0]$ 범위의 실수로 변환합니다.
* **정규화의 역할 (Role of Normalization):**
  $$ \text{Normalized Output (정규화된 값)} = \frac{\text{Pixel Value (픽셀 값)} - \text{Mean (평균)}}{\text{Std (표준편차)}} $$
  * 밝거나 어두운 배경 데이터가 극단으로 치우치는 현상을 방지하고 분포를 균일하게 펼칩니다 (Spreads out intensity distribution so bright/dark images don't cluster at extremes).
* **제약 조건 (Constraint):** `transforms.Normalize()`는 반드시 텐서(Tensor) 상태에서만 동작하므로, 무조건 `ToTensor()` 뒤에 위치해야 합니다.

**[EN]**
* **Mechanics of `transforms.ToTensor()`:**
  1) **Format Conversion:** Converts PIL Image to `torch.Tensor`.
  2) **Dimension Reordering:** $[H, W, C] \rightarrow [C, H, W]$
  3) **Value Scaling:** Divides all pixel integers $[0, 255]$ by $255.0 \rightarrow$ Range $[0.0, 1.0]$
* **Role of Normalization:**
  $$ \text{Normalized Output} = \frac{\text{Pixel Value} - \text{Mean}}{\text{Std}} $$
  * Spreads out intensity distribution so bright/dark images don't cluster at extremes.
* **Constraint:** `transforms.Normalize()` works strictly on Tensors (must be placed after `ToTensor()`).

---

## 3. Complete Custom Transform Pipeline Code (완성형 전처리 파이프라인 코드)

**[KR]**
* 아래는 앞서 설명한 규칙들을 모두 적용한 완성형 이미지 전처리 파이프라인 코드입니다.

**[EN]**
* Below is the complete image transformation pipeline code applying all the rules explained above.

```python
from torchvision import transforms 

# 이미지 전처리 파이프라인 정의
flower_transforms = transforms.Compose([ 
    transforms.Resize(256),       # 1. 짧은 변 기준 비율 유지 축소 (Image 영역)
    transforms.CenterCrop(224),   # 2. 중앙부 224x224 정사각형 크롭 (Image 영역)
    transforms.ToTensor(),        # 3. 다리 건너기 -> [C, H, W] 차원 및 [0.0, 1.0] 스케일링
    transforms.Normalize(         # 4. 표준화 분포 변환 (Tensor 영역)
        mean=[0.485, 0.456, 0.406], 
        std=[0.229, 0.224, 0.225] 
    ) 
]) 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-2 Transform Pipelines-1" src="https://github.com/user-attachments/assets/f01da387-355e-49f6-aa7e-f8a09a309575" />
    <img width="1264" height="1635" alt="3-2 Transform Pipelines-2" src="https://github.com/user-attachments/assets/5652aa18-a971-473e-b00c-293be61df5f1" />
  </div>
</details>
