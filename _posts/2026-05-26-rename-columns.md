---
title: "4-4 Rename Columns"
date: 2026-05-26 17:50:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, rename, column]
---

## 1. 열 이름 변경하기 (Rename Columns)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 주어진 `students` 데이터프레임의 기존 열(Column) 이름들을 더 명확하고 이해하기 쉬운 이름으로 변경하여 반환하는 과정을 다룹니다. 데이터 분석 시 데이터의 가독성을 높이기 위해 필수적으로 거치는 작업입니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of renaming the existing columns of the given `students` DataFrame to more clear and descriptive names. This is an essential step in data analysis to improve the readability of the data.

### Input & Output Example

**Input (`students` DataFrame):**

| id | first | last | age |
| :--- | :--- | :--- | :--- |
| 1 | Mason | King | 6 |
| 2 | Ava | Wright | 7 |
| 3 | Taylor | Hall | 16 |
| 4 | Georgia | Thompson | 18 |
| 5 | Thomas | Moore | 15 |

**Output:**

| student_id | first_name | last_name | age_in_years |
| :--- | :--- | :--- | :--- |
| 1 | Mason | King | 6 |
| 2 | Ava | Wright | 7 |
| 3 | Taylor | Hall | 16 |
| 4 | Georgia | Thompson | 18 |
| 5 | Thomas | Moore | 15 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `rename()` 메서드를 사용하면 데이터프레임의 열 이름을 변경할 수 있습니다. `columns` 파라미터에 딕셔너리(Dictionary) 형태로 변경할 이름들을 매핑하여 전달합니다.

**[EN]** You can change the column names of a DataFrame using Pandas' `rename()` method. Pass a dictionary to the `columns` parameter mapping the old names to the new ones.

```python
import pandas as pd

def renameColumns(students: pd.DataFrame) -> pd.DataFrame:
    # 딕셔너리 매핑을 통해 열 이름을 {'기존 이름': '새 이름'} 형태로 변경합니다.
    # Rename columns using dictionary mapping: {'old_name': 'new_name'}.
    students = students.rename(
        columns={
            'id': 'student_id',
            'first': 'first_name',
            'last': 'last_name',
            'age': 'age_in_years'
        }
    )
    
    return students
```

---

## 3. `rename()` 메서드 세부 설명 (Details of `rename()`)

**[KR]** `rename(columns={...})` 구조의 핵심은 딕셔너리 매핑입니다.
* **`{'old': 'new'}` 구조:** 변경하고 싶은 기존 열의 이름을 Key로, 새롭게 지정할 이름을 Value로 작성합니다.
* **선택적 변경:** 딕셔너리에 명시된 열의 이름만 변경되며, 딕셔너리에 포함되지 않은 나머지 열들은 원래 이름을 그대로 유지합니다.

**[EN]** The core of the `rename(columns={...})` structure is dictionary mapping.
* **`{'old': 'new'}` structure:** Set the existing column name you want to change as the Key, and the new name as the Value.
* **Selective renaming:** Only the columns specified in the dictionary are renamed. Any columns not included in the dictionary will retain their original names.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-4 Rename Columns-1" src="https://github.com/user-attachments/assets/8c7b515e-a60d-47b0-b981-209d3fbb256c" />
    <img width="1264" height="1635" alt="4-4 Rename Columns-2" src="https://github.com/user-attachments/assets/2b9145df-b622-4a0b-8251-a71c988e83d2" />
  </div>
</details>
