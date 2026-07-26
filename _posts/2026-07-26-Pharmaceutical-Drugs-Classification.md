---
title: "의약품 재고 관리를 위한 AI 컴퓨터비전 파이프라인 구축 (ResNet & YOLO)"
date: 2026-07-26 14:07:00 +0900
categories: ["Machine Learning & Deep Learning"]
tags: [ai, computer-vision, pytorch, resnet18, yolov5, image-classification, object-detection, smart-logistics]
---

최근 의료 헬스케어와 스마트 물류(재고 관리) 분야의 AI 활용에 관심이 생겨 기획해 본 미니 프로젝트입니다.

여담 (Thoughts on AI Learning)

이번 프로젝트의 데이터는 [Kaggle: Pharmaceutical Drugs Classification using YOLOv5](https://www.kaggle.com/code/vencerlanz09/pharmaceutical-drugs-classification-using-yolov5/notebook)에서 받아와 진행하였으며, 코드는 Gemini의 도움을 받아 작성하였습니다. 
AI 시대에 어떻게 공부해야 하는가에 대해 많은 고민을 해왔습니다. 저의 결론은 대략 이러합니다. 단순히 많은 지식을 기억하는 일이나 프로그래밍 언어의 세세한 문법을 전부 파악하는 일은 사실 AI 시대가 도래하기 이전에도 현명한 공부법이 아니었다고 생각합니다. 그런데 AI 시대가 되며 그러한 단편적인 학습 방법은 매우 비효율적이며, 학습의 의미가 성장이 아닌 잘못된 방향으로 흘러가는 주객이 전도된 방법이라 생각합니다.
물론 코드를 아예 읽지도 못하거나 하는 것은 문제가 되는 것이 사실이며 그것을 부정하는 것은 아닙니다. 이번 프로젝트 또한 여태까지의 모든 포스팅이 그러하였듯이, **손으로 직접 적으며 분석한 필기노트**가 첨부될 예정입니다. :)

---

## 1. 서론 및 데이터 준비 (Introduction & Data Setup)

폴더 구조는 다음과 같이 10개의 클래스(의약품 종류)로 배치하였습니다. 데이터 디렉토리 내의 각 디렉토리에는 `00000000.jpg`부터 `00000999.jpg`까지의 이미지 데이터가 들어있습니다.

```text
C:\Pharmaceutical Drugs Classification\data\
 ├── Alaxan
 ├── Bactidol
 ├── Bioflu
 ├── Biogesic
 ├── DayZinc
 ├── Decolgen
 ├── Fish Oil
 ├── Kremil S
 ├── Medicol
 └── Neozep
```

<img width="300" height="300" alt="00000000" src="https://github.com/user-attachments/assets/193eb961-d584-4fce-9897-d6248b8dc456" />

예시로 첨부한 [Alaxan의 00000000.jpg]

## 2. 모델 학습 (ResNet18 Training)

C:\Pharmaceutical Drugs Classification\main.ipynb 파일을 만든 후 본격적으로 Pharmaceutical Drugs Classification을 진행하였습니다. 첫 번째 셀의 코드는 다음과 같습니다.

여담 (Hardware Setup)

AI 공부를 시작하면서 GPU 장비 욕심에 RTX 5090 Laptop이 탑재된 노트북을 구매하였고, 이 장비를 통해 여러 프로젝트를 진행해왔습니다. 그러나 이번 프로젝트에서 버전 호환 문제가 몇 차례 발생하여, 미니 프로젝트임을 감안해 과감히 CPU로 학습을 진행하였습니다. 내용에는 전혀 달라질 것이 없으며 학습 시간에도 큰 무리가 없었습니다.

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torchvision import datasets, models, transforms
from torch.utils.data import DataLoader, random_split
import os

# ==========================================
# 1. 기본 설정 (디바이스 및 하이퍼파라미터)
# ==========================================
# GPU가 있으면 사용하고, 없으면 CPU를 사용합니다.
# device = torch.device("cuda" if torch.cuda.is_available() else "cpu") <<< RTX 5090 Laptop에서 호환 문제 발생
device = torch.device("cpu") # 강제로 CPU 할당
print(f"현재 사용 중인 디바이스: {device}")

BATCH_SIZE = 32
EPOCHS = 10
LEARNING_RATE = 0.001

