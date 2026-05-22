---
title: "2-3 Recursive Binary Search"
date: 2026-05-22 16:04:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, algorithm, binary_search, recursion]
---

## 1. 재귀를 이용한 이진 탐색 (Recursive Binary Search)

**[KR]** 앞서 `while` 반복문을 사용하여 구현했던 이진 탐색(Binary Search)을 이번에는 **재귀 함수(Recursion)**를 이용하여 구현해 보았습니다. 

재귀적 이진 탐색의 핵심은 탐색 범위를 반으로 줄일 때마다, 새로운 시작점(`left`)과 끝점(`right`)을 매개변수로 삼아 자기 자신을 다시 호출하는 것입니다. 반복문을 사용할 때보다 변수 갱신이 직관적이며, 수학적인 분할 정복(Divide and Conquer)의 논리를 코드로 매우 깔끔하게 표현할 수 있습니다.

**[EN]** In this section, we implemented Binary Search using **Recursion** instead of the previously used `while` loop. 

The core of recursive binary search is that every time the search range is halved, the function calls itself again using the updated starting (`left`) and ending (`right`) points as parameters. Compared to using a loop, variable updating is more intuitive, and the mathematical logic of Divide and Conquer can be expressed very cleanly in the code.

---

## 2. C++ 코드 구현 (Implementation)

**[KR]** 필기에 작성된 논리를 바탕으로 복원한 C++ 코드입니다. 타겟을 찾지 못해 `left`가 `right`보다 커지는 순간(탐색 범위가 엇갈리는 순간)에는 `-1`을 반환하도록 탈출 조건(Base Case)을 설정했습니다.

**[EN]** This is the C++ code restored based on the logic written in the notes. The base case is set to return `-1` the moment `left` becomes greater than `right` (when the search range crosses over), indicating that the target cannot be found.

```cpp
#include <iostream>
using namespace std;

// 재귀적 이진 탐색 함수 (Recursive Binary Search Function)
int RecursiveBinarySearch(int arr[], int left, int right, int x) {
    // 탈출 조건: 탐색 범위가 유효할 때만 진행
    if (left <= right) {
        int middle = (left + right) / 2;

        // 1. 타겟 값을 찾은 경우 (Base Case)
        if (x == arr[middle]) {
            return middle; // 인덱스 반환
        } 
        // 2. 타겟이 중간값보다 작은 경우 -> 왼쪽 절반 탐색
        else if (x < arr[middle]) {
            return RecursiveBinarySearch(arr, left, middle - 1, x);
        } 
        // 3. 타겟이 중간값보다 큰 경우 -> 오른쪽 절반 탐색
        else {
            return RecursiveBinarySearch(arr, middle + 1, right, x);
        }
    }
    
    // 데이터를 찾지 못하고 탐색 범위가 끝난 경우
    return -1; 
}

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    int n = sizeof(arr) / sizeof(arr[0]);

    // 7을 찾는 테스트 (배열, 시작 인덱스, 끝 인덱스, 타겟)
    int targetIndex = RecursiveBinarySearch(arr, 0, n - 1, 7);
    
    if (targetIndex != -1) {
        cout << "Target found at index: " << targetIndex << endl;
    } else {
        cout << "Target not found." << endl;
    }

    return 0;
}
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-3 Recursive Binary Search-1" src="https://github.com/user-attachments/assets/1b3e38a9-6bcf-4771-a82c-ae8db931bfc9" />
  </div>
</details>
