---
title: "2-2 Fibonacci"
date: 2026-05-22 16:00:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, algorithm, recursion, fibonacci, iteration]
---

## 1. 피보나치 수열 (Fibonacci Sequence)

**[KR]** 피보나치 수열은 앞의 두 수를 더해 다음 수를 만들어내는 대표적인 수열입니다 (0, 1, 1, 2, 3, 5, 8...). 이번 필기에서는 피보나치 수열을 구하는 두 가지 방식, 즉 **재귀 함수(Recursion)**를 이용한 방법과 **반복문(Iteration)**을 이용한 방법을 비교하여 구현했습니다.

* **재귀(Recursion):** 코드가 수학적 점화식과 거의 일치하여 매우 직관적이고 간결하지만, 동일한 값을 여러 번 반복해서 계산해야 하므로 숫자가 커질수록 성능이 크게 저하됩니다.
* **반복문(Iteration):** 변수들을 활용해 이전 두 값을 기억하고 더해나가는 방식입니다. 코드는 약간 길어지지만, 중복 계산이 없기 때문에 성능과 메모리 효율 측면에서 훨씬 뛰어납니다.

**[EN]** The Fibonacci sequence is a famous series of numbers where each number is the sum of the two preceding ones (0, 1, 1, 2, 3, 5, 8...). In these notes, I implemented two different approaches to generate the Fibonacci sequence: using **Recursion** and using **Iteration (For loop)**.

* **Recursion:** The code is highly intuitive and concise, almost mirroring the mathematical recurrence relation. However, it suffers from severe performance degradation as the number grows due to massive redundant calculations.
* **Iteration:** This approach uses variables to remember and add the previous two values. While the code is slightly longer, it is significantly more efficient in terms of performance and memory since it avoids redundant computations.

---

## 2. C++ 코드 구현 (Implementation)

```cpp
#include <iostream>
using namespace std;

// 1. 재귀(Recursion)를 이용한 피보나치 수열
int RecurFibonacci(int n) {
    // 탈출 조건 (Base Case): 0번째와 1번째 항은 자기 자신을 반환
    if (n <= 1) {
        return n;
    }
    // 점화식 (Recursive Case): 앞의 두 항을 더함
    return RecurFibonacci(n - 1) + RecurFibonacci(n - 2);
}

// 2. 반복문(Iteration)을 이용한 피보나치 수열
int ForFibonacci(int n) {
    int n1 = 0; // f(n-2)
    int n2 = 1; // f(n-1)
    int result; // f(n)

    if (n == 0) return 0;
    else if (n == 1) return 1;
    else {
        // 2번째 항부터 n번째 항까지 반복하며 갱신
        for (int i = 2; i <= n; i++) {
            result = n1 + n2;
            n1 = n2;       // 한 칸씩 앞으로 이동
            n2 = result;   // 한 칸씩 앞으로 이동
        }
        return result;
    }
}

int main() {
    // 10번째 피보나치 수 구하기 (0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55)
    cout << "RecurFibonacci(10): " << RecurFibonacci(10) << endl;
    cout << "ForFibonacci(10): " << ForFibonacci(10) << endl;

    return 0;
}
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-2 Fibonacci-1" src="https://github.com/user-attachments/assets/0ba6b0cd-dec6-4d39-8468-a67a9ba70252" />
  </div>
</details>