# 데이터가 있는 최상위 폴더 경로 (r을 붙여 이스케이프 문자 오류 방지)
data_dir = r"C:\Pharmaceutical Drugs Classification\data"

# ==========================================
# 2. 데이터 전처리 (Transforms)
# ==========================================
data_transforms = transforms.Compose([
    transforms.Resize((224, 224)), # ResNet 기본 입력 사이즈로 통일
    transforms.ToTensor(),         # 이미지를 파이토치 텐서(0~1 사이 값)로 변환
    transforms.Normalize([0.485, 0.456, 0.406], [0.229, 0.224, 0.225]) # 정규화 (표준 스케일)
])

# ==========================================
# 3. 데이터셋 불러오기 및 Train/Val 나누기
# ==========================================
full_dataset = datasets.ImageFolder(root=data_dir, transform=data_transforms)
print(f"총 데이터 개수: {len(full_dataset)}")
print(f"클래스 종류: {full_dataset.classes}") # 10개의 약 이름 출력

# Train(80%)과 Validation(20%)으로 데이터 나누기
train_size = int(0.8 * len(full_dataset))
val_size = len(full_dataset) - train_size
train_dataset, val_dataset = random_split(full_dataset, [train_size, val_size])

train_loader = DataLoader(train_dataset, batch_size=BATCH_SIZE, shuffle=True)
val_loader = DataLoader(val_dataset, batch_size=BATCH_SIZE, shuffle=False)

# ==========================================
# 4. AI 모델 불러오기 및 수정 (ResNet18)
# ==========================================
model = models.resnet18(weights=models.ResNet18_Weights.IMAGENET1K_V1)

# 마지막 출력층(Fully Connected Layer)을 클래스 개수(10개)에 맞게 수정
num_ftrs = model.fc.in_features
model.fc = nn.Linear(num_ftrs, 10) 
model = model.to(device) 

# ==========================================
# 5. 손실 함수와 최적화 기법 (Loss & Optimizer)
# ==========================================
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=LEARNING_RATE)

# ==========================================
# 6. 모델 학습 루프 (Training Loop)
# ==========================================
print("학습을 시작합니다!")

for epoch in range(EPOCHS):
    # --- 1) 학습 단계 ---
    model.train()
    running_loss = 0.0
    
    for images, labels in train_loader:
        images, labels = images.to(device), labels.to(device)
        
        optimizer.zero_grad()      # 이전 배치의 기울기 초기화
        outputs = model(images)    # 예측값 계산
        loss = criterion(outputs, labels) # Loss 계산
        
        loss.backward()            # 역전파(기울기 계산)
        optimizer.step()           # 가중치 업데이트
        
        running_loss += loss.item() * images.size(0)
        
    epoch_loss = running_loss / train_size
    
    # --- 2) 검증 단계 ---
    model.eval()
    corrects = 0
    
    with torch.no_grad():
        for images, labels in val_loader:
            images, labels = images.to(device), labels.to(device)
            outputs = model(images)
            
            _, preds = torch.max(outputs, 1) 
            corrects += torch.sum(preds == labels.data)
            
    epoch_acc = corrects.double() / val_size
    
    print(f"Epoch {epoch+1}/{EPOCHS} | Train Loss: {epoch_loss:.4f} | Val Accuracy: {epoch_acc:.4f}")

print("학습 종료!")
```
```text
[첫 번째 셀의 결과]

현재 사용 중인 디바이스: cpu
총 데이터 개수: 10000
클래스 종류: ['Alaxan', 'Bactidol', 'Bioflu', 'Biogesic', 'DayZinc', 'Decolgen', 'Fish Oil', 'Kremil S', 'Medicol', 'Neozep']
학습을 시작합니다!
Epoch 1/10 | Train Loss: 0.3505 | Val Accuracy: 0.9535
Epoch 2/10 | Train Loss: 0.1304 | Val Accuracy: 0.9575
Epoch 3/10 | Train Loss: 0.1067 | Val Accuracy: 0.9700
Epoch 4/10 | Train Loss: 0.1072 | Val Accuracy: 0.9675
Epoch 5/10 | Train Loss: 0.0683 | Val Accuracy: 0.9515
Epoch 6/10 | Train Loss: 0.0706 | Val Accuracy: 0.9700
Epoch 7/10 | Train Loss: 0.0600 | Val Accuracy: 0.9785
Epoch 8/10 | Train Loss: 0.0591 | Val Accuracy: 0.9850
Epoch 9/10 | Train Loss: 0.0274 | Val Accuracy: 0.9930
Epoch 10/10 | Train Loss: 0.0490 | Val Accuracy: 0.9685
학습 종료!
```
## 3. 학습 결과 시각화 (Loss & Accuracy)
다음은 학습 결과 시각화를 위해 작성된 두 번째 셀의 코드입니다.

```python
import matplotlib.pyplot as plt

