---
title: "4-2 Drop Missing Data"
date: 2026-05-26 17:40:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, dropna, missing_data]
---

## 1. 결측치 제거하기 (Drop Missing Data)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 주어진 `students` 데이터프레임에서 `name` 열의 값이 결측치(None, NaN 등)인 행(Row)을 완전히 제거하는 과정을 다룹니다. 데이터 전처리 과정에서 필수적인 결측치 정제 작업을 의미합니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of completely removing rows from the `students` DataFrame where the `name` column has missing values (like None, NaN). This represents an essential missing data cleansing task in data preprocessing.

### Input & Output Example

**Input (`students` DataFrame):**

| student_id | name | age |
| :--- | :--- | :--- |
| 32 | Piper | 5 |
| 217 | None | 19 |
| 779 | Georgia | 20 |
| 849 | Willow | 14 |

**Output:**
(`name`이 `None`인 217번 학생의 데이터가 삭제됩니다.)

| student_id | name | age |
| :--- | :--- | :--- |
| 32 | Piper | 5 |
| 779 | Georgia | 20 |
| 849 | Willow | 14 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `dropna()` 메서드를 사용하면 데이터프레임 내에 결측치가 포함된 행을 통째로 삭제할 수 있습니다. 특정 열에 있는 결측치만 확인하여 삭제하고 싶을 때는 `subset` 파라미터에 대상 열의 이름을 리스트 형태로 전달합니다.

**[EN]** You can delete entire rows containing missing values in a DataFrame using Pandas' `dropna()` method. If you want to check and drop missing values based only on specific columns, you pass the target column names as a list to the `subset` parameter.

```python
import pandas as pd

def dropMissingData(students: pd.DataFrame) -> pd.DataFrame:
    # 'name' 열을 기준으로 결측치(NA)가 있는 행을 찾아 통째로 삭제합니다.
    # Drops rows completely if there are missing values (NA) in the 'name' column.
    return students.dropna(subset=['name'])
```

---

## 3. `dropna()` 세부 옵션 (Details of `dropna()`)

**[KR]** `dropna`는 **Drop NA (Not Available)**의 줄임말입니다.
* **`subset` 옵션을 사용할 경우:** 명시된 열(`name`)에서 결측치가 발생한 경우에만 해당 행을 삭제합니다.
* **`subset` 옵션을 생략할 경우:** `student_id`, `name`, `age` 중 **단 하나라도** 빈칸(결측치)이 있는 행은 전부 삭제됩니다.

**[EN]** `dropna` stands for **Drop NA (Not Available)**.
* **When using the `subset` option:** It drops the row only if a missing value occurs in the specified column(s) (e.g., `name`).
* **When omitting the `subset` option:** Any row with a blank (missing value) in **any** of the columns (`student_id`, `name`, `age`) will be entirely deleted.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-2 Drop Missing Data-1" src="https://github.com/user-attachments/assets/e8795998-7fca-46c0-a265-0ab0859de5ea" />
  </div>
</details>
