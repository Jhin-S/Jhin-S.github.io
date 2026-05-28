---
title: "Operator Overloading"
date: 2026-05-28 15:45:00 +0900
categories: ["C++"]
tags: [cpp, oop, operator_overloading, mystring, class]
---

## 1. 연산자 오버로딩 (Operator Overloading) 개념

**[KR]** 연산자 오버로딩이란 커스텀 객체끼리 `+`, `-`, `==` 등의 연산자를 사용했을 때 해당 연산이 어떻게 동작할지 개발자가 직접 정의하는 기능입니다. 파이썬에서 두 리스트나 문자열에 `+` 연산자를 사용하면 하나의 리스트나 문자열로 이어붙여지듯이, C++에서도 클래스 내부에 `+`나 `==` 연산자의 구체적인 동작 방식을 정해줄 수 있습니다.

---

## 2. 문법 및 `MyString` 클래스 적용 (Syntax & Implementation)

**[KR]** C++에서는 일반적인 함수 이름 자리에 `operator` 키워드와 함께 재정의할 기호를 붙여서 정의합니다. 기본 구조는 `반환타입 operator연산자이름(const 클래스이름& other)` 형태를 가집니다. 만들어진 함수에 반환값을 설정하면 해당 연산자의 기능이 클래스에 맞게 덮어쓰기(Overloading) 됩니다.

### 2.1. `operator+` 구현 (문자열 이어붙이기)
**[KR]** 두 개의 `MyString` 객체를 더할 때, 두 문자열의 길이를 합친 크기만큼 동적 할당을 수행하여 데이터를 복사한 후 반환하는 코드입니다.

```cpp
MyString MyString::operator+(const MyString& other) {
    // 두 문자열의 길이를 합친 결과 크기 계산
    size_t result_size = this->str_size + other.str_size;
    // 널 문자('\0')를 포함할 공간(+1)만큼 동적 할당
    char* temp = new char[result_size + 1];

    // 첫 번째 문자열 복사
    for (size_t i = 0; i < this->str_size; i++) {
        temp[i] = this->str_data[i];
    }
    // 두 번째 문자열 이어붙이기
    for (size_t i = 0; i < other.str_size; i++) {
        temp[i + this->str_size] = other.str_data[i];
    }

    temp[result_size] = '\0';
    
    MyString result(temp);
    delete[] temp;
    
    return result;
}
```


### 2.2. `operator==` 구현 (문자열 비교)
**[KR]** 두 객체가 같은지 비교할 때, 먼저 길이를 확인하고 길이가 같다면 문자 하나씩 순회하며 일치 여부를 판별합니다.

```cpp
bool MyString::operator==(const MyString& other) {
    // 길이가 다르면 무조건 false 반환
    if (other.str_size != this->str_size) return false;
    
    // 길이가 같다면 요소 하나씩 비교
    for (size_t i = 0; i < this->str_size; i++) {
        if (*(this->str_data + i) != *(other.str_data + i)) {
            return false;
        }
    }
    
    return true;
}
```


---

## 3. 실제 사용 예시 (Usage in `main`)

**[KR]** 연산자 오버로딩을 구현해 두면, `main` 함수 내에서 직관적인 기호만으로 객체 간의 연산 및 비교가 가능해집니다.

```cpp
int main() {
    // 1. operator+ 사용 예시
    MyString str1("Hello, ");
    MyString str2("World!");
    MyString str3 = str1 + str2;
    
    str3.Print(); // 출력: Hello, World!

    // 2. operator== 사용 예시
    MyString str4("Apple");
    MyString str5("Apple");
    
    if (str4 == str5) {
        cout << "Equal" << endl; // 두 객체의 내용이 같으므로 출력됨
    }

    return 0;
}
```


<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="연산자 오버로딩-1" src="https://github.com/user-attachments/assets/5d9a8a83-d35c-408f-8683-05209ad9dcc3" />
    <img width="1264" height="1635" alt="연산자 오버로딩-2" src="https://github.com/user-attachments/assets/af4b7d65-bc69-472d-8ffe-7b0223466c75" />
    <img width="1264" height="1635" alt="연산자 오버로딩-3" src="https://github.com/user-attachments/assets/e127ed48-4ede-4d48-a65a-9840b5a52a4b" />
  </div>
</details>