# ==========================================
# 1. 학습 결과 데이터 입력
# ==========================================
epochs = list(range(1, 11))
train_losses = [0.3477, 0.1475, 0.1285, 0.0982, 0.0512, 0.1010, 0.0337, 0.0606, 0.0534, 0.0294]
val_accuracies = [0.9540, 0.9495, 0.9820, 0.9615, 0.9815, 0.9815, 0.9860, 0.9660, 0.9680, 0.9755]

# ==========================================
# 2. 그래프 그리기
# ==========================================
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

# Train Loss 그래프
ax1.plot(epochs, train_losses, marker='o', color='red', label='Train Loss')
ax1.set_title('Training Loss')
ax1.set_xlabel('Epochs')
ax1.set_ylabel('Loss')
ax1.set_xticks(epochs)
ax1.grid(True, linestyle='--', alpha=0.5)
ax1.legend()

# Validation Accuracy 그래프
ax2.plot(epochs, val_accuracies, marker='o', color='blue', label='Validation Accuracy')
ax2.set_title('Validation Accuracy')
ax2.set_xlabel('Epochs')
ax2.set_ylabel('Accuracy')
ax2.set_xticks(epochs)
ax2.grid(True, linestyle='--', alpha=0.5)
ax2.legend()

plt.tight_layout()
plt.show()
```

[두번째 셀의 결과]
<img width="1189" height="490" alt="학습 결과 시각화 (Loss   Accuracy)" src="https://github.com/user-attachments/assets/0aff21fd-67e9-4cf2-8f1d-9cb3b76c81da" />

## 4. 오차 행렬 (Confusion Matrix) 및 F1-Score

정확도 외에 클래스별 세부 성능을 파악하기 위해 혼동 행렬과 F1-Score를 출력하는 세 번째 셀입니다.

```python
import torch
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.metrics import classification_report, confusion_matrix

# ==========================================
# 1. 예측값과 정답 데이터 모으기
# ==========================================
model.eval() 
all_preds = []
all_labels = []

print("평가를 시작합니다...")

with torch.no_grad():
    for images, labels in val_loader:
        images = images.to(device)
        labels = labels.to(device)
        
        outputs = model(images)
        _, preds = torch.max(outputs, 1) 
        
        all_preds.extend(preds.cpu().numpy())
        all_labels.extend(labels.cpu().numpy())

class_names = full_dataset.classes

# ==========================================
# 2. F1-Score 등 성능 리포트 출력
# ==========================================
print("\n[ 분류 성능 리포트 ]")
print(classification_report(all_labels, all_preds, target_names=class_names))

# ==========================================
# 3. 오차 행렬(Confusion Matrix) 그리기
# ==========================================
cm = confusion_matrix(all_labels, all_preds)

plt.figure(figsize=(10, 8))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues',
            xticklabels=class_names, yticklabels=class_names)

plt.title('Confusion Matrix')
plt.xlabel('Predicted')
plt.ylabel('Actual')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
[세 번째 셀의 결과]

```text
평가를 시작합니다...

[ 분류 성능 리포트 ]
              precision    recall  f1-score   support

      Alaxan       0.99      0.98      0.99       194
    Bactidol       0.98      0.98      0.98       194
      Bioflu       0.99      0.87      0.93       221
    Biogesic       0.99      0.92      0.96       214
     DayZinc       0.96      0.98      0.97       200
    Decolgen       1.00      0.99      1.00       195
    Fish Oil       0.97      1.00      0.98       213
    Kremil S       0.95      1.00      0.98       176
     Medicol       1.00      1.00      1.00       196
      Neozep       0.86      0.97      0.91       197

    accuracy                           0.97      2000
   macro avg       0.97      0.97      0.97      2000
weighted avg       0.97      0.97      0.97      2000
```

