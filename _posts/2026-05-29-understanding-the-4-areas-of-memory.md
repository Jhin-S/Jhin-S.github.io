---
title: "Understanding the 4 Areas of Memory"
date: 2026-05-29 17:24:00 +0900
categories: ["C++"]
tags: [cpp, memory_management, code_segment, data_segment, heap, stack]
---

## 메모리의 4대 영역 (The 4 Areas of Memory)

**[KR]** C++ 프로그램을 실행할 때, 컴퓨터(운영체제)는 프로그램이 원활하게 돌아갈 수 있도록 목적에 따라 메모리 공간을 크게 4가지 영역으로 나누어 관리합니다. 각 영역이 어떤 역할을 담당하는지 명확히 이해하는 것은 C++ 메모리 관리의 핵심입니다.

### 1. Code (코드) 영역
* **역할:** 개발자가 작성한 소스 코드가 저장되는 구역입니다.
* **특징:** C++ 코드가 컴파일을 거쳐 컴퓨터가 이해할 수 있는 기계어(0과 1)로 변환된 뒤 이 자리에 저장됩니다. CPU는 이 영역에 올려진 명령어를 읽고 한 줄씩 차례대로 실행합니다.
* **메모리 보호:** 프로그램이 실행되는 도중에 코드가 임의로 변경되면 치명적인 오류가 발생하므로, 이 영역은 철저히 읽기 전용(Read-Only)으로 보호됩니다.

### 2. Data (데이터) 영역 (= Static 영역)
* **역할:** 프로그램의 시작부터 종료 시점까지 절대 사라지지 않고 유지되는 영역입니다.
* **특징:** 프로그램이 처음 켜질 때 메모리에 고정적으로 할당되며, 프로그램이 완전히 꺼질 때만 함께 소멸합니다.
* **저장 예시:** 전역 변수(Global variables), `static` 변수, 그리고 함수들의 메모리 주소 등이 이 영역에 보관됩니다.

### 3. Heap (힙) 영역
* **역할:** 개발자가 필요할 때 마음대로 메모리를 빌리고 다 쓰면 반납할 수 있는 자유 메모리 공유 구역입니다. 이전에 학습한 `new` 연산자를 통해 런타임 중에 메모리를 동적 할당받는 공간이 바로 이 힙 영역이며, 사용 후에는 반드시 `delete`로 반납해야 메모리 누수를 막을 수 있습니다.

### 4. Stack (스택) 영역
* **역할:** 함수가 호출될 때 사용되었다가, 함수의 실행이 끝나면 자동으로 내부 데이터가 사라지는 임시 구역입니다. 일반적인 지역 변수(Local variables)나 함수의 매개변수들이 이곳에 저장됩니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Understanding the 4 Areas of Memory-1" src="https://github.com/user-attachments/assets/76d24b28-80a9-49aa-9cca-99cf5557eb26" />
  </div>
</details>
