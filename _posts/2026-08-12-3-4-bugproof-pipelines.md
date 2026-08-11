---
title: "3-4 Bugproof Pipelines"
date: 2026-08-12 06:10:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, data-augmentation, error-handling, de-normalization]
math: true
---

## 1. On-the-Fly Data Augmentation (실시간 데이터 증강)

**[KR]**
* **증강을 수행하는 이유 (Why Augment):**
  * 조명 조건이나 정중앙 배치 등 특정 패턴에만 치우치는 과적합(Over-fitting)을 방지합니다.
  * 지엽적인 구도 대신 핵심 특성(모양, 색상)에 집중하도록 유도합니다.
* **실시간 전략 (On-the-Fly Strategy):**
  * 매 에포크마다 메모리 상에서 동적으로 무작위 연산을 적용하여 디스크 저장 공간을 절약합니다.

**[EN]**
* **Why Augment:**
  * Prevents over-fitting to specific lighting or centered compositions.
  * Teaches the model to recognize structural features (shape, color) rather than superficial details.
* **On-the-Fly Strategy:**
  * Transformations are applied dynamically in memory when images are loaded during each epoch.

### 학습용 대 검증용 변환 파이프라인 분리 (Train vs Validation Transforms)

```python
from torchvision import transforms 

# 학습용 변환 (무작위 증강 포함) - Train Transforms
train_transforms = transforms.Compose([ 
    transforms.RandomResizedCrop(224), 
    transforms.RandomHorizontalFlip(), 
    transforms.ColorJitter(brightness=0.2, contrast=0.2), 
    transforms.ToTensor(), 
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]) 
]) 

# 검증용 변환 (증강 제거 - 평가 일관성 유지) - Validation Transforms
val_transforms = transforms.Compose([ 
    transforms.Resize(256), 
    transforms.CenterCrop(224), 
    transforms.ToTensor(), 
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]) 
]) 
```

---

## 2. Robust Error Handling with Recursive `__getitem__` (재귀 호출을 활용한 예외 처리)

**[KR]**
* **문제 상황 (Problem):** 손상된 이미지 단 1장 때문에 4시간 동안 돌아가던 학습 루프가 멈추는(breaking) 현상.
* **내부 해결 패턴 (Solution Pattern inside `__getitem__`):** `try-except`와 재귀(Recursive) 호출을 활용하여 다음 샘플을 로드합니다.

**[EN]**
* **Problem:** A single corrupted image breaking a multi-hour training run.
* **Solution Pattern inside `__getitem__`:** Utilizes `try-except` and recursive calls to bypass and load the next sample.

```python
def __getitem__(self, idx): 
    try: 
        file_idx = idx + 1 
        img_path = os.path.join(self.img_dir, f"image_{file_idx:05d}.jpg") 
        
        # 이미지 로드 및 손상 검증
        image = Image.open(img_path) 
        image.verify() # 파일 손상 여부 확인
        image = Image.open(img_path).convert("RGB") # 재오픈 및 RGB 채널 보정
        
        if self.transform: 
            image = self.transform(image) 
            
        label = self.labels[idx] 
        return image, label 
        
    except Exception as e: 
        print(f"[경고] 인덱스 {idx} 에서 손상된 이미지 발견: {e}") 
        # 프로그램 중단 없이 다음 샘플로 재귀적(Recursive) 우회 로딩!
        next_idx = (idx + 1) % len(self) 
        return self.__getitem__(next_idx) 
```

---

## 3. De-normalization for Visualization (시각화를 위한 역정규화)

**[KR]**
* **검증을 위한 정규화 해제 (Undoing Normalization for Inspection):** 모델에 입력하기 위해 정규화되었던 텐서를 시각화하기 위해 역으로 연산합니다.

**[EN]**
* **Undoing Normalization for Inspection:** Reversing the normalization applied to the tensor to properly visualize it.

```python
import torch 
import matplotlib.pyplot as plt 

def denormalize(tensor, mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]): 
    # 원본 텐서 변형 방지를 위해 복사본 생성
    tensor = tensor.clone() 
    
    for t, m, s in zip(tensor, mean, std): 
        t.mul_(s).add_(m) # 역연산: 원본 = 정규화값 * 표준편차 + 평균
        
    return torch.clamp(tensor, 0, 1) 

# 활용법: 증강 처리된 이미지 텐서를 가시적으로 시각화
# plt.imshow(denormalize(img_tensor).permute(1, 2, 0)) 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-4 Bugproof Pipelines-1" src="https://github.com/user-attachments/assets/6beda765-9643-4649-bb67-8075a0221e84" />
    <img width="1264" height="1635" alt="3-4 Bugproof Pipelines-2" src="https://github.com/user-attachments/assets/7c457499-00e3-4dfd-b915-79a988d6bf70" />
    <img width="1264" height="1635" alt="3-4 Bugproof Pipelines-3" src="https://github.com/user-attachments/assets/ccd6c5c8-dfa8-4c2c-8c98-ad1248bb2da4" />
  </div>
</details>
