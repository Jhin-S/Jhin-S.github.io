---
title: "3-2 SparsePolynomial"
date: 2026-05-29 17:05:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, polynomial, sparse_polynomial, oop]
---

## 1. 희소 다항식 (Sparse Polynomial) 추상 자료형

**[KR]** 일반적인 배열로 다항식을 구현할 때, $1 + 2x^{10000000}$과 같은 다항식을 처리하려면 10000001 크기의 배열이 필요하여 극심한 메모리 낭비가 발생합니다. 이를 해결하기 위해 계수(Coefficient)와 지수(Exponent)를 하나의 쌍(`Term`)으로 묶고, 실제 존재하는 항만 동적 배열에 저장하는 **희소 다항식(Sparse Polynomial)** 자료구조를 구현하는 과제입니다. 

**[EN]** When implementing a polynomial using a standard array, a polynomial like $1 + 2x^{10000000}$ would require an array of size 10000001, leading to severe memory waste. To resolve this, this task implements a **Sparse Polynomial** data structure, which pairs the coefficient and exponent into a single `Term` and stores only the existing (non-zero) terms in a dynamic array.

---

## 2. 테스트 코드 (Problem: Test Code)

**[KR]** 구현한 `SparsePolynomial` 클래스가 정상적으로 작동하는지 검증하는 `main` 함수입니다. 항 추가(`NewTerm`), 다항식 출력(`Print`), 특정 $x$ 값에 대한 식 계산(`Eval`), 그리고 두 희소 다항식의 덧셈(`Add`) 기능이 모두 요구사항에 맞게 동작해야 합니다.

```cpp
#include "SparsePolynomial.h"
#include <iostream>

int main()
{
	using namespace std;

	// 희소 다항식
	// 1 + 2*x^10000000 을 앞의 방식으로는 10000000 + 1 크기의 배열이 필요하지만 
	// 여기서는 Term 2개로 가능

	SparsePolynomial p1; // max_degree는 기본값으로 설정

	// exp가 작은 항부터 추가한다고 가정
	p1.NewTerm(1.0f, 0);	// 1 * x^0 = 1
	p1.NewTerm(1.5f, 1);	// 1.5 * x^1
	p1.NewTerm(2.0f, 2);	// 2 * x^2

	p1.Print(); // 1 + 1.5*x^1 + 2*x^2

	cout << p1.Eval(0.0f) << endl; // 1 + 1.5*0 + 2*0^2 = 1
	cout << p1.Eval(1.0f) << endl; // 1 + 1.5*1 + 2*1^2 = 4.5
	cout << p1.Eval(2.0f) << endl; // 1 + 1.5*2 + 2*2^2 = 1 + 3 + 8 = 12

	cout << endl;

	// Add() Test1
	cout << "Add() Test" << endl;
	{
		SparsePolynomial p1; // max_degree는 기본값으로 설정

		// exp가 작은 항부터 추가한다고 가정
		p1.NewTerm(1.0f, 0);
		p1.NewTerm(1.5f, 1);
		p1.NewTerm(2.0f, 2);

		p1.Print(); // 1 + 1.5*x^1 + 2*x^2

		SparsePolynomial p2;

		// exp가 작은 항부터 추가한다고 가정
		p2.NewTerm(1.0f, 1);
		p2.NewTerm(3.0f, 2);
		p2.NewTerm(5.0f, 7);
		p2.NewTerm(2.0f, 11);

		p2.Print(); // 1*x^1 + 3*x^2 + 5*x^7 + 2*x^11

		cout << endl;

		SparsePolynomial psum = p1.Add(p2);
		psum.Print(); // 1 + 2.5*x^1 + 5*x^2 + 5*x^7 + 2*x^11

		cout << endl;
	}

	// Add() Test2
	cout << "Add() Test2" << endl;
	{
		SparsePolynomial p1; // max_degree는 기본값으로 설정

		// exp가 작은 항부터 추가한다고 가정
		p1.NewTerm(1.0f, 0);
		p1.NewTerm(1.5f, 1);
		p1.NewTerm(2.0f, 2);
		p1.NewTerm(5.0f, 7);
		p1.NewTerm(3.5f, 10);
		p1.NewTerm(5.5f, 20);
		p1.NewTerm(5.0f, 1000);

		p1.Print(); // 1 + 1.5*x^1 + 2*x^2 + 5*x^7 + 3.5*x^10 + 5.5*x^20 + 5*x^1000

		SparsePolynomial p2;

		// exp가 작은 항부터 추가한다고 가정
		p2.NewTerm(3.2f, 0);
		p2.NewTerm(1.0f, 1);
		p2.NewTerm(3.0f, 2);
		p2.NewTerm(2.0f, 11);

		p2.Print(); // 3.2 + 1*x^1 + 3*x^2 + 2*x^11

		cout << endl;

		SparsePolynomial psum = p1.Add(p2);
		psum.Print(); // 4.2 + 2.5*x^1 + 5*x^2 + 5*x^7 + 3.5*x^10 + 2*x^11 + 5.5*x^20 + 5*x^1000

		cout << endl;
	}

	return 0;
}
```