<img width="920" height="790" alt="오차 행렬(Confusion Matrix) 및 F1-Score" src="https://github.com/user-attachments/assets/2cb83c92-cf0c-4404-9908-5b5218a06957" />


## 5. 객체 탐지 시도 (YOLOv5 Object Detection)

단순 이미지 분류를 넘어 재고 관리에 필수적인 객체 탐지를 YOLOv5 사전 학습 모델로 실험해 본 네 번째 셀입니다.

```python
import torch
import matplotlib.pyplot as plt
import os

# ==========================================
# 1. YOLOv5 모델 불러오기 (PyTorch Hub 활용)
# ==========================================
print("YOLOv5 모델을 불러오는 중...")
model_yolo = torch.hub.load('ultralytics/yolov5', 'yolov5s', pretrained=True, device='cpu')

# ==========================================
# 2. 클래스별 샘플 이미지 1장씩 추출 (총 10장)
# ==========================================
data_dir = r"C:\Pharmaceutical Drugs Classification\data"
class_names = ['Alaxan', 'Bactidol', 'Bioflu', 'Biogesic', 'DayZinc', 
               'Decolgen', 'Fish Oil', 'Kremil S', 'Medicol', 'Neozep']

sample_image_paths = []

for cls in class_names:
    cls_dir = os.path.join(data_dir, cls)
    images = os.listdir(cls_dir)
    
    if images:
        sample_path = os.path.join(cls_dir, images[0]) 
        sample_image_paths.append(sample_path)

# ==========================================
# 3. 객체 탐지(Object Detection) 수행
# ==========================================
print(f"\n총 {len(sample_image_paths)}개의 샘플 이미지에 대해 객체 탐지를 시작합니다...")
results = model_yolo(sample_image_paths)

# ==========================================
# 4. 탐지 결과 시각화 (2x5 Grid)
# ==========================================
print("\n[ 탐지 결과 요약 ]")
results.print()

fig, axes = plt.subplots(2, 5, figsize=(20, 8))
fig.suptitle('YOLOv5 Object Detection - Pre-trained Model Test', fontsize=16)

rendered_images = results.render()

for i, ax in enumerate(axes.flat):
    if i < len(rendered_images):
        ax.imshow(rendered_images[i])
        ax.set_title(class_names[i])
        ax.axis('off')
    else:
        ax.axis('off')

plt.tight_layout()
plt.show()
```
[네 번째 셀의 결과]
```text
image 1/10: 300x300 (no detections)
image 2/10: 300x300 (no detections)
image 3/10: 300x300 1 kite
image 4/10: 300x300 1 kite, 2 carrots
image 5/10: 300x300 (no detections)
image 6/10: 300x300 1 frisbee
image 7/10: 300x300 2 frisbees
image 8/10: 300x300 1 sports ball
image 9/10: 300x300 1 frisbee, 2 sports balls
image 10/10: 300x300 (no detections)
Speed: 3.2ms pre-process, 32.0ms inference, 0.8ms NMS per image at shape (10, 3, 640, 640)
```

## 6. 최종 결과 해석 (Final Interpretation)

1. 학습 곡선 (Loss & Accuracy) 해석: "과적합(Overfitting)의 경계선"

관찰 결과: Training Loss 그래프를 보면 1~9 Epoch 동안 손실값이 0.35에서 0.02 수준으로 매우 이상적으로 꾸준히 하락하지만, 10 Epoch에서 0.0490으로 반등하는 모습이 관찰됩니다. Validation Accuracy 역시 Epoch 9에서 99.30%로 정점을 찍은 후, 10 Epoch에서는 오히려 정확도가 96.85%로 급락하는 모습이 뚜렷하게 관찰됩니다.

엔지니어의 시각: 이는 전형적인 과적합(Overfitting) 초기 증상입니다. 모델이 훈련 데이터의 지엽적인 픽셀이나 노이즈까지 지나치게 암기하기 시작하면서, 처음 보는 검증 데이터에 대한 일반화(Generalization) 성능이 떨어지기 시작한 것입니다.

분석 및 해결책: 이러한 수리적 근거를 바탕으로 최적의 모델 가중치는 Epoch 9에 형성되었다고 판단할 수 있으며, 향후 시스템 고도화 시 조기 종료(Early Stopping) 콜백을 적용하여 과적합을 제어해야한다.

