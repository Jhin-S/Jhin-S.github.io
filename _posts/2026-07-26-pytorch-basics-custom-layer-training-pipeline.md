---
title: "PyTorch Basics: Custom Layer & Training Pipeline"
date: 2026-07-26 12:50:00 +0900
categories: ["Machine Learning & Deep Learning"]
tags: [pytorch, machine-learning, deep-learning, custom-layer, training-pipeline, neural-networks]
math: true
---

## 1. 개요 (Overview)

**[KR]** 파이토치(PyTorch)에서 `nn.Module`을 상속받아 사용자 정의 레이어(Custom Layer)와 모델(Model)을 직접 클래스로 정의하고, 학습(Forward, Loss, Backward, Optimize)시키는 가장 표준적인 구조를 알아봅니다.

**[EN]** This covers the most standard structure in PyTorch for directly defining custom layers and models as classes by inheriting `nn.Module`, and training them (Forward, Loss, Backward, Optimize).

---

## 2. 사용자 정의 선형 레이어 (Custom Linear Layer)

**[KR]** $Y = XW^T + b$ 연산을 직접 구현하는 사용자 정의 선형 레이어를 생성합니다. 가중치와 편향은 반드시 `nn.Parameter`로 선언해야 파이토치가 학습할 파라미터로 인식합니다. 가중치 $W$의 차원은 `(out_features, in_features)` 이며, 편향 $b$의 차원은 `out_features` 입니다.

**[EN]** We create a custom linear layer that directly implements the $Y = XW^T + b$ operation. Weights and biases must be declared as `nn.Parameter` so that PyTorch recognizes them as learnable parameters. The dimension of weight $W$ is `(out_features, in_features)`, and the dimension of bias $b$ is `out_features`.

```python
import torch 
import torch.nn as nn 
import torch.optim as optim 

class MyLinearLayer(nn.Module): 
    def __init__(self, in_features, out_features): 
        super().__init__() 
        
        # nn.Parameter로 선언해야 파이토치가 학습할 가중치/편향으로 인식한다.
        # W 차원: (out_features, in_features)
        self.W = nn.Parameter(torch.randn(out_features, in_features)) 
        
        # b 차원: out_features
        self.b = nn.Parameter(torch.zeros(out_features)) 

    def forward(self, x): 
        # x: (batch_size, in_features)
        # 반환 차원: (batch_size, out_features)
        return torch.matmul(x, self.W.T) + self.b 
```

## 3. 사용자 정의 모델 (Custom Model)

**[KR]** 위에서 만든 MyLinearLayer와 활성화 함수(ReLU) 등을 조합하여 전체 모델을 구성합니다. __init__에서 레이어들을 모델 내부 속성(Attribute)으로 등록하고, forward 메서드에서 순전파 흐름을 정의합니다.

**[EN]** We construct the full model by combining the MyLinearLayer created above with an activation function (ReLU). We register the layers as internal attributes of the model in __init__, and define the forward pass flow in the forward method.

```python
class MySimpleModel(nn.Module): 
    def __init__(self, input_dim, hidden_dim, output_dim): 
        super().__init__() 
        
        # 레이어들을 모델 내부 속성(Attribute)으로 등록
        self.layer1 = MyLinearLayer(input_dim, hidden_dim) 
        self.relu = nn.ReLU() 
        self.layer2 = MyLinearLayer(hidden_dim, output_dim) 

    def forward(self, x): 
        # 순전파 흐름 정의
        out = self.layer1(x) 
        out = self.relu(out) 
        out = self.layer2(out) 
        return out 
```

## 4. 데이터 준비 및 모델 설정 (Data Preparation & Setup)

**[KR]** 배치 크기가 4이고 특성 차원이 2인 예시 데이터를 준비합니다. 입력 차원을 2에서 4로 늘렸다가 최종적으로 1로 줄이는 모델 객체를 생성하고, 평균 제곱 오차(MSE) 손실 함수와 확률적 경사 하강법(SGD) 옵티마이저를 설정합니다.

