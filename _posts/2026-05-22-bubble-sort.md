---
title: "1-3 Bubble Sort"
date: 2026-05-22 14:00:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, algorithm, bubble_sort]
---

## 1. 버블 정렬 (Bubble Sort)의 개념

**[KR]** 버블 정렬(Bubble Sort)은 0번과 1번, 1번과 2번, 2번과 3번... 이런 식으로 **인접한 두 원소를 비교하여 큰 값을 오른쪽으로 계속 밀어내는(보내는)** 매우 직관적인 정렬 알고리즘입니다. 

한 번의 사이클이 끝날 때마다 가장 큰 값이 맨 오른쪽 끝에 자리 잡게 되므로, 다음 탐색에서는 맨 끝 원소를 제외하고 비교를 진행하면 됩니다. 아래 코드에는 `isSwap`이라는 `bool` 변수를 사용하여, 한 사이클 동안 **단 한 번의 교환(Swap)도 일어나지 않았다면 이미 정렬이 완료된 것으로 판단하고 반복문을 탈출(`break`)하는 최적화 기법**이 적용되어 있습니다.

**[EN]** Bubble Sort is a highly intuitive sorting algorithm that compares adjacent elements (e.g., 0th and 1st, 1st and 2nd, 2nd and 3rd...) and **pushes the larger value to the far right**. 

At the end of each cycle, the largest value settles at the far right end, so the next iteration can exclude the last sorted element. The code below applies an optimization technique using a boolean variable named `isSwap`: **if no swaps occur during a full cycle, the algorithm assumes the array is completely sorted and exits the loop early using `break`.**

---

## 2. C++ 코드 구현 (Implementation)

```cpp
#include <iostream>
using namespace std;

// 인접한 두 원소를 비교하여 큰 값을 오른쪽으로 보낸다.
void BubbleSort(int arr[], int size) {
    bool isSwap;
    
    // 한 번 순회할 때마다 가장 큰 값이 맨 뒤로 고정되므로 탐색 범위를 하나씩 줄여나감
    for (int i = size - 1; i > 0; i--) {
        isSwap = false; // 매 사이클마다 교환 여부 초기화
        
        for (int j = 0; j < i; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
                isSwap = true; // 교환이 발생했음을 기록
            }
        }
        
        // 만약 이번 사이클에서 한 번도 자리 바꿈이 없었다면 이미 정렬 완료된 상태
        if (isSwap == false) {
            break;
        }
    }
}

int main() {
    int arr[] = {2, 5, 4, 9, 2, 7};
    int size = sizeof(arr) / sizeof(arr[0]);
    
    BubbleSort(arr, size);

    // 정렬된 결과 출력
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-3 Bubble Sort-1" src="https://github.com/user-attachments/assets/237b43fd-74d8-4eeb-8df7-171d44b0f63b" />
  </div>
</details>
