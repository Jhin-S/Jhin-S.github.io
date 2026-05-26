---
title: "4-5 Change Data Type"
date: 2026-05-26 17:55:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, astype, datatype]
---

## 1. 데이터 타입 변경하기 (Change Data Type)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. `students` 데이터프레임의 `grade` 열에 있는 데이터 타입을 실수형(Float)에서 정수형(Integer)으로 변환하는 과정을 다룹니다. 데이터 분석 시 메모리 최적화나 연산의 정확도를 높이기 위해 자주 수행하는 데이터 형변환 작업입니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of converting the data type of the `grade` column in the `students` DataFrame from floating-point (Float) to integer (Integer). This type casting operation is frequently performed during data analysis to optimize memory usage and improve computational accuracy.

### Input & Output Example

**Input (`students` DataFrame):**

| student_id | name | age | grade |
| :--- | :--- | :--- | :--- |
| 1 | Ava | 6 | 73.0 |
| 2 | Kobe | 15 | 87.0 |

**Output:**
(`grade` 열의 73.0, 87.0이 정수 73, 87로 변환됩니다.)

| student_id | name | age | grade |
| :--- | :--- | :--- | :--- |
| 1 | Ava | 6 | 73 |
| 2 | Kobe | 15 | 87 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `astype()` 메서드를 사용하면 데이터프레임 내 특정 열의 데이터 타입을 원하는 형태로 쉽게 바꿀 수 있습니다. 파라미터로 변환하고자 하는 타입(예: `int`, `float`, `str` 등)을 전달하면 해당 타입으로 캐스팅된 새로운 시리즈(Series)가 반환되며, 이를 다시 기존 열에 할당하여 덮어씁니다.

**[EN]** By using the `astype()` method in Pandas, you can easily change the data type of a specific column in a DataFrame to the desired format. Passing the target type (e.g., `int`, `float`, `str`, etc.) as a parameter returns a new Series cast to that type, which is then reassigned to overwrite the existing column.

```python
import pandas as pd

def changeDatatype(students: pd.DataFrame) -> pd.DataFrame:
    # 'grade' 열의 데이터 타입을 정수형(int)으로 변환한 뒤 덮어씁니다.
    # Convert the data type of the 'grade' column to integer (int) and overwrite it.
    students['grade'] = students['grade'].astype(int)
    
    return students
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-5 Change Data Type-1" src="https://github.com/user-attachments/assets/541d57d7-1fd2-47e2-9712-21dcd7c2f571" />
  </div>
</details>
