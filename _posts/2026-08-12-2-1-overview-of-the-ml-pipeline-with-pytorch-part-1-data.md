---
title: "2-1 Overview of the ML Pipeline with PyTorch Part 1: Data"
date: 2026-08-12 05:01:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, ml-pipeline, data-loader, dataset]
math: true
---

## 1. The Scalability Problem & Batch Solution (데이터 스케일 문제 및 배치 처리)

**[KR]**
* **메모리 병목 현상 (Memory Bottleneck):** 수백만 개의 원시 배달 기록(또는 고해상도 이미지)을 한꺼번에 로드하면 RAM 용량을 초과하여 시스템이 다운(crashes)됩니다.
* **핵심 철학 (Core Philosophy):**
  * **지연 로딩 (Lazy Loading):** 모든 데이터를 한꺼번에 메모리에 올리지 않습니다.
  * 미니배치(Mini-Batches)를 활용하여 "필요한 순간에 필요한 만큼만" 로드합니다.

**[EN]**
* **Memory Bottleneck:** Loading millions of raw delivery records (or high-res images) at once overwhelms RAM, causing system crashes.
* **Core Philosophy:**
  * **Lazy Loading:** Do not preload all data into memory at once.
  * Load only what you need, when you need it using Mini-Batches.

---

## 2. PyTorch Data Pipeline Components (PyTorch 데이터 파이프라인 구성 요소)

### Step 1: Transforms (`torchvision.transforms`)

**[KR]**
* **입력값을 0을 중심으로 만드는 이유:** 신경망은 입력값이 작고 0 근처에 모여 있을 때 학습 속도와 안정성이 극대화됩니다.

**[EN]**
* **Why center data around 0?:** Neural networks train faster and more stably when inputs have small, zero-centered ranges.

```python
from torchvision import transforms 

transform = transforms.Compose([ #
    transforms.ToTensor(), # 텐서 변환 및 0.0~1.0 사이 값 스케일링
    transforms.Normalize(mean=[0.5], std=[0.5]) # 0 평균 중심으로 정규화
]) 
```

### Step 2: Dataset (`torch.utils.data.Dataset`)

**[KR]**
* 데이터 세트의 메타데이터, 디스크 저장 경로, 전체 개수(`len()`), 인덱스 접근(`dataset[i]`) 및 로드 시 Transform 적용을 담당합니다.

**[EN]**
* Manages dataset metadata, disk storage paths, total length (`len()`), and Indexing (`dataset[i]`).

```python
from torchvision.datasets import MNIST 

dataset = MNIST( 
    root='./data', # 데이터 저장 경로
    train=True,    # 학습용/테스트용 구분
    download=True, # 자동 다운로드
    transform=transform # 전처리 파이프라인 적용
) 
```

### Step 3: DataLoader (`torch.utils.data.DataLoader`)

**[KR]**
* Dataset의 개별 샘플들을 미니배치 단위(`batch_size=64`)로 묶어서 공급합니다.
* `shuffle=True`는 데이터 순서 편향을 방지하기 위해 에포크마다 순서를 무작위로 섞습니다.

**[EN]**
* Groups Single Samples from Dataset into mini-batches (`batch_size=64`).
* `shuffle=True` breaks temporal/ordering bias during model training.

```python
from torch.utils.data import DataLoader 

dataloader = DataLoader( 
    dataset, 
    batch_size=64, 
    shuffle=True 
) 
```

---

## 3. Complete Data Pipeline Workflow (전체 파이프라인 흐름)

**[KR]**
1) 디스크 상의 원시 데이터 (Raw Data on Disk)
2) Dataset의 인덱스 기반 데이터 요청 (Dataset indexing request)
3) Transform을 통한 실시간 전처리/정규화 (Transforms applied on-the-fly)
4) DataLoader가 지정된 배치 크기만큼 묶음 생성 (DataLoader batches multiple items)
5) 신경망 모델로 배치 데이터 전달 (Forward to Neural Network Model)

**[EN]**
1) Raw Data on Disk $\rightarrow$
2) Dataset indexing request $\rightarrow$
3) Transforms applied on-the-fly $\rightarrow$
4) DataLoader batches multiple items $\rightarrow$
5) Forwarded to Neural Network Model

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-1 Overview of the ML Pipeline with PyTorch Part 1_ Data-1" src="https://github.com/user-attachments/assets/aaf8f42f-aab1-4d06-960d-49570dac4070" />
    <img width="1264" height="1635" alt="2-1 Overview of the ML Pipeline with PyTorch Part 1_ Data-2" src="https://github.com/user-attachments/assets/68642a39-f764-49e1-aee9-d8073857e07e" />
  </div>
</details>
