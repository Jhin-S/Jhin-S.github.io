---
title: "5-2 Reshape Data: Pivot"
date: 2026-05-26 18:15:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, pivot, reshape]
---

## 1. 데이터 재구조화: 피벗 (Reshape Data: Pivot)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 주어진 `weather` 데이터프레임의 형태를 변환하여, 특정 열을 행(Row) 인덱스로, 다른 열을 새로운 열(Column)로, 그리고 남은 열을 교차점의 데이터 값(Value)으로 재배치하는 과정을 다룹니다. 세로로 긴(Long-format) 데이터를 가로로 넓은(Wide-format) 데이터로 바꿀 때 유용하게 쓰입니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of transforming the shape of the given `weather` DataFrame by reassigning a specific column as the row index, another column as the new columns, and the remaining column as the intersection data values. This is particularly useful when converting long-format data into wide-format data.

### Input & Output Example

**Input (`weather` DataFrame):**

| city | month | temperature |
| :--- | :--- | :--- |
| Jacksonville | January | 13 |
| Jacksonville | February | 23 |
| Jacksonville | March | 38 |
| Jacksonville | April | 5 |
| Jacksonville | May | 34 |
| El Paso | January | 20 |
| El Paso | February | 6 |
| El Paso | March | 26 |
| El Paso | April | 2 |
| El Paso | May | 43 |

**Output:**
(`month`가 행으로, `city`가 열로 이동하며 해당 교차점에 `temperature`가 배치됩니다.)

| month | El Paso | Jacksonville |
| :--- | :--- | :--- |
| April | 2 | 5 |
| February | 6 | 23 |
| January | 20 | 13 |
| March | 26 | 38 |
| May | 43 | 34 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `pivot()` 메서드를 사용하면 복잡한 데이터프레임을 원하는 기준으로 쉽게 재배치할 수 있습니다. 각 파라미터에 기준이 될 열의 이름을 문자열로 전달하면 됩니다.

**[EN]** You can easily rearrange a complex DataFrame based on desired criteria using Pandas' `pivot()` method. You simply pass the names of the target columns as strings to each respective parameter.

```python
import pandas as pd

def pivotTable(weather: pd.DataFrame) -> pd.DataFrame:
    # month를 행으로, city를 열로, temperature를 값으로 지정하여 피벗 테이블을 생성합니다.
    # Create a pivot table with month as rows, city as columns, and temperature as values.
    ans = weather.pivot(index='month', columns='city', values='temperature')
    
    return ans
```

---

## 3. `pivot()` 메서드의 핵심 파라미터 (Key Parameters of `pivot()`)

**[KR]** `pivot()` 메서드는 주로 3가지 핵심 파라미터를 입력받아 작동합니다.
1. **`index`**: 새로운 데이터프레임의 **행(가로줄)** 기준이 될 기존 열의 이름입니다.
2. **`columns`**: 새로운 데이터프레임의 **열(세로줄)** 기준이 될 기존 열의 이름입니다.
3. **`values`**: 행과 열이 교차하는 지점(Cell)에 들어갈 **실제 데이터 값**이 있는 열의 이름입니다.

**[EN]** The `pivot()` method primarily operates by taking 3 key parameters:
1. **`index`**: The name of the existing column that will become the new **row** index.
2. **`columns`**: The name of the existing column that will become the new **column** headers.
3. **`values`**: The name of the existing column containing the **actual data values** to populate the intersecting cells.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-2 Reshape Data_ Pivot-1" src="https://github.com/user-attachments/assets/c08963d5-23e0-41bc-8179-23dfd00c0633" />
    <img width="1264" height="1635" alt="5-2 Reshape Data_ Pivot-2" src="https://github.com/user-attachments/assets/50f23064-d754-46c9-ae8c-dd69826776a5" />
  </div>
</details>
