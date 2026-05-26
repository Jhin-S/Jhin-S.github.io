---
title: "3-2 Create a New Column"
date: 2026-05-26 17:15:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, column, insert]
---

## 1. 새로운 열 만들기 (Create a New Column)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 주어진 `employees` 데이터프레임의 기존 열인 `salary` 값을 활용하여, 기존 급여의 2배 값을 가지는 새로운 `bonus` 열을 추가하는 문제입니다. Pandas에서 파생 변수(기존 데이터를 바탕으로 만들어진 새로운 열)를 생성하는 가장 기본적인 방법을 다룹니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. The task is to add a new `bonus` column to the given `employees` DataFrame, where the values are twice the existing `salary` values. It covers the most fundamental method of creating derived variables (new columns generated based on existing data) in Pandas.

### Input & Output Example

**Input (`employees` DataFrame):**

| name | salary |
| :--- | :--- |
| Piper | 4548 |
| Grace | 28150 |
| Georgia | 1103 |
| Willow | 6593 |
| Finn | 74576 |
| Thomas | 24433 |

**Output:**

| name | salary | bonus |
| :--- | :--- | :--- |
| Piper | 4548 | 9096 |
| Grace | 28150 | 56300 |
| Georgia | 1103 | 2206 |
| Willow | 6593 | 13186 |
| Finn | 74576 | 149152 |
| Thomas | 24433 | 48866 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** 데이터프레임에 새로운 열을 추가할 때는 딕셔너리(Dictionary)에 새로운 키(Key)와 값(Value)을 할당하는 방식과 동일하게 작성하면 됩니다. 기존 `salary` 열에 2를 곱하면 벡터화 연산(Vectorized Operation)을 통해 모든 행에 동일하게 수식이 적용됩니다.

**[EN]** Adding a new column to a DataFrame is similar to assigning a new key and value to a Dictionary. When you multiply the existing `salary` column by 2, the formula is applied to all rows simultaneously through vectorized operation.

```python
import pandas as pd

def createBonusColumn(employees: pd.DataFrame) -> pd.DataFrame:
    # 기존 salary 열의 값에 2를 곱하여 새로운 bonus 열에 할당합니다.
    # Assign twice the value of the salary column to the new bonus column.
    employees['bonus'] = employees['salary'] * 2
    
    return employees
```

---

## 3. 다양한 열 추가 방법 (Advanced Column Insertion)

**[KR]** 기본 연산 외에도 데이터프레임에 새로운 열을 추가하는 다양한 방법이 있습니다.

1. **데이터를 리스트(List)로 넣는 경우:**
   행의 개수와 리스트의 길이가 일치해야 합니다.
   ```python
   bonus_list = [5000, 1000, 3000, 4000, 2000, 1500]
   employees['bonus'] = bonus_list
   ```

2. **원하는 위치(인덱스)에 열을 삽입하고 싶을 때 (`df.insert`):**
   새로운 열은 기본적으로 맨 오른쪽에 추가되지만, `insert()` 메서드를 사용하면 원하는 위치에 열을 끼워 넣을 수 있습니다.
   ```python
   # 0번(첫 번째) 위치에 'grade'라는 열을 만들고 전부 'A'로 채워 넣습니다.
   # 기존 열들은 오른쪽으로 한 칸씩 밀려납니다.
   employees.insert(0, 'grade', 'A')
   ```

**[EN]** In addition to basic arithmetic operations, there are various ways to add new columns to a DataFrame.

1. **Adding data as a List:**
   The length of the list must match the number of rows in the DataFrame.
   ```python
   bonus_list = [5000, 1000, 3000, 4000, 2000, 1500]
   employees['bonus'] = bonus_list
   ```

2. **Inserting a column at a specific position (`df.insert`):**
   New columns are added to the far right by default, but you can use the `insert()` method to place a column exactly where you want it.
   ```python
   # Inserts a new 'grade' column at position 0 (the first column) and fills it with 'A'.
   # Existing columns are shifted one position to the right.
   employees.insert(0, 'grade', 'A')
   ```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="3-2 Create a New Column-1" src="https://github.com/user-attachments/assets/359fc7fb-26dc-4434-a585-02f0cf8b771d" />
    <img width="1264" height="1635" alt="3-2 Create a New Column-2" src="https://github.com/user-attachments/assets/4e573f58-3ee7-4ae2-a919-2796d89773a7" />
  </div>
</details>