---

## 3. 헤더 파일 (SparsePolynomial.h)

**[KR]** 지수(`exp`)와 계수(`coef`)를 하나로 묶은 `Term` 구조체와, 이 `Term`들의 동적 배열을 멤버로 갖는 `SparsePolynomial` 클래스가 선언되어 있습니다.

```cpp
#pragma once

struct Term {
	int exp;
	float coef;

	Term(float coef, int exp) {
		this->coef = coef;
		this->exp = exp;
	}
	Term() {}
};

class SparsePolynomial {
private:
	size_t default_size = 100;
	size_t length = 0;
	Term* terms;
public:
	SparsePolynomial();

	SparsePolynomial(const SparsePolynomial& other);

	~SparsePolynomial();

	static bool compareTerm(const Term& a, const Term& b);

	void NewTerm(float coef, int exp);

	void Print() const;

	float Eval(float x) const;

	int Exist(int target) const;

	SparsePolynomial Add(const SparsePolynomial& other);
};
```

---

## 4. 소스 코드 구현 (SparsePolynomial.cpp)

**[KR]** 선언된 기능들을 구체적으로 구현한 해답 소스 코드입니다. 배열의 용량이 가득 찰 경우 동적으로 크기를 늘려주는 배열 리사이징 로직과, 덧셈 시 같은 지수를 가진 항의 계수를 병합하는 로직이 핵심입니다.

```cpp
# include <iostream>
# include <algorithm>
# include <cmath>
# include "SparsePolynomial.h"

SparsePolynomial::SparsePolynomial() {
	this->terms = new Term[this->default_size];
};

SparsePolynomial::SparsePolynomial(const SparsePolynomial& other) {
	this->length = other.length;
	this->default_size = other.default_size;

	this->terms = new Term[this->default_size];
	for (size_t i = 0; i < this->length; i++) {
		this->terms[i] = other.terms[i];
	}
}

SparsePolynomial::~SparsePolynomial() {
	if (this->terms != nullptr) delete[] terms;
	terms = nullptr;
}

bool SparsePolynomial::compareTerm(const Term& a, const Term& b) {
	return a.exp < b.exp;
}

void SparsePolynomial::NewTerm(float coef, int exp) {
	if (this->length == this->default_size) {
		this->default_size += 100;
		Term* new_terms = new Term[this->default_size];
		for (size_t i = 0; i < this->length; i++) {
			new_terms[i] = this->terms[i];
		}
		delete[] this->terms;
		this->terms = new_terms;
	}
	terms[this->length] = Term(coef, exp);
	this->length += 1;
	std::sort(this->terms, this->terms + length, compareTerm);
}

void SparsePolynomial::Print() const {
	if (this->length == 0) {
		std::cout << "" << '\n';
	}
	else {
		for (size_t i = 0; i < this->length; i++) {
			if (this->terms[i].exp == 0) std::cout << this->terms[i].coef;
			else if (this->terms[i].exp == 1) std::cout << this->terms[i].coef << "x";
			else std::cout << this->terms[i].coef << "x^" << this->terms[i].exp;
			if (i != this->length - 1) std::cout << " + ";
		}
	}
}

float SparsePolynomial::Eval(float x) const {
	float result = 0.0f;
	for (size_t i = 0; i < this->length; i++) {
		result += this->terms[i].coef * std::pow(x, this->terms[i].exp);
	}
	return result;
}

int SparsePolynomial::Exist(int target) const {
	if (this->length == 0) return -1;

	for (size_t i = 0; i < this->length; i++) {
		if (this->terms[i].exp == target) return i;
	}

	return -1;
}

SparsePolynomial SparsePolynomial::Add(const SparsePolynomial& other) {
	SparsePolynomial new_polynomial;
	for (size_t i = 0; i < this->length; i++) {
		if (other.Exist(this->terms[i].exp) != -1) {
			new_polynomial.NewTerm(this->terms[i].coef + other.terms[other.Exist(this->terms[i].exp)].coef, this->terms[i].exp);
		}
		else {
			new_polynomial.NewTerm(this->terms[i].coef, this->terms[i].exp);
		}
	}
	for (size_t j = 0; j < other.length; j++) {
		if (this->Exist(other.terms[j].exp) == -1) new_polynomial.NewTerm(other.terms[j].coef, other.terms[j].exp);
		else continue;
	}
	return new_polynomial;

}
```
