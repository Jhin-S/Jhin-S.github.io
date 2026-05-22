---
title: "2-1 Calculating the sum recursively"
date: 2026-05-22 15:45:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, algorithm, recursion]
---

## 1. 재귀(Recursion)를 이용한 배열의 합 계산

**[KR]** 재귀(Recursion)의 기초를 다지기 위해, 배열 내 모든 원소의 합을 재귀 함수로 구하는 코드를 작성해 보았습니다. 재귀 함수를 설계할 때는 무한 루프에 빠지지 않도록 **탈출 조건(Base Case)**을 설정하는 것이 가장 중요합니다. 

여기서는 배열의 탐색 크기(`n`)가 1이 되었을 때 첫 번째 원소(`arr[0]`)를 반환하도록 탈출 조건을 설정했습니다. 그 외의 경우에는 **'배열의 마지막 원소(`arr[n-1]`)'**와 **'나머지 원소들의 합을 구하는 재귀 호출(`RecurSum(arr, n-1)`)'**을 더하여 결과를 반환하도록 점화식을 구성했습니다.

**[EN]** To build a solid foundation in recursion, I wrote a code that calculates the sum of all elements in an array using a recursive function. When designing a recursive function, setting a **Base Case** is the most critical step to prevent infinite loops. 

In this implementation, the base case is established to return the first element (`arr[0]`) when the search size of the array (`n`) reaches 1. Otherwise, the recursive case (recurrence relation) is structured to return the sum of the **'last element of the array (`arr[n-1]`)'** and the **'recursive call for the sum of the remaining elements (`RecurSum(arr, n-1)`)'**.

---

## 2. C++ 코드 구현 (Implementation)

```cpp
#include <iostream>
using namespace std;

// 재귀 함수 선언 (Function Declaration)
int RecurSum(int arr[], int n);

int main() {
    // 1부터 10까지의 합을 구하는 예제 (1~10 Sum Example)
    int arr[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    int n = sizeof(arr) / sizeof(arr[0]);

    // 결과 출력 (Output the result)
    cout << "Sum: " << RecurSum(arr, n) << endl;

    return 0;
}

// 재귀 함수 구현 (Recursive Function Implementation)
int RecurSum(int arr[], int n) {
    // 탈출 조건 (Base Case): 원소가 1개 남았을 때 첫 번째 원소 반환
    if (n == 1) {
        return arr[0];
    }
    
    // 점화식 (Recursive Case): 현재 크기의 마지막 원소 + 나머지 크기의 배열 합
    return arr[n - 1] + RecurSum(arr, n - 1);
}
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-1 Calculating the sum recursively-1" src="https://github.com/user-attachments/assets/e70bc37f-453d-414b-b987-7ef33e5a15a1" />
  </div>
</details>
