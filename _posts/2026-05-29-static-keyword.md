---
title: "Static Keyword"
date: 2026-05-29 17:15:00 +0900
categories: ["C++"]
tags: [cpp, static, memory_management, oop, data_segment]
---

## 1. 정적(Static) 키워드의 의미와 메모리 할당

**[KR]** C++에서 변수나 함수에 `static` 키워드가 붙게 되면, 객체의 생성 여부와 무관하게 프로그램이 실행되는 순간부터 종료될 때까지 메모리에 고정적으로 존재하게 됩니다. 

* **동적(Dynamic) 변수/함수:** 일반적인 클래스 객체나 `new` 연산자로 할당된 메모리는 필요할 때 생성되고 사용이 끝나면 소멸합니다. 즉, 힙(Heap)이나 스택(Stack) 영역에 유동적으로 위치하며 수명 역시 유동적입니다.
* **정적(Static) 변수/함수:** 프로그램이 켜지는 순간 데이터(Data) 영역(또는 정적 영역)이라는 고정된 메모리에 자리를 잡고, 프로그램이 꺼질 때까지 소멸하지 않고 유지됩니다. 즉, 위치와 수명이 정적(Static)입니다.

---

## 2. 일반 멤버 함수 vs `static` 멤버 함수

**[KR]** 클래스 내부의 일반 `public` 함수와 `static` 함수는 **"객체를 생성해야만 쓸 수 있는가?"**와 **"`this` 포인터가 존재하는가?"**를 기준으로 명확히 구분됩니다.

* **일반 `public` 함수 (객체의 개인 비서):** 클래스의 설계도를 바탕으로 실제 객체(Instance)를 생성해야만 호출할 수 있습니다. 함수가 호출될 때 자신을 호출한 객체의 메모리 주소인 `this` 포인터를 물고 들어가기 때문에, 객체 개인의 멤버 변수에 자유롭게 접근할 수 있습니다.
* **`static` 함수 (클래스 본사의 공용 툴):** 객체를 단 하나도 생성하지 않아도 프로그램 시작부터 메모리에 존재하므로 클래스명과 범위 지정 연산자(`::`)를 통해 즉시 호출이 가능합니다. 특정 객체의 주소(`this` 포인터)를 가지지 않으므로 내부에서 객체의 인스턴스 변수를 직접 호출하면 에러가 발생합니다.

### 코드 비교 예시 (SparsePolynomial)
```cpp
class SparsePolynomial {
private:
    int length = 0; // 객체 개인의 변수

public:
    // 일반 public 함수
    void Print() {
        std::cout << this->length; // 어떤 객체가 호출했는지 알 수 있으므로 사용 가능
    }

    // static 함수
    static bool compareTerm(const Term& a, const Term& b) {
        // std::cout << length; // this 포인터가 없어 특정 객체의 length를 알 수 없으므로 에러 발생!
        return a.exp < b.exp;
    }
};

int main() {
    SparsePolynomial p1;
    p1.Print(); // 일반 함수는 객체(p1)가 있어야 호출 가능

    // static 함수는 객체 생성 없이 클래스명으로 바로 호출 가능
    bool result = SparsePolynomial::compareTerm(termA, termB); 
}
```


---

## 3. 클래스 내부에 `static`을 사용하는 이유

**[KR]** C 언어처럼 전역 함수로 외부에 빼두지 않고, 굳이 클래스 내부에 `static` 함수를 정의하는 이유는 크게 두 가지입니다.

1. **이름 충돌 방지 및 가독성 향상 (Namespace):** `SparsePolynomial::compareTerm()`과 같이 클래스 소속을 명시하여 호출하므로 다른 함수의 이름과 겹칠 위험이 없으며, 코드를 읽을 때 어떤 클래스와 연관된 기능인지 쉽게 파악할 수 있습니다.
2. **`private` 멤버 접근 권한 (보안):** `static` 함수는 `this` 포인터가 없어 인스턴스 변수를 직접 사용할 수는 없지만, 동일한 클래스 소속이므로 매개변수로 해당 클래스의 객체를 넘겨받았을 경우 그 객체의 `private` 변수까지 자유롭게 접근하여 열어볼 수 있는 강력한 권한을 가집니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Static Keyword-1" src="https://github.com/user-attachments/assets/202a6c6f-f461-4f48-ad5e-b6997f779ad5" />
    <img width="1264" height="1635" alt="Static Keyword-2" src="https://github.com/user-attachments/assets/dd987ccf-2779-419a-b20e-6e1ca6d8ecbc" />
    <img width="1264" height="1635" alt="Static Keyword-3" src="https://github.com/user-attachments/assets/fc1d9bdc-9a74-4473-8986-0e0c39c909a9" />
  </div>
</details>
