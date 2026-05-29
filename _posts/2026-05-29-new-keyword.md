---
title: "new keyword"
date: 2026-05-29 17:30:00 +0900
categories: ["C++"]
tags: [cpp, memory_management, new, delete, dynamic_allocation, pointer]
---

## 1. `new` 연산자의 개념과 사용 이유

**[KR]** C++에서 `new` 연산자는 메모리를 동적으로 할당할 때 사용하는 핵심 키워드입니다. 

### 스택(Stack) vs 힙(Heap) 메모리
* **스택(Stack) 메모리:** `int a;`와 같은 일반적인 변수 선언은 스택에 저장되며, 함수가 끝나면 자동으로 사라지고 컴파일 시점에 그 크기가 결정되어야 합니다.
* **힙(Heap) 메모리:** `new` 키워드를 사용하면 프로그램 실행(런타임) 중에 힙 공간에서 메모리를 할당받습니다. 개발자가 원할 때 메모리를 생성하고 해제할 수 있습니다.

### 언제 `new`를 사용하는가?
1. 프로그램 실행 중에 크기가 유동적으로 변경되는 배열이 필요할 때 사용합니다.
2. 객체의 생명 주기(Lifetime)를 개발자가 직접 제어해야 할 때 사용합니다.
3. 메모리 용량이 매우 큰 데이터를 다룰 때 사용합니다.

### 메모리 해제의 중요성
**[KR]** `new`로 할당한 메모리는 사용이 끝난 후 반드시 `delete` 키워드를 사용하여 수동으로 해제해야 합니다. 이를 수행하지 않으면 메모리 누수(Memory Leak)가 발생하여 프로그램이 점점 느려지다가 결국 멈추거나 종료될 수 있습니다.

---

## 2. 단일 객체 및 변수 할당/해제

**[KR]** 단일 데이터 공간을 할당하고 해제하는 기본적인 방법입니다. 메모리 해제 후에는 포인터를 `nullptr`로 초기화하여 안전하게 비워두는 것이 좋습니다.

```cpp
#include <iostream>

int main() {
    // 1. 힙 메모리에 int형 공간을 만들고 주소값을 포인터에 저장
    int* ptr = new int;
    
    // 2. 값 대입 및 사용
    *ptr = 100;
    std::cout << "값: " << *ptr << ", 주소: " << ptr << std::endl;
    
    // 3. 할당과 초기화를 동시에 하는 방법
    int* ptr2 = new int(200);
    
    // 4. 사용이 끝난 메모리는 반드시 해제
    delete ptr;
    delete ptr2;
    
    // 5. 해제 후 포인터를 비워두는 것이 안전
    ptr = nullptr;
    ptr2 = nullptr;
    
    return 0;
}
```


---

## 3. 배열 할당 및 해제

**[KR]** 배열을 동적으로 할당할 때는 `new[]`를 사용하며, 이를 해제할 때는 반드시 `delete[]`를 사용하여 대괄호(`[]`) 짝을 맞춰주는 것이 핵심 규칙입니다. 컴파일 시점이 아닌 실행 중에 사용자 입력으로 배열의 크기를 결정할 수 있습니다.

```cpp
#include <iostream>

int main() {
    int size;
    std::cout << "배열의 크기를 입력하세요: ";
    std::cin >> size; // 실행 중에 크기가 결정됨

    // 1. 동적 배열 할당
    int* arr = new int[size];

    // 2. 배열 사용
    for (int i = 0; i < size; ++i) {
        arr[i] = (i + 1) * 10;
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;

    // 3. 동적 배열 해제 (반드시 delete 뒤에 []를 붙여야 함)
    delete[] arr;
    arr = nullptr;

    return 0;
}
```


---

## 4. 객체(Class) 생성 시 `new`의 동작

**[KR]** 클래스의 인스턴스를 `new` 연산자로 생성하게 되면, 힙 영역에 메모리가 할당됨과 동시에 해당 클래스의 **생성자(Constructor)**가 자동으로 호출됩니다. 반대로 할당된 객체를 `delete`로 해제할 때는 메모리가 반환되기 직전에 **소멸자(Destructor)**가 호출됩니다.

```cpp
#include <iostream>

class Monster {
public:
    Monster() { 
        std::cout << "몬스터 생성!" << std::endl; 
    }
    ~Monster() { 
        std::cout << "몬스터 소멸!" << std::endl; 
    }
};

int main() {
    // 생성자 호출됨
    Monster* myMonster = new Monster();
    
    // 소멸자 호출됨
    delete myMonster;
    
    return 0;
}
```


<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="new keyword-1" src="https://github.com/user-attachments/assets/4a503735-a085-42b6-9920-7943028b617d" />
    <img width="1264" height="1635" alt="new keyword-2" src="https://github.com/user-attachments/assets/700e4094-4867-42c8-a992-b6838b994431" />
    <img width="1264" height="1635" alt="new keyword-3" src="https://github.com/user-attachments/assets/d6ab65f3-1a20-482a-a40c-ba1795f84a7c" />
    <img width="1264" height="1635" alt="new keyword-4" src="https://github.com/user-attachments/assets/a9b0a8c2-374e-42c9-9b29-cd5e6adcfba5" />
  </div>
</details>
