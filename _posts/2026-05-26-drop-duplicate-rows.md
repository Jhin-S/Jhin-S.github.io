---
title: "4-1 Drop Duplicate Rows"
date: 2026-05-26 17:25:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, duplicates]
---

## 1. 중복 행 제거하기 (Drop Duplicate Rows)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 고객 정보가 담긴 `customers` 데이터프레임에서 `email` 열의 값이 중복되는 행(Row)들을 찾아 제거하는 문제입니다. 데이터 전처리 과정에서 필수적으로 거치게 되는 중복 데이터 정제(Data Cleansing) 작업을 다룹니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. The task is to find and remove duplicate rows based on the `email` column in the `customers` DataFrame. It covers data cleansing for duplicate data, which is an essential step in the data preprocessing pipeline.

### Input & Output Example

**Input (`customers` DataFrame):**

| customer_id | name | email |
| :--- | :--- | :--- |
| 1 | Ella | emily@example.com |
| 2 | David | michael@example.com |
| 3 | Zachary | sarah@example.com |
| 4 | Alice | john@example.com |
| 5 | Finn | john@example.com |
| 6 | Violet | alice@example.com |

**Output:**
(`john@example.com` 이메일이 중복되므로, 첫 번째로 등장한 Alice의 데이터만 남기고 Finn의 데이터는 삭제됩니다.)

| customer_id | name | email |
| :--- | :--- | :--- |
| 1 | Ella | emily@example.com |
| 2 | David | michael@example.com |
| 3 | Zachary | sarah@example.com |
| 4 | Alice | john@example.com |
| 6 | Violet | alice@example.com |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `drop_duplicates()` 메서드를 사용하면 데이터프레임 내의 중복된 행을 쉽게 제거할 수 있습니다. 특정 열을 기준으로 중복을 판별하려면 `subset` 파라미터를 지정해주면 됩니다.

**[EN]** You can easily remove duplicate rows in a DataFrame using Pandas' `drop_duplicates()` method. To identify duplicates based on a specific column, you specify the `subset` parameter.

```python
import pandas as pd

def dropDuplicateEmails(customers: pd.DataFrame) -> pd.DataFrame:
    # 'email' 열을 기준으로 중복된 행을 찾아 제거합니다.
    # Drops duplicate rows based on the 'email' column.
    return customers.drop_duplicates(subset=['email'])
```

---

## 3. 중복 제거 세부 옵션 (Advanced Options for `drop_duplicates`)

**[KR]** `drop_duplicates()` 메서드는 다양한 옵션을 통해 중복 제거 방식을 세밀하게 조정할 수 있습니다.

1. **`subset` 옵션 생략 시:**
   만약 `subset` 옵션을 쓰지 않으면, 데이터프레임의 **모든 열(customer_id, name, email)의 값이 토씨 하나 틀리지 않고 100% 동일해야만** 중복으로 판정하여 삭제합니다.

2. **`keep` 옵션 (어떤 중복 데이터를 남길지 결정):**
   * `keep='first'` (기본값): 중복된 값 중 **첫 번째** 항목만 남기고 나머지를 삭제합니다.
   * `keep='last'`: 중복된 값 중 **마지막** 항목만 남기고 나머지를 삭제합니다.
   * `keep=False`: 중복된 값이 있는 **모든 행을 완전히 삭제**합니다.

**[EN]** The `drop_duplicates()` method provides various options to fine-tune how duplicates are removed.

1. **Omitting the `subset` option:**
   If the `subset` option is not used, a row is considered a duplicate and dropped **only if all columns (`customer_id`, `name`, `email`) are 100% identical**.

2. **The `keep` option (Determines which duplicates to keep):**
   * `keep='first'` (Default): Keeps the **first** occurrence and drops the rest.
   * `keep='last'`: Keeps the **last** occurrence and drops the rest.
   * `keep=False`: **Drops all rows** that have duplicate values, leaving none behind.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-1 Drop Duplicate Rows-1" src="https://github.com/user-attachments/assets/45405d5e-0285-4d71-bdef-465b869f4751" />
  </div>
</details>
