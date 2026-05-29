---
title: "Virtual Keyword"
date: 2026-05-29 17:20:00 +0900
categories: ["C++"]
tags: [cpp, oop, virtual, polymorphism, dynamic_binding, inheritance]
---

## 1. 가상함수와 다형성 (Virtual Functions & Polymorphism)

**[KR]** 객체지향 프로그래밍(OOP)에서 상속을 사용할 때, 부모 클래스의 메서드를 자식 클래스에서 재정의(Overriding)하는 경우가 많습니다. 이때 `virtual` 키워드는 프로그램 실행(런타임) 중에 컴파일러가 올바른 자식 클래스의 메서드를 찾아가도록 유도하는 핵심 역할을 합니다.

예를 들어, 수학식을 그리는 프로그램에서 부모 클래스인 `MathFunction`을 상속받아 다항식을 계산하는 `SparsePolynomial` 클래스와 삼각함수를 계산하는 `SineFunction` 클래스를 만들었다고 가정해 보겠습니다. 모든 수학 함수는 특정 `x` 값을 넣으면 `y` 값을 반환해야 하므로, 부모 클래스에 `Eval(float x)` 메서드를 정의하고 자식들이 각자의 계산 로직에 맞게 이를 오버라이딩(Overriding)하게 됩니다.

---

## 2. 가상함수가 없을 때의 문제점 (정적 바인딩)

**[KR]** 컴파일러에게 자식 클래스의 메서드를 우선적으로 확인하라는 신호(`virtual`)를 주지 않고 클래스를 설계하면, 다형성을 활용하려 할 때 치명적인 버그가 발생합니다.

```cpp
#include <iostream>

// 부모 클래스 설계 (virtual 키워드 없음)
class MathFunction {
public:
    float Eval(float x) { return 0.0f; } // 기본적으로 0.0f만 반환함
};

// 자식 클래스 (다항식)
class SparsePolynomial : public MathFunction {
public:
    float Eval(float x) {
        // 지수와 계수를 가지고 다항식을 계산하는 로직...
        return 10.0f; // 임시 계산 결과
    }
};

int main() {
    SparsePolynomial p1; // 알맹이는 자식(다항식) 객체
    MathFunction* f = &p1; // 부모의 포인터 변수로 자식 객체를 가리킴 (C++에서 허용됨)
    
    std::cout << f->Eval(1.0f) << std::endl; 
    // 기대 결과: 다항식 계산 결과인 10.0f
    // 실제 결과: 0.0f (부모 함수가 호출됨)
    
    return 0;
}
```


포인터 `f`가 가리키는 실제 메모리 알맹이는 다항식(`p1`)임에도 불구하고, `virtual` 키워드가 없으면 컴파일러는 포인터의 껍데기 자료형(`MathFunction*`)만 보고 부모의 `Eval()` 함수를 정적으로 바인딩(Static Binding)해버립니다.

---

## 3. 해결사: `virtual` 키워드와 동적 바인딩 (Dynamic Binding)

**[KR]** 이 문제를 해결하기 위해 부모 클래스의 메서드 앞에 `virtual` 키워드를 붙여 가상함수로 선언합니다.

```cpp
class MathFunction {
public:
    // 가상함수로 선언!
    virtual float Eval(float x) { return 0.0f; }
};
```


부모 클래스에 `virtual`이 선언되어 있으면, 포인터로 `Eval()`을 호출할 때 껍데기 자료형만 보지 않고 메모리 끝까지 추적하여 **실제 연결된 자식 클래스의 함수를 찾아갑니다.** 이를 런타임에 호출할 함수가 결정된다고 하여 **동적 바인딩(Dynamic Binding)**이라고 부릅니다.

---

## 4. 다형성(Polymorphism)의 강력한 활용

**[KR]** 동적 바인딩이 가능해지면 파이썬과 같이 간결하고 유연한 통제가 가능해집니다. 서로 다른 자식 객체들을 부모 포인터 배열 하나로 묶어서 관리할 수 있는 것이 다형성(Polymorphism)의 핵심입니다.

```cpp
int main() {
    // 부모 포인터 배열 하나로 여러 자식 객체를 묶음
    MathFunction* functions[2];
    functions[0] = new SparsePolynomial();
    functions[1] = new SineFunction();

    // 파이썬처럼 간결하게 통제 가능
    for (int i = 0; i < 2; i++) {
        // 코드상으로는 똑같이 부모의 Eval을 외치지만, 
        // 런타임에는 동적 바인딩을 통해 각자 자식의 진짜 계산 함수를 알아서 찾아감
        std::cout << functions[i]->Eval(2.0f) << std::endl;
    }
    
    // 동적 할당 메모리 해제 로직 (생략)
    
    return 0;
}
```


<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Virtual Keyword-1" src="https://github.com/user-attachments/assets/95766a83-c4bc-4f3c-856c-e033b376a5a3" />
    <img width="1264" height="1635" alt="Virtual Keyword-2" src="https://github.com/user-attachments/assets/633aaf1e-0caf-4c02-a9d3-4cc034c70c9d" />
    <img width="1264" height="1635" alt="Virtual Keyword-3" src="https://github.com/user-attachments/assets/14b48a56-bd21-4533-a22d-68c584b5932f" />
  </div>
</details>
