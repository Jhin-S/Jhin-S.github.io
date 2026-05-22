---
title: "1-4 Insertion Sort"
date: 2026-05-22 14:05:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, algorithm, insertion_sort]
---

## 1. 삽입 정렬 (Insertion Sort)의 개념과 실행 과정

**[KR]** 삽입 정렬(Insertion Sort)은 두 번째 원소부터 시작하여, 그 앞의 이미 정렬된 부분 배열과 비교하며 자신이 들어갈 알맞은 위치를 찾아 '삽입'하는 정렬 알고리즘입니다. 새로운 카드를 손에 쥐고 기존의 정렬된 카드 사이의 올바른 자리에 끼워 넣는 과정과 같습니다.

**[EN]** Insertion Sort is a sorting algorithm that begins with the second element and compares it against the already sorted sub-array before it, finding its correct position to 'insert' itself. It is similar to sorting a hand of playing cards, where you pick up a new card and insert it into the correct spot among the previously sorted cards.

### Execution Example
필기에서 다룬 배열의 정렬 과정을 단계별로 살펴보면 다음과 같습니다.
(Let's look at the step-by-step sorting process of the array covered in the notes.)

* **Initial:** `[4, 3, 2, 10, 12, 15, 6]`
* **Step 1:** `3`을 `4` 앞으로 삽입 → `[3, 4, 2, 10, 12, 15, 6]`
* **Step 2:** `2`를 `3, 4` 앞으로 삽입 → `[2, 3, 4, 10, 12, 15, 6]`
* **Step 3~5:** `10, 12, 15`는 이미 앞의 원소보다 크므로 제자리 유지
* **Step 6:** `6`을 `10, 12, 15` 앞으로 삽입 → `[2, 3, 4, 6, 10, 12, 15]`

---

## 2. C++ 코드 구현 (Implementation)

**[KR]** 데이터를 한 칸씩 뒤로 미루면서 빈 공간을 만들고, 최종 위치에 값을 집어넣습니다. 이때 특정 조건(나보다 작은 값을 만나거나, 배열의 끝에 도달함)을 만족하면 즉시 탐색을 중단해야 하므로 `for`문보다는 `while`문이 훨씬 자연스럽고 효율적입니다.

**[EN]** The algorithm shifts elements one position to the right to make room and then inserts the value into its final position. Since the search must stop immediately when a certain condition is met (encountering a smaller value or reaching the start of the array), using a `while` loop is much more natural and efficient than a `for` loop.

```cpp
#include <iostream>
using namespace std;

void InsertionSort(int arr[], int size) {
    // 두 번째 원소(인덱스 1)부터 시작
    for (int i = 1; i < size; i++) {
        int temp = arr[i]; // 현재 삽입할 타겟 값을 임시 저장
        int j = i - 1;     // 타겟의 바로 앞 인덱스부터 탐색 시작

        // 타겟 값(temp)보다 큰 원소들을 오른쪽으로 한 칸씩 미룸
        while (j >= 0 && arr[j] > temp) {
            arr[j + 1] = arr[j];
            j--;
        }
        
        arr[j + 1] = temp; 
        
        // while 문이 끝났다는건 나보다 작은 녀석을 만났거나
        // 더 이상 앞이 없다는 뜻
        // 조건에 따라 멈추는 반복문은 while 이 자연스럽다.
    }
}

int main() {
    int arr[] = {4, 3, 2, 10, 12, 15, 6};
    int size = sizeof(arr) / sizeof(arr[0]);

    InsertionSort(arr, size);

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
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-4 Insertion Sort-1" src="https://github.com/user-attachments/assets/360da35e-5707-4c50-863c-9f752f2aa234" />
  </div>
</details>
