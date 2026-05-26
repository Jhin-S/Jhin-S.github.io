---
title: "2-2 Display the First Three Rows"
date: 2026-05-26 16:43:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, head, tail]
---

## 1. 상위 3개 행 출력하기 (Display the First Three Rows)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 주어진 `employees` 데이터프레임에서 최상단에 있는 3개의 행(Row)만 추출하여 반환하는 문제입니다. 데이터 분석 실무에서 거대한 데이터셋의 형태를 처음 미리보기(Preview) 할 때 가장 자주 사용하는 메서드인 `head()`의 개념을 다룹니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. The task is to extract and return only the top three rows from the given `employees` DataFrame. It covers the `head()` method, which is the most frequently used function in data analysis practice to preview the structure of a massive dataset.

### Input & Output Example

**Input (`employees` DataFrame):**

| employee_id | name | department | salary |
| :--- | :--- | :--- | :--- |
| 3 | Bob | Operation | 48675 |
| 90 | Alice | Sales | 11096 |
| 9 | Tatiana | Engineering | 33805 |
| 60 | Annabelle | Information Technology | 37678 |
| 49 | Jonathan | Human Resources | 23793 |
| 43 | Khaled | Administration | 40454 |

**Output:**

| employee_id | name | department | salary |
| :--- | :--- | :--- | :--- |
| 3 | Bob | Operation | 48675 |
| 90 | Alice | Sales | 11096 |
| 9 | Tatiana | Engineering | 33805 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `head(n)` 메서드를 사용하면 데이터프레임의 **앞에서부터(최상단부터) n개의 행**을 손쉽게 가져올 수 있습니다. 만약 반대로 데이터의 **뒤에서부터(최하단부터) n개의 행**을 가져오고 싶다면 `tail(n)` 메서드를 사용하면 됩니다.

**[EN]** using the `head(n)` method in Pandas allows you to easily fetch the **first 'n' rows from the top** of the DataFrame. Conversely, if you want to fetch the **last 'n' rows from the bottom** of the data, you can use the `tail(n)` method.

```python
import pandas as pd

def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
    # 데이터프레임의 상위 3개 행을 반환합니다.
    # Returns the first 3 rows of the DataFrame.
    return employees.head(3)
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-2 Display the First Three Rows-1" src="https://github.com/user-attachments/assets/518b8c5a-0f93-474c-bd6b-cadee2b68ae0" />
  </div>
</details>
