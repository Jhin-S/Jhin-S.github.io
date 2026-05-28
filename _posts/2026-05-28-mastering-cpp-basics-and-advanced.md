---
title: "클래스 제작으로 이해하는 C++의 기초와 심화 [Mastering C++ Basics and Advanced Concepts by Building a Class]"
date: 2026-05-28 15:30:00 +0900
categories: ["C++"]
tags: [cpp, oop, pointer, dynamic_allocation, reference, string_class]
---

잠시간의 기간 동안 C++을 다루지 않고 Python만 다루다보니 C++의 개념이 친숙치 않게 되었습니다.
내가 적은 코드임에도 불구하고 편안히 보이지 않게 되어서 직접 작성했던 DataStructure의 MyString 부분을 리뷰하며 개념을 상기시켜보았습니다.

## 1. 기본 문법과 제어 (The Basics)

**[KR]** 파이썬의 기초 문법과 대응되지만, 모든 변수의 '타입(Type)'을 명시해야 한다는 엄격함과 더불어, 내장 클래스와 원시 자료형의 차이가 극명하게 나타납니다. 직접 구현한 `MyString` 클래스의 코드를 통해 이를 확인할 수 있습니다.

### 원시 자료형(Primitive Types)과 사용자 정의 자료형
**[KR]** C++의 기본 자료형인 `int`, `float`, `double`, `char`, `bool` 등은 객체가 아니므로 내장된 메서드를 가지지 않습니다. 파이썬에서는 `a = "hi hay"`라고 선언한 뒤 `a.split()`처럼 바로 문자열 메서드를 쓸 수 있습니다. 하지만 C++에서 `"hi hay"`는 단순한 문자 조각 배열일 뿐이며, 내장된 문자열 조작 함수가 존재하지 않습니다. 따라서 이 데이터에 다양한 기능(메서드)을 부여하기 위해 `MyString`과 같은 클래스(껍데기)를 직접 씌워 사용자 정의 자료형을 만들어야 합니다.

### 스코프와 네임스페이스 (Scope Resolution Operator)
```cpp
// MyString.cpp 코드 발췌
MyString::MyString(const char* init) {
    // ...
}
```
**[KR]** `::` 기호는 범위 지정 연산자(Scope Resolution Operator)로, "~에 소속된"이라는 의미를 가집니다. `MyString::MyString`은 현재 구현하고자 하는 생성자 함수가 `MyString` 클래스에 소속되어 있음을 컴파일러에 명시하는 역할을 합니다.

### 값에 의한 호출 vs 참조에 의한 호출 (Call by Value vs Reference)
```cpp
// 참조(Reference) 예시 코드
int a = 10;
cout << &a << endl; // 16진수 메모리 주소 출력
int& ref = a;       // ref는 a의 별명이다.
ref = 20;           // 별명을 바꾸니 a도 20이 된다.
```
**[KR]** C++에서 `&` 기호는 쓰이는 위치에 따라 의미가 완전히 달라집니다. 이미 만들어진 변수 앞에 붙이면(`&a`) 해당 변수의 메모리 주소를 반환하지만, 자료형 뒤에 선언하면(`int& ref = a`) 해당 변수의 '별명(참조)'이 됩니다. 함수에 인자를 전달할 때 값을 그대로 복사하는 값에 의한 호출(Call by value)을 사용하면 메모리 복사 연산 때문에 속도가 느려집니다. 이를 방지하기 위해 참조를 활용하며, `const MyString& other`처럼 `const` 키워드를 함께 사용하여 함수 내부에서 원본 데이터가 의도치 않게 수정되는 인간의 실수를 방지합니다.

---

## 2. 메모리와 포인터 (Memory & Pointers) - ⭐ C++의 핵심

**[KR]** 파이썬의 가비지 컬렉터(Garbage Collector)가 자동으로 처리해주던 메모리 관리를 C++에서는 개발자가 포인터와 동적 할당을 통해 직접 제어해야 합니다.

