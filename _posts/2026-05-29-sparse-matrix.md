---
title: "3-3 SparseMatrix"
date: 2026-05-29 19:45:00 +0900
categories: ["DataStructure"]
tags: [datastructure, cpp, sparse_matrix, matrix, array, oop]
---

## 1. 희소 행렬 (Sparse Matrix) 추상 자료형

**[KR]** 희소 행렬(Sparse Matrix)은 행렬의 요소 중 대부분이 0으로 이루어진 행렬을 의미합니다. 이를 일반적인 2차원 배열로 구현할 경우 심각한 메모리 낭비가 발생합니다. 이를 해결하기 위해 행(Row), 열(Column), 값(Value)을 하나의 구조체(`Element`)로 묶고, 0이 아닌 유효한 데이터만 동적 배열에 저장하는 방식으로 자료구조를 최적화합니다. 일반적으로 동적 배열의 0번째 인덱스(`matrix[0]`)에는 전체 행렬의 행 개수, 열 개수, 그리고 0이 아닌 값의 총 개수(Non-zero term)를 저장하여 메타 데이터로 활용합니다.

---

## 2. 테스트 코드 (Problem: Test Code)

**[KR]** 구현한 `SparseMatrix` 클래스가 정상적으로 작동하는지 검증하는 `main` 함수입니다. 무작위 순서로 데이터를 삽입(`SetValue`)해도 내부적으로 올바르게 정렬되어야 하며, 행과 열이 뒤바뀐 전치 행렬(`Transpose`)을 성공적으로 반환하고 출력(`Print`)해야 합니다.

```cpp
#include <iostream>
#include "SparseMatrix.h"

int main()
{
	using namespace std;

	SparseMatrix m1(4, 6, 6); // 4 by 6 matrix, Non-zero term 6개

	// 정렬되지 않은 순서로 추가
	m1.SetValue(2, 3, 5.0f);
	m1.SetValue(0, 5, 2.0f);
	m1.SetValue(1, 1, 1.0f);
	m1.SetValue(0, 0, 1.0f);
	m1.SetValue(0, 3, 7.0f);
	m1.SetValue(1, 2, 3.0f);

	// m1.SetValue(2, 3, 4.0f); // <- 덮어쓰는 경우

	m1.Print();

	cout << endl;

	SparseMatrix tr = m1.Transpose(); // 전치행렬

	tr.Print();

	return 0;
}
```


---

## 3. 헤더 파일 (SparseMatrix.h)

**[KR]** 행렬의 각 요소를 표현하는 `Element` 구조체와, 이를 동적 배열로 관리하는 `SparseMatrix` 클래스의 선언부입니다. 

```cpp
#pragma once

struct Element {
	int column;
	int row;
	float value;

	Element(int row, int column, float value) {
		this->row = row;
		this->column = column;
		this->value = value;
	}
	Element() {}

};

class SparseMatrix {
private:
	size_t default_size = 100;
	size_t index = 0;
	Element* matrix;

public:
	SparseMatrix();
	~SparseMatrix();
	SparseMatrix(const SparseMatrix& other);
	SparseMatrix(int row, int column, float value);
	static bool compareMatrix(const Element& a, const Element& b);
	int Exist(int row, int column);
	void SetValue(int row, int column, float value);
	void Print();
	SparseMatrix Transpose();
};
```


---

## 4. 소스 코드 구현 (SparseMatrix.cpp)

**[KR]** `SparseMatrix` 클래스의 세부 기능이 구현된 소스 코드입니다. `SetValue` 호출 시 기존에 데이터가 존재하면 값을 덮어쓰고, 존재하지 않으면 새로운 값을 동적 배열에 추가한 뒤 행(row)과 열(column)을 기준으로 재정렬(`std::sort`)합니다. `Transpose` 함수는 행과 열의 크기를 반대로 뒤집은 새로운 행렬을 생성하고 데이터를 재배치하여 반환합니다.

```cpp
#include <iostream>
#include "SparseMatrix.h"
#include <algorithm>

SparseMatrix::SparseMatrix() {
	this->matrix = new Element[this->default_size];
	this->index += 1;
}

SparseMatrix::SparseMatrix(int row, int column, float value) {
	this->index += 1;
	this->matrix = new Element[this->default_size];
	this->matrix[0].row = row;
	this->matrix[0].column = column;
	this->matrix[0].value = value;
}

SparseMatrix::~SparseMatrix() {
	if (this->matrix != nullptr){
		delete[] this->matrix;
		this->matrix = nullptr;
	}
}

SparseMatrix::SparseMatrix(const SparseMatrix& other) {
	this->default_size = other.default_size;
	this->index = other.index;

	this->matrix = new Element[this->default_size];

	for (size_t i = 0; i < index; i++) {
		this->matrix[i] = other.matrix[i];
	}
}

bool SparseMatrix::compareMatrix(const Element& a, const Element& b) {
	if (a.row == b.row) return a.column < b.column;
	return a.row < b.row;
}

int SparseMatrix::Exist(int row, int column) {
	for (size_t i = 1; i < index; i++) {
		if ((this->matrix[i].column == column) && (this->matrix[i].row == row)) return i;
	}
	return -1;
}

void SparseMatrix::SetValue(int row, int column, float value) {
	if (this->Exist(row, column) == -1){
		if (this->index == this->default_size) {
			this->default_size += 100;
			Element* new_matrix = new Element[this->default_size];
			for (size_t i = 0; i < this->index; i++) {
				new_matrix[i] = this->matrix[i];
			}
			delete[] this->matrix;
			this->matrix = new_matrix;
		}
		this->matrix[index] = Element(row, column, value);
		std::sort(this->matrix+1, this->matrix + index + 1, this->compareMatrix);
		this->index += 1;
	}
	else {
		this->matrix[this->Exist(row, column)].value = value;
	}
}

void SparseMatrix::Print() {
	for (size_t i = 1; i < this->index; i++) {
		std::cout << "(" << this->matrix[i].row << ", " << this->matrix[i].column << ", " << this->matrix[i].value << ")" << "\n";
	}
}

SparseMatrix SparseMatrix::Transpose() {
	SparseMatrix temp_matrix(this->matrix[0].column, this->matrix[0].row, this->matrix[0].value);

	for (size_t i = 1; i < this->index; i++) {
		temp_matrix.SetValue(this->matrix[i].column, this->matrix[i].row, this->matrix[i].value);
	}
	return temp_matrix;
}
```