2. 오차 행렬 (Confusion Matrix) 해석: "진짜 문제는 Bioflu와 Neozep"

관찰 결과: 모델의 전체 정확도가 97%에 달하지만, 실무(물류 창고 등)에서는 '틀린 3%'로 인해 재고 오차가 발생합니다. 오차 행렬을 자세히 보면, 실제 정답이 Bioflu인 221개의 데이터 중 무려 25개가 Neozep으로 오분류되었습니다.

지표와의 교차 검증: 분류 성능 리포트에서 Neozep의 Precision(정밀도)이 0.86으로 10개 약품 중 가장 낮고, Bioflu의 Recall(재현율)이 0.87로 가장 낮게 나온 이유가 바로 이 25개의 오분류 데이터 때문입니다. (즉, 모델이 Neozep이라고 대답했을 때 진짜 Neozep일 확률이 떨어졌다는 뜻입니다.)

엔지니어의 시각: 딥러닝 모델이 다차원 벡터 공간에서 Bioflu와 Neozep의 시각적 특징(포장지 색상, 알약의 형태, 글씨체 등)을 뚜렷하게 분리(Linear Separation)하지 못하고 혼동하고 있다는 의미입니다.

분석 및 해결책: Bioflu와 Neozep 간의 클래스 혼동 현상이 발견되었습니다. 이 문제를 해결하기 위해 두 약품 이미지에 대비(Contrast) 조절이나 컷아웃(Cutout) 등의 특정 데이터 증강 기법을 집중적으로 적용하여 두 클래스 간의 특징 공간(Feature Space)을 강제로 분리하는 실험을 추가로 진행해야 합니다.

YOLOv5 객체 탐지 시도 (10개 클래스 샘플링을 통한 사전 타당성(Feasibility) 검증)

관찰 결과: 탐지 결과를 보면 의약품을 전혀 탐지하지 못하거나(no detections), 알약과 포장지를 kite(연), carrots(당근), frisbee(원반), sports ball(스포츠 공) 등 전혀 엉뚱한 객체로 잘못 인식하는 현상이 뚜렷하게 관찰되었습니다.

엔지니어의 시각: 이는 해당 YOLOv5s 모델이 COCO 데이터셋(일상 사물 80종)으로 학습되어 있어 발생하는 전형적인 Domain Gap(도메인 격차) 현상입니다. 모델이 제약품 패키지의 고유한 시각적 특징(특정 텍스트 폰트, 알약의 배열, 포장재의 반사광 등)을 인식할 도메인 지식이 전혀 없음을 수리적, 시각적으로 확인했습니다.

분석 및 해결책: 단순한 이미지 분류(Image Classification)를 넘어, 실제 의약품의 재고 수량 추정, 위치 파악, 입출고 자동화 등 재고관리를 수행하는 AI 시스템을 구축하기 위해서는 객체 탐지(Object Detection) 파이프라인의 고도화가 필수적입니다. 따라서 데이터를 YOLO 포맷으로 전처리한 뒤 의약품 도메인에 특화된 가중치로 모델을 파인튜닝(Fine-Tuning)하는 것이 본 프로젝트의 한계점 및 다음 절차라 할 수 있겠습니다.


<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 코드분석 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="코드분석-1" src="https://github.com/user-attachments/assets/a946e172-aced-46ef-9ba1-e8baf585b2fa" />
    <img width="1264" height="1635" alt="코드분석-2" src="https://github.com/user-attachments/assets/5440de7f-f1dd-45ee-b044-bd1cfddd8704" />
    <img width="1264" height="1635" alt="코드분석-3" src="https://github.com/user-attachments/assets/4fec399c-a13b-40c9-afe6-0f6abf5966d7" />
    <img width="1264" height="1635" alt="코드분석-4" src="https://github.com/user-attachments/assets/0e8a69b0-f737-458a-8863-c0966d6ab8e7" />
    <img width="1264" height="1635" alt="코드분석-5" src="https://github.com/user-attachments/assets/e2b806c4-fdb7-4f59-a9a6-2e27e376db57" />
    <img width="1264" height="1635" alt="코드분석-6" src="https://github.com/user-attachments/assets/2dfdfd77-087c-4439-8773-1b8a4b963e35" />
  </div>
</details>













