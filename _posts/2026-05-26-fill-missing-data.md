---
title: "4-6 Fill Missing Data"
date: 2026-05-26 18:00:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, fillna, missing_data]
---

## 1. 결측치 채우기 (Fill Missing Data)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. 주어진 `products` 데이터프레임에서 `quantity` 열에 존재하는 결측치(None, NaN)를 숫자 `0`으로 일괄 대체하는 과정을 다룹니다. 앞서 다룬 결측치 제거(`dropna`)와 함께 데이터 전처리 과정에서 가장 빈번하게 사용되는 결측치 보간(Imputation) 작업입니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. It covers the process of replacing all missing values (None, NaN) in the `quantity` column of the `products` DataFrame with the number `0`. Along with dropping missing values (`dropna`), this data imputation task is one of the most frequently performed operations during data preprocessing.

### Input & Output Example

**Input (`products` DataFrame):**

| name | quantity | price |
| :--- | :--- | :--- |
| Wristwatch | None | 135 |
| Wireless Earbuds | None | 821 |
| Golf Clubs | 779 | 9319 |
| Printer | 849 | 3051 |

**Output:**
(`quantity` 열의 결측치인 `None` 값들이 모두 `0`으로 채워집니다.)

| name | quantity | price |
| :--- | :--- | :--- |
| Wristwatch | 0 | 135 |
| Wireless Earbuds | 0 | 821 |
| Golf Clubs | 779 | 9319 |
| Printer | 849 | 3051 |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** Pandas의 `fillna()` 메서드를 사용하면 데이터프레임이나 특정 열(Series)에 존재하는 모든 결측치를 원하는 값으로 한 번에 채울 수 있습니다. 변환하고자 하는 대상 열(`products['quantity']`)을 지정한 뒤 `.fillna(0)`을 적용하고, 이를 다시 기존 열에 덮어쓰면 갱신이 완료됩니다.

**[EN]** Using Pandas' `fillna()` method, you can replace all missing values in a DataFrame or a specific column (Series) with a desired value at once. By selecting the target column (`products['quantity']`), applying `.fillna(0)`, and reassigning it back to the original column, the update is complete.

```python
import pandas as pd

def fillMissingValues(products: pd.DataFrame) -> pd.DataFrame:
    # 'quantity' 열의 결측치를 찾아 숫자 0으로 채워 넣은 후 기존 열에 덮어씁니다.
    # Find missing values in the 'quantity' column, fill them with 0, and overwrite the column.
    products['quantity'] = products['quantity'].fillna(0)
    
    return products
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="4-6 Fill Missing Data-1" src="https://github.com/user-attachments/assets/13e7d027-8e76-403f-90d2-7e034a9df36d" />
  </div>
</details>
