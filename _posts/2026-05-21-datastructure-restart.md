---
title: "[DataStructure] 1-1 Swap"
date: 2026-05-21 20:20:00 +0900
categories: [DataStructure]
tags: [datastructure, cpp, HongLab]
---

## I'm diving back into Data Structures with C++

I have been studying Data Structures in C++, but I realized I need a stronger foundation. So, I am starting fresh today.

### Pointer & Reference Swap 

```cpp
#include <iostream>

using namespace std;

// 1. 포인터를 이용한 Swap
void MySwapPtr(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// 2. 참조자(Reference)를 이용한 Swap
void MySwapRef(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}

int main() {
    // Swap 테스트
    int a = 3;
    int b = 2;
    cout << a << " " << b << endl; // 3 2 출력
    
    MySwapPtr(&a, &b);
    cout << a << " " << b << endl; // 2 3 출력
    
    MySwapRef(a, b);
    cout << a << " " << b << endl; // 3 2 출력 (다시 원래대로)

    cout << "------------------" << endl;

    // 정렬 (Sorting) 테스트
    int arr[] = {3, 2};
    cout << arr[0] << " " << arr[1] << endl; // 3 2 출력
    
    // 앞의 숫자가 더 크면 자리 바꾸기 (오름차순 정렬의 기본)
    if (arr[0] > arr[1]) {
        MySwapRef(arr[0], arr[1]);
    }
    
    cout << arr[0] << " " << arr[1] << endl; // 2 3 출력 (정렬 완료)

    return 0;
}
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: flex; align-items: flex-start; gap: 10px; margin-top: 15px;">
    <img alt="필기 1" src="https://github.com/user-attachments/assets/a1a2eb9c-8ef4-48c0-951b-9f21191610fe" style="flex: 1; min-width: 0; border-radius: 6px;" />
    <img alt="필기 2" src="https://github.com/user-attachments/assets/7490c361-c6aa-4e7a-a6ba-c1597959681d" style="flex: 1; min-width: 0; border-radius: 6px;" />
  </div>
</details>
