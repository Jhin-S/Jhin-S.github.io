---
title: "4-3 Modify Columns"
date: 2026-05-26 17:45:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, modify, column]
---

## 1. 열 데이터 수정하기 (Modify Columns)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. `employees` 데이터프레임에 이미 존재하는 `salary` 열의 모든 값을 2배로 수정하여 반환하는 과정을 다룹니다. 기존에 존재하는 열의 데이터를 덮어쓰기(Overwrite)하는 방법을 확인하는 문제입니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of modifying all values in the existing `salary` column of the `employees` DataFrame by multiplying them by 2 and returning the result. This problem demonstrates how to overwrite data in an already existing column.

### Input & Output Example

**Input (`employees` DataFrame):**

| name | salary |
| :--- | :--- |
| Jack | 19666 |
| Piper | 74754 |
| Mia | 62509 |
| Ulysses | 54866 |

**Output:**
(`salary` 열의 모든 값이 2배로 수정됩니다.)

| name | salary |
| :--- | :--- |
| Jack | 39332 |
| Piper | 149508 |
| Mia | 125018 |
| Ulysses | 109732 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** 데이터프레임에서 이미 존재하는 열의 이름을 딕셔너리의 키(Key)처럼 지정하고 새로운 데이터를 할당하면, 새로운 열이 추가되는 것이 아니라 **기존 열의 데이터가 덮어씌워집니다**. 벡터화 연산(Vectorized Operation)을 통해 `salary` 열 전체에 2를 곱한 값을 다시 `salary` 열에 할당하여 값을 갱신합니다.

**[EN]** In a DataFrame, if you specify an existing column name like a Dictionary key and assign new data to it, it does not add a new column but rather **overwrites the data in the existing column**. Through vectorized operation, the entire `salary` column is multiplied by 2, and the result is reassigned to the `salary` column to update its values.

```python
import pandas as pd

def modifySalaryColumn(employees: pd.DataFrame) -> pd.DataFrame:
    # 이미 존재하는 'salary' 열에 접근하여 2를 곱한 뒤 다시 덮어씁니다.
    # Access the existing 'salary' column, multiply by 2, and overwrite it.
    employees['salary'] = employees['salary'] * 2
    
    return employees
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-3 Modify Columns-1" src="https://github.com/user-attachments/assets/e97fd260-8f76-4607-9cd7-55733db14b74" />
  </div>
</details>
