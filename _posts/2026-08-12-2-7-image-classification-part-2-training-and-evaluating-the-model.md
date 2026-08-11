---
title: "2-7 Image Classification - Part 2: Training and Evaluating the Model"
date: 2026-08-12 05:38:00 +0900
categories: ["PyTorch for Deep Learning Professional Certificate", "PyTorch: Fundamentals"]
tags: [pytorch, deep-learning, machine-learning, image-classification, training-loop, evaluation]
math: true
---

## 1. Training Setup & Initialization (학습 설정 및 초기화)

**[KR]**
* **설정 파이프라인 (Setup Pipeline):** 모델을 인스턴스화하여 장치(Device)로 이동시키고, 손실 함수와 최적화 알고리즘을 정의합니다.

**[EN]**
* **Setup Pipeline:** Instantiate the model, move it to the device, and define the loss function and optimization algorithm.

```python
import torch 
import torch.nn as nn 
import torch.optim as optim 

# 장치 선택 (Device Selection)
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu') 

# 모델 인스턴스화 및 장치 이동 (Instantiate model and move to device)
model = DigitClassifier().to(device) 

# 손실함수 및 최적화 알고리즘 정의 (Define loss function and optimizer)
criterion = nn.CrossEntropyLoss() 
optimizer = optim.Adam(model.parameters(), lr=0.001) 
```

---

## 2. Single Epoch Training Function (1 에포크 학습 함수)

**[KR]**
* **구현 패턴 (Implementation Pattern):** PyTorch의 표준 학습 루프 5단계를 포함하여 손실 값과 정확도를 추적(Tracking)하는 함수를 구성합니다.

**[EN]**
* **Implementation Pattern:** Construct a function tracking loss and accuracy, including PyTorch's standard 5-step training loop.

```python
def train_one_epoch(model, dataloader, criterion, optimizer, device): 
    model.train() # 모델을 학습 모드로 설정
    running_loss = 0.0 
    correct = 0 
    total = 0 

    for inputs, targets in dataloader: 
        inputs, targets = inputs.to(device), targets.to(device) 

        optimizer.zero_grad() 
        outputs = model(inputs) 
        loss = criterion(outputs, targets) 
        loss.backward() 
        optimizer.step() 

        # 손실값 및 정확도 추적
        running_loss += loss.item() * inputs.size(0) 
        _, predicted = outputs.max(1) 
        correct += predicted.eq(targets).sum().item() 
        total += targets.size(0) 

    epoch_loss = running_loss / total 
    epoch_acc = correct / total 
    
    return epoch_loss, epoch_acc 
```

---

## 3. Evaluation Function & Full Training Loop (평가 함수 및 전체 학습 루프)

**[KR]**
* **평가 함수 구현 (Evaluation Implementation):** 기울기 계산을 비활성화하고 전체 정확도를 반환합니다.
* **전체 다중 에포크 실행 (Full Multi-Epoch Execution):** 정해진 에포크 수만큼 학습과 평가를 반복합니다.

**[EN]**
* **Evaluation Implementation:** Disables gradient calculation and returns overall accuracy.
* **Full Multi-Epoch Execution:** Repeats training and evaluation for a set number of epochs.

```python
def evaluate(model, dataloader, device): 
    model.eval() # 모델을 평가 모드로 설정
    correct = 0 
    total = 0 

    with torch.no_grad(): 
        for inputs, targets in dataloader: 
            inputs, targets = inputs.to(device), targets.to(device) 
            
            outputs = model(inputs) 
            _, predicted = outputs.max(1) 
            correct += predicted.eq(targets).sum().item() 
            total += targets.size(0) 

    return correct / total 

# 전체 다중 에포크 실행 (Full Multi-Epoch Execution)
epochs = 10 
for epoch in range(epochs): 
    train_loss, train_acc = train_one_epoch(model, train_loader, criterion, optimizer, device) 
    test_acc = evaluate(model, test_loader, device) 
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-7 Image Classification - Part 2_ Training and Evaluating the Model-1" src="https://github.com/user-attachments/assets/53c711c2-111a-4908-b1df-b73f0838a255" />
    <img width="1264" height="1635" alt="2-7 Image Classification - Part 2_ Training and Evaluating the Model-2" src="https://github.com/user-attachments/assets/7ee15076-e572-4fbc-867c-ad3d32496683" />
    <img width="1264" height="1635" alt="2-7 Image Classification - Part 2_ Training and Evaluating the Model-3" src="https://github.com/user-attachments/assets/0c5afe3a-7c8b-4fc7-b884-ab8fa6b5d20f" />
  </div>
</details>
