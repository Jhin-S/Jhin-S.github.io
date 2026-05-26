---
title: "5-3 Reshape Data: Melt"
date: 2026-05-26 18:25:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, melt, reshape]
---

## 1. 데이터 재구조화: 멜트 (Reshape Data: Melt)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 가로로 넓게 퍼져 있는(Wide-format) `report` 데이터프레임을 세로로 긴(Long-format) 형태로 변환하는 과정을 다룹니다. 앞서 다룬 `pivot`의 반대 역할을 수행하며, 여러 열에 분산된 데이터를 기준 열을 바탕으로 하나의 열로 모아줍니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of transforming a wide-format `report` DataFrame into a long-format. It performs the opposite function of `pivot`, gathering data distributed across multiple columns into a single column based on an identifier column.

### Input & Output Example

**Input (`report` DataFrame):**

| product | quarter_1 | quarter_2 | quarter_3 | quarter_4 |
| :--- | :--- | :--- | :--- | :--- |
| Umbrella | 417 | 224 | 379 | 611 |
| Sleeping Bag | 800 | 936 | 93 | 875 |

**Output:**

| product | quarter | sales |
| :--- | :--- | :--- |
| Umbrella | quarter_1 | 417 |
| Sleeping Bag | quarter_1 | 800 |
| Umbrella | quarter_2 | 224 |
| Sleeping Bag | quarter_2 | 936 |
| Umbrella | quarter_3 | 379 |
| Sleeping Bag | quarter_3 | 93 |
| Umbrella | quarter_4 | 611 |
| Sleeping Bag | quarter_4 | 875 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `melt()` 메서드를 사용하면 여러 열의 이름들을 데이터 값으로 변환하여 새로운 열로 내릴 수 있습니다. `id_vars`를 기준으로 나머지 열들이 압축되어 내려옵니다.

**[EN]** Using Pandas' `melt()` method allows you to convert multiple column names into data values and melt them down into a new column. The remaining columns are compressed down based on `id_vars`.

```python
import pandas as pd

def meltTable(report: pd.DataFrame) -> pd.DataFrame:
    # product 열을 기준으로 나머지 분기별 데이터를 quarter와 sales 열로 재배치합니다.
    # Rearrange the quarterly data into quarter and sales columns based on the product column.
    ans = report.melt(
        id_vars=['product'],
        var_name='quarter',
        value_name='sales'
    )
    return ans
```

---

## 3. `melt()` 메서드의 핵심 파라미터 (Key Parameters of `melt()`)

**[KR]** 1. **`id_vars`**: 기준점이 되는 열입니다. 해당 열의 데이터는 변형되지 않고 그대로 유지됩니다.
2. **`var_name`**: 가로로 퍼져있던 기존 열의 이름들이 하나로 모이게 될 **새로운 열의 이름**입니다.
3. **`value_name`**: 원래 표 안에 존재하던 실제 데이터 값들이 모이게 될 **새로운 열의 이름**입니다.

**[EN]**
1. **`id_vars`**: The identifier column(s). The data in this column remains unchanged.
2. **`var_name`**: The **new column name** where the previously spread-out column headers will be gathered.
3. **`value_name`**: The **new column name** where the actual data values from the original table will be gathered.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="5-3 Reshape Data_ Melt-1" src="https://github.com/user-attachments/assets/d33d667e-e82c-49f0-9646-a229024bbb45" />
    <img width="1264" height="1635" alt="5-3 Reshape Data_ Melt-2" src="https://github.com/user-attachments/assets/728a50c6-abfb-4dfc-ad9b-8f36014080dc" />
  </div>
</details>
