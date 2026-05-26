---
title: "3-1 Select Data"
date: 2026-05-26 16:57:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, loc]
---

## 1. 데이터 선택하기 (Select Data)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 주어진 `students` 데이터프레임에서 `student_id`가 101인 학생의 `name`과 `age` 열만 선택하여 반환하는 문제입니다. 특정 조건을 만족하는 행(Row)을 찾고, 그 중에서도 원하는 열(Column)만 추출하는 방법을 다룹니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. The task is to select and return only the `name` and `age` columns for the student whose `student_id` is 101 from the given `students` DataFrame. It covers how to find rows that meet a specific condition and extract only the desired columns from them.

### Input & Output Example

**Input (`students` DataFrame):**

| student_id | name | age |
| :--- | :--- | :--- |
| 101 | Ulysses | 13 |
| 53 | William | 10 |
| 128 | Henry | 6 |
| 3 | Henry | 11 |

**Output:**

| name | age |
| :--- | :--- |
| Ulysses | 13 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** 조건에 맞는 데이터를 추출하는 두 가지 방법을 소개합니다. 첫 번째는 `.loc`을 사용하여 행 조건과 열 조건을 한 번에 지정하는 방법이며, 두 번째는 불리언 인덱싱(Boolean Indexing)으로 행을 먼저 필터링한 뒤 원하는 열을 선택하는 방법입니다.

**[EN]** Here are two methods to extract data that meets the conditions. The first method uses `.loc` to specify both row and column conditions at once, while the second method uses Boolean Indexing to filter the rows first and then selects the desired columns.

```python
import pandas as pd

# 방법 1 (Method 1): .loc[행 조건, 열 조건] 사용
def selectData(students: pd.DataFrame) -> pd.DataFrame:
    return students.loc[students['student_id'] == 101, ['name', 'age']]

# 방법 2 (Method 2): 불리언 인덱싱 후 열 선택
def selectData_v2(students: pd.DataFrame) -> pd.DataFrame:
    filtered_students = students[students['student_id'] == 101]
    return filtered_students[['name', 'age']]
```

---

## 3. DataFrame `[]` 사용 규칙 (Indexing Rules)

**[KR]** DataFrame 객체 뒤에 대괄호 `[]`를 사용할 때의 기본적인 동작 규칙입니다.
* **열(Column) 추출:** 대괄호 안에 문자열(열 이름)이나 리스트를 넣으면 열을 추출합니다.
  * `students['name']`
  * `students[['name', 'age']]`
* **조건식을 이용한 행(Row) 추출:** 대괄호 안에 조건식을 넣으면 조건을 만족하는 행을 추출합니다.
  * `students[students['age'] > 15]`
* **슬라이싱을 이용한 행(Row) 추출:** 대괄호 안에 숫자 범위를 넣으면 해당 인덱스의 행을 추출합니다.
  * `students[0:2]` (0번 인덱스부터 1번 인덱스까지, 총 2줄)

**[EN]** These are the basic rules for using brackets `[]` after a DataFrame object.
* **Extracting Columns:** Passing a string (column name) or a list of strings extracts columns.
  * `students['name']`
  * `students[['name', 'age']]`
* **Extracting Rows by Condition:** Passing a conditional expression extracts rows that meet the condition.
  * `students[students['age'] > 15]`
* **Extracting Rows by Slicing:** Passing a numerical range extracts rows based on their indices.
  * `students[0:2]` (extracts from index 0 to 1, a total of 2 rows)

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-1 Select Data-1" src="https://github.com/user-attachments/assets/f583155c-9ff7-4c56-bcbd-2365c7e8d4dc" />
    <img width="1264" height="1635" alt="3-1 Select Data-2" src="https://github.com/user-attachments/assets/79f341b1-4e2f-424c-8d39-790d55587bea" />
  </div>
</details>
