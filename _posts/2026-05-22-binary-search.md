---
title: "1-5 Binary Search"
date: 2026-05-22 14:10:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, algorithm, binary_search]
---

## 1. 이진 탐색 (Binary Search)의 개념

**[KR]** 이진 탐색(Binary Search)은 **미리 정렬된 배열**에서 특정한 값을 찾아내는 매우 효율적인 탐색 알고리즘입니다. 탐색 범위를 절반씩 줄여나가기 때문에 데이터가 많을수록 순차 탐색(Sequential Search)보다 압도적으로 빠른 속도를 자랑합니다. 

알고리즘의 동작 방식은 다음과 같습니다.
1. 배열의 시작점(`left`)과 끝점(`right`)을 기준으로 중간점(`mid`)을 계산합니다.
2. 중간점의 값과 찾고자 하는 값(`target`)을 비교합니다.
3. 타겟이 중간점의 값보다 크면 `left`를 `mid + 1`로 옮겨 오른쪽 절반을 탐색하고, 작으면 `right`를 `mid - 1`로 옮겨 왼쪽 절반을 탐색합니다.
4. 값을 찾거나, 탐색 범위가 뒤집혀(`left > right`) 더 이상 찾을 데이터가 없을 때까지 반복합니다.

**[EN]** Binary Search is a highly efficient algorithm for finding an item from a **previously sorted array**. It works by repeatedly dividing in half the portion of the list that could contain the item, making it overwhelmingly faster than sequential search, especially with large datasets.

The algorithm works as follows:
1. Calculate the midpoint (`mid`) based on the starting (`left`) and ending (`right`) points of the array.
2. Compare the value at the midpoint with the `target` value.
3. If the target is greater than the midpoint value, shift `left` to `mid + 1` to search the right half. If it's smaller, shift `right` to `mid - 1` to search the left half.
4. Repeat this process until the value is found or the search interval is empty (`left > right`).

---

## 2. C++ 코드 구현 (Implementation)

**[KR]** 필기한 내용을 바탕으로 구현한 C++ 이진 탐색 코드입니다. `while(true)` 무한 루프를 사용하여 조건을 만족했을 때 `break`로 빠져나오도록 직관적으로 구현되었습니다.

**[EN]** This is the C++ implementation of Binary Search based on the handwritten notes. It uses a `while(true)` loop, intuitively breaking out of the loop when the target is found or when it is determined that the target does not exist in the list.

```cpp
#include <iostream>
using namespace std;

// 함수 선언
void BinarySearch(int arr[], int n, int target);

int main() {
    // 0부터 9까지 정렬된 배열에서 3을 찾는 경우
    int arr[] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
    int n = sizeof(arr) / sizeof(arr[0]);

    BinarySearch(arr, n, 3);

    return 0;
}

// 이진 탐색 함수 구현
void BinarySearch(int arr[], int n, int target) {
    int left = 0;
    int right = n - 1;
    int mid = (left + right) / 2;

    while (true) {
        // 1. 원하는 값을 찾았을 때
        if (target == arr[mid]) {
            cout << "I got the number! " << arr[mid] << endl;
            break;
        }

        // 2. 타겟이 중간값보다 클 때 (오른쪽 절반 탐색)
        if (target > arr[mid]) {
            left = mid + 1;
            mid = (left + right) / 2;
        } 
        // 3. 타겟이 중간값보다 작을 때 (왼쪽 절반 탐색)
        else if (target < arr[mid]) {
            right = mid - 1;
            mid = (left + right) / 2;
        }

        // 4. 탐색 범위가 엇갈렸을 때 (데이터가 없음)
        if (left > right) {
            cout << "목록에 target이 없습니다." << endl;
            break;
        }
    }
}
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-5 Binary Search-1" src="https://github.com/user-attachments/assets/7674ffe1-35a8-4f30-8e3e-52062634a94a" />
  </div>
</details>
