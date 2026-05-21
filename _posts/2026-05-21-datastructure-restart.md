---
title: "[DataStructure] 1-1 sort"
date: 2026-05-21 20:20:00 +0900
categories: [DataStructure]
tags: [datastructure, cpp, HongLab]
---

## I'm diving back into Data Structures with C++

I have been studying Data Structures in C++, but I realized I need a stronger foundation. So, I am starting fresh today.

<div style="display: flex; justify-content: space-between; gap: 10px; margin-bottom: 20px;">
  <img src="[https://github.com/user-attachments/assets/714b55e1-f315-408a-86a8-9cd7049f36fc](https://github.com/user-attachments/assets/714b55e1-f315-408a-86a8-9cd7049f36fc)" alt="필기 1" style="width: 48%; border-radius: 8px;">
  <img src="[https://github.com/user-attachments/assets/de16ab0d-cf16-4beb-81f7-ddc44f664938](https://github.com/user-attachments/assets/de16ab0d-cf16-4beb-81f7-ddc44f664938)" alt="필기 2" style="width: 48%; border-radius: 8px;">
</div>

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
