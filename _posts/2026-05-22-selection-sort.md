---
title: "1-2 Selection Sort"
date: 2026-05-22 12:30:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, algorithm, selection_sort, exchange_sort]
---

## 1. 3개의 데이터 정렬해보기 (Hardcoding)

**[KR]** 정렬 알고리즘의 기초를 다지기 위해, 가장 단순한 형태인 배열 내 3개의 요소를 정렬하는 것부터 고민해 보았습니다. 배열의 요소들을 직접 비교하고 위치를 바꾸는(Swap) 논리를 세우면서, 정렬이 완료되었는지 확인하는 `CheckSorted` 함수도 함께 구현했습니다.

**[EN]** To build a solid foundation in sorting algorithms, I started by thinking about the simplest form: sorting 3 elements in an array. While establishing the logic to directly compare and swap elements, I also implemented a `CheckSorted` function to verify if the sorting is complete.

```cpp
#include <iostream>
using namespace std;

// 배열이 정렬되었는지 확인하는 함수
bool CheckSorted(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        if (arr[i] > arr[i + 1]) {
            return false;
        }
    }
    return true;
}

int main() {
    int arr[3] = {9, 8, 1}; // 예시 데이터
    int size = sizeof(arr) / sizeof(arr[0]);

    // TODO: 3개의 데이터 직접 정렬해보기
    if (arr[0] > arr[1]) swap(arr[0], arr[1]);
    if (arr[1] > arr[2]) swap(arr[1], arr[2]);
    if (arr[0] > arr[1]) swap(arr[0], arr[1]);

    cout << "Sorted: " << CheckSorted(arr, size) << endl;

    return 0;
}
```

---

## 2. 교환 정렬 (Exchange Sort)의 우연한 발견

**[KR]** 앞선 아이디어를 바탕으로 반복문(for)을 사용해 배열 전체를 정렬하는 코드를 작성해 보았습니다. 처음에는 이것이 '선택 정렬'이라고 생각하고 구현했지만, 코드를 자세히 분석해 보니 **조건을 만족할 때마다 즉시 데이터를 교환(Swap)하는 '교환 정렬(Exchange Sort)'** 방식이었습니다. 이 방식은 동작은 하지만, 매번 불필요한 `swap`이 발생하여 성능 면에서 아쉬움이 남습니다.

**[EN]** Based on the previous idea, I wrote a code using a `for` loop to sort the entire array. Initially, I implemented it thinking it was 'Selection Sort'. However, upon closer analysis, it turned out to be an **'Exchange Sort' method, where data is swapped immediately whenever a condition is met.** While this method works, it involves unnecessary swaps every time, leaving room for performance improvement.

```cpp
#include <iostream>
using namespace std;

// 구현하고 보니 교환 정렬(Exchange Sort)이었던 코드
void ExchangeSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        for (int j = i + 1; j < size; j++) {
            // 비교 후 즉시 위치를 바꿈 (매번 Swap 발생)
            if (arr[i] > arr[j]) {
                swap(arr[i], arr[j]);
            }
        }
    }
}

int main() {
    int arr[] = {5, 1, 3, 9, 10, 7, 7, 9, 1, 8};
    int size = sizeof(arr) / sizeof(arr[0]);

    ExchangeSort(arr, size);

    for (int i = 0; i < size; i++) {
        cout << arr[i] << " " << flush;
    }
    return 0;
}
```

---

## 3. 선택 정렬 (Selection Sort)의 완성

**[KR]** 교환 정렬의 단점을 보완하기 위해 원래 목표였던 **선택 정렬(Selection Sort)**을 최종적으로 완성했습니다. 선택 정렬의 핵심은 매번 자리를 바꾸는 것이 아니라, **'최솟값(minimum)의 인덱스를 기억'**해두었다가 안쪽 반복문이 완전히 끝난 후 단 한 번만 `swap`을 수행하는 것입니다. 이렇게 최솟값의 위치만 찾아서 마지막에 교환해 줌으로써, 메모리 쓰기(Swap) 작업을 최소화하여 훨씬 효율적인 정렬을 구현할 수 있었습니다.

**[EN]** To overcome the drawbacks of Exchange Sort, I finally completed the originally intended **'Selection Sort'**. The core of Selection Sort is not swapping every time, but **'remembering the index of the minimum value'** and performing a single `swap` only after the inner loop finishes completely. By finding the position of the minimum value and swapping it at the end, I could minimize memory write operations (swaps) and implement a much more efficient sort.

```cpp
#include <iostream>
using namespace std;

// minimum을 기억한다! 진짜 선택 정렬 (Selection Sort)
void SelectionSort(int arr[], int size) {
    int minimum;
    for (int i = 0; i < size - 1; i++) {
        minimum = i; // 현재 위치를 최솟값 인덱스로 초기화
        for (int j = i + 1; j < size; j++) {
            // 더 작은 값을 찾으면 인덱스만 갱신
            if (arr[j] < arr[minimum]) {
                minimum = j;
            }
        }
        // 탐색이 끝난 후, 최솟값과 현재 위치를 딱 한 번만 교환
        swap(arr[i], arr[minimum]);
    }
}

int main() {
    int arr[] = {5, 1, 3, 9, 10, 7, 7, 1, 8};
    int size = sizeof(arr) / sizeof(arr[0]);

    SelectionSort(arr, size);

    for (int i = 0; i < size; i++) {
        cout << arr[i] << " " << flush;
    }
    return 0;
}
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">Jhin의 원본 손필기 노트</summary>
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-2 Selection Sort-1" src="https://github.com/user-attachments/assets/cbc9a5fe-1cb2-43e4-8e26-5276a4adc1cc" />
    <img width="1264" height="1635" alt="1-2 Selection Sort-2" src="https://github.com/user-attachments/assets/f53058ff-6dc6-41e3-a8fb-cb77feba2fda" />
    <img width="1264" height="1635" alt="1-2 Selection Sort-3" src="https://github.com/user-attachments/assets/6ec42fcc-2691-4d01-ab67-58a7201db8fa" />
  </div>
</details>