### 포인터와 널 문자
```cpp
// 생성자 코드 구현부 발췌
while (true) {
    if (*(init + str_size) != '\0') {
        str_size++;
    } else {
        break;
    }
}
```
**[KR]** 초기화되지 않은 포인터가 쓰레기값을 가리키는 위험을 막기 위해, 빈 주소를 의미하는 `nullptr`로 초기화하는 것이 권장됩니다. 문자열의 길이를 파악할 때는 포인터 연산(`*(init + str_size)`)을 활용하여 메모리를 순차적으로 탐색하며, 문자열의 끝을 의미하는 널 문자(`'\0'`)가 나올 때까지 직접 글자 수를 셉니다. 생성자의 매개변수인 `const char* init`이 가리키는 것은 결국 메모리에 올라간 첫 번째 문자열 글자의 주소 단 하나입니다.

### 동적 할당 (Dynamic Allocation)
```cpp
// 동적 할당 코드 발췌
str_data = new char[str_size + 1];
for (size_t i = 0; i < str_size + 1; i++) {
    *(str_data + i) = *(init + i);
}
```
**[KR]** 문자열의 정확한 길이를 알아낸 후에는 `new char[str_size + 1]`를 호출하여 동적 할당(Dynamic Allocation)을 수행합니다. 이때 `+ 1`을 더하는 이유는 문자열의 끝을 알리는 널 문자(`\0`)가 들어갈 공간을 확보하기 위함입니다.

---

## 3. 객체지향 프로그래밍 (OOP)

**[KR]** 파이썬의 클래스와 개념적 결은 같지만, 접근 권한 제어(`Access Specifiers`)가 시스템적으로 훨씬 엄격하게 강제됩니다.

### Struct vs Class 컨벤션
**[KR]** 모든 멤버 변수와 함수를 `public`으로 설정하면 파이썬의 클래스나 C++의 `struct`와 완전히 동일하게 동작합니다. 하지만 C++ 컨벤션(Convention) 상, 기능 없이 데이터 값만 묶어둘 때는 `struct`를 사용하고, 내부 기능을 구현할 때는 `class`를 사용하기로 약속되어 있습니다. 클래스는 기본적으로 정보 은닉을 위해 속성값을 `private`에 몰아넣는 캡슐화 원칙을 따릅니다.

### 접근 제어자와 상속 (private vs protected)
```cpp
// 상속 및 접근 제어자 테스트 코드 발췌
class MyString {
private:
    size_t str_size;
protected:
    char* str_data;
};

// MyString을 상속받은 자식 클래스
class EmailString : public MyString {
    void CheckEmail() {
        str_size = 10;         // 에러! private 속성이기 때문
        str_data[0] = 'a';     // 가능! protected 속성은 자식 클래스 접근 허용
    }
};
```
**[KR]** `private`와 `protected` 모두 클래스 외부에서의 접근을 차단하지만, 상속 관계에서 큰 차이를 보입니다. `private`으로 선언된 `str_size`는 이를 상속받은 자식 클래스(`EmailString`) 내부에서도 접근할 수 없어 컴파일 에러가 발생합니다. 반면 `protected`로 선언된 `str_data`는 자식 클래스에게 접근을 허용하여 `str_data[0] = 'a'`와 같이 데이터를 직접 수정할 수 있습니다.

### 헤더 파일의 중복 포함 방지
```cpp
// MyString.h 상단
#pragma once
```
**[KR]** 클래스의 구조를 정의하는 헤더 파일 상단에는 `#pragma once`를 선언해야 합니다. 이는 다수의 소스 파일에서 동일한 헤더를 여러 번 `include` 할 때 발생하는 중복 포함(컴파일 에러)을 방지하는 역할을 합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="공부내용-1" src="https://github.com/user-attachments/assets/0d58e9c6-5c07-41af-8f81-1e60304ba197" />
    <img width="1264" height="1635" alt="공부내용-2" src="https://github.com/user-attachments/assets/58e8100a-4466-4038-923d-ab428c489d08" />
    <img width="1264" height="1635" alt="공부내용-3" src="https://github.com/user-attachments/assets/ee5ff539-b97b-4252-ae20-56011a621a8d" />
    <img width="1264" height="1635" alt="공부내용-4" src="https://github.com/user-attachments/assets/0630f71e-90e7-48cb-8126-78781ec6fe4c" />
    <img width="1264" height="1635" alt="공부내용-5" src="https://github.com/user-attachments/assets/247dd4fd-8ce2-47ad-a31c-158c9e52b7c3" />
    <img width="1264" height="1635" alt="공부내용-6" src="https://github.com/user-attachments/assets/1efa9373-ba97-4613-b603-c59d20b8600e" />
  </div>
</details>
