---
title: "5-1 Reshape Data: Concatenate"
date: 2026-05-26 18:10:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, concatenate, reshape]
---

## 1. 데이터프레임 합치기 (Reshape Data: Concatenate)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 동일한 열(Column) 구조를 가진 두 개의 데이터프레임 `df1`과 `df2`를 세로(수직)로 이어 붙여 하나의 데이터프레임으로 병합하는 과정을 다룹니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of vertically concatenating two DataFrames, `df1` and `df2`, which have the same column structure, into a single unified DataFrame.

### Input & Output Example

**Input (`df1`):**

| student_id | name | age |
| :--- | :--- | :--- |
| 1 | Mason | 8 |
| 2 | Ava | 6 |
| 3 | Taylor | 15 |
| 4 | Georgia | 17 |

**Input (`df2`):**

| student_id | name | age |
| :--- | :--- | :--- |
| 5 | Leo | 7 |
| 6 | Alex | 7 |

**Output:**
(`df1` 아래에 `df2`가 그대로 이어 붙습니다.)

| student_id | name | age |
| :--- | :--- | :--- |
| 1 | Mason | 8 |
| 2 | Ava | 6 |
| 3 | Taylor | 15 |
| 4 | Georgia | 17 |
| 5 | Leo | 7 |
| 6 | Alex | 7 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `concat()` 함수를 사용하면 여러 개의 데이터프레임을 리스트 형태로 묶어서 한 번에 병합할 수 있습니다. 기본적으로 행(Row)을 기준으로 세로로 병합됩니다.

**[EN]** Using Pandas' `concat()` function, you can pass multiple DataFrames as a list to merge them all at once. By default, it concatenates them vertically along the rows.

```python
import pandas as pd

def concatenateTables(df1: pd.DataFrame, df2: pd.DataFrame) -> pd.DataFrame:
    # 두 데이터프레임을 리스트로 묶어 세로로 병합합니다.
    # Concatenate the two DataFrames vertically by passing them as a list.
    return pd.concat([df1, df2])
```

---

## 3. `pd.concat()` 세부 활용 팁 (Additional Tips for `concat()`)

**[KR]** 만약 데이터를 세로가 아닌 **가로(열 기준)**로 이어 붙이고 싶다면, `axis=1` 파라미터를 추가해주면 됩니다.
* **가로 병합 예시:** `pd.concat([df1, df2], axis=1)`

**[EN]** If you want to concatenate the data **horizontally (by columns)** instead of vertically, you can simply add the `axis=1` parameter.
* **Horizontal Concatenation Example:** `pd.concat([df1, df2], axis=1)`

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-1 Reshape Data_ Concatenate-1" src="https://github.com/user-attachments/assets/726a1476-87c9-4607-bf8e-53c0e8eafb0e" />
    <img width="1264" height="1635" alt="5-1 Reshape Data_ Concatenate-2" src="https://github.com/user-attachments/assets/388e6474-c231-40de-a331-3658c2b20849" />
  </div>
</details>
