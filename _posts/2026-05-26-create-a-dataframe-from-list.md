---
title: "1-1 Create a DataFrame from List"
date: 2026-05-26 16:15:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe]
---

## 1. 리스트로 데이터프레임 만들기 (Create a DataFrame from List)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 첫 번째 문제입니다. 주어진 2차원 리스트(List of Lists)인 `student_data`를 Pandas의 핵심 자료구조인 `DataFrame` 객체로 변환하는 가장 기초적인 과정을 다룹니다. 변환과 동시에 각 열(Column)의 이름을 `student_id`와 `age`로 지정해 주어야 합니다.

**[EN]** This is the first problem from LeetCode's "Introduction to Pandas" track. It covers the most fundamental process of converting a given 2D list (List of Lists), `student_data`, into a Pandas `DataFrame` object, which is the core data structure in Pandas. During the conversion, we must also assign the column names as `student_id` and `age`.

### Input & Output Example

**Input:**
`student_data = [[1, 15], [2, 11], [3, 11], [4, 20]]`

**Output:**

| student_id | age |
| :--- | :--- |
| 1 | 15 |
| 2 | 11 |
| 3 | 11 |
| 4 | 20 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas 모듈을 불러온 뒤, `pd.DataFrame()` 생성자를 사용하여 데이터를 데이터프레임으로 변환합니다. 이때 `columns` 파라미터에 리스트 형태로 원하는 컬럼명들을 순서대로 전달하면 손쉽게 컬럼 이름을 부여할 수 있습니다.

**[EN]** After importing the Pandas module, we use the `pd.DataFrame()` constructor to convert the data. By passing a list of desired column names to the `columns` parameter in the correct order, we can easily assign names to the columns.

```python
import pandas as pd
from typing import List

def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    # student_data 리스트와 컬럼명 리스트를 매핑하여 DataFrame 생성
    # Create a DataFrame by mapping the student_data list with the list of column names
    df = pd.DataFrame(student_data, columns=['student_id', 'age'])
    
    return df
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1 Create a DataFrame from List-1" src="https://github.com/user-attachments/assets/27c44200-dce9-4b22-a45b-e977285dbca9" />
  </div>
</details>