**[EN]** We prepare example data with a Batch Size of 4 and a Feature dim of 2. We instantiate the model object that expands the input dimension from 2 to 4 and finally reduces it to 1, and we set up the Mean Squared Error (MSELoss) function and the Stochastic Gradient Descent (SGD) optimizer.

```python
# 데이터 준비 (Batch Size=4, Feature dim=2)
X_train = torch.tensor([[1.0, 2.0],
                        [3.0, 1.0],
                        [0.5, 4.0],
                        [2.0, 2.0]]) 

Y_train = torch.tensor([[5.0],
                        [7.0],
                        [9.0],
                        [6.0]]) 

# 모델 객체 생성 (입력 차원 2 -> 은닉 차원 4 -> 출력 차원 1)
model = MySimpleModel(input_dim=2, hidden_dim=4, output_dim=1) 

# 손실 함수(Loss Function) 및 옵티마이저(Optimizer) 설정
criterion = nn.MSELoss() 
optimizer = optim.SGD(model.parameters(), lr=0.01) 
```
## 5. 학습 루프 및 추론 (Training Loop & Inference)

**[KR]** 총 500 에포크(Epochs) 동안 학습을 반복합니다. 매 루프마다 model.train()으로 학습 모드를 활성화하고, 순전파, 손실 계산, 기울기 초기화(zero_grad), 역전파(backward), 파라미터 업데이트(step)의 5단계 과정을 거칩니다. 학습이 완료되면 model.eval() 및 torch.no_grad()를 사용하여 기울기 추적 없이 추론/평가를 수행하여 메모리를 절약합니다.

**[EN]** The training loop iterates for a total of 500 Epochs. During each loop, we activate training mode with model.train(), and go through a 5-step process: forward pass, loss calculation, gradient initialization (zero_grad), backward pass (backward), and parameter update (step). After training is complete, we perform inference/evaluation without tracking gradients to save memory, utilizing model.eval() and torch.no_grad().

```python
# 학습 루프 (Training Loop)
epochs = 500 
print("=== 학습 시작 ===") 

for epoch in range(1, epochs + 1): 
    # (1) 모델을 학습 모드로 전환
    model.train() 
    
    # (2) 순전파 (Forward Pass)
    predictions = model(X_train) 
    
    # (3) 손실(Loss) 계산
    loss = criterion(predictions, Y_train) 
    
    # (4) 역전파 (Backward Pass)
    # 이전 단계에서 축적된 기울기(Gradient) 초기화
    optimizer.zero_grad() 
    
    # 자동 미분으로 모든 parameter 기울기 계산 (dL/dw, dL/db)
    loss.backward() 
    
    # 파라미터 업데이트 (w = w - lr * grad)
    optimizer.step() 
    
    # 100번째 에포크마다 손실 출력
    if epoch % 100 == 0: 
        print(f"Epoch [{epoch}/{epochs}] - Loss: {loss.item():.4f}") 

# 추론 / 검증
model.eval() # 평가 모드로 전환
with torch.no_grad(): # 검증 시에는 기울기를 추적하지 않음 (메모리 절약)
    test_x = torch.tensor([[1.0, 2.0]]) 
    pred = model(test_x) 
    print(f"[추론 결과]\n입력: {test_x.numpy()} -> 예측값: {pred.item():.4f}") 
```

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="PyTorch Basics Custom Layer  Training Pipeline-1" src="https://github.com/user-attachments/assets/f399ab83-feb5-432b-9b5e-b2f8f7e4840e" />
    <img width="1264" height="1635" alt="PyTorch Basics Custom Layer  Training Pipeline-2" src="https://github.com/user-attachments/assets/f7e5d96f-04b7-415c-874e-af954a8f85fb" />
    <img width="1264" height="1635" alt="PyTorch Basics Custom Layer  Training Pipeline-3" src="https://github.com/user-attachments/assets/767c48ba-53e7-437d-a881-9c11035623e6" />
    <img width="1264" height="1635" alt="PyTorch Basics Custom Layer  Training Pipeline-4" src="https://github.com/user-attachments/assets/d0a67bbb-294b-41d7-ad63-3b3aa9ee5bfe" />
  </div>
</details>
