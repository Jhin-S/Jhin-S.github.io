---
title: "2-1 Get the size of a DataFrame"
date: 2026-05-26 16:38:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, shape]
---

## 1. 데이터프레임 크기 구하기 (Get the Size of a DataFrame)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 두 번째 문제입니다. 주어진 데이터프레임 `players`의 행(Row)과 열(Column)의 개수를 구하여 리스트 형태로 반환하는 아주 간단한 문제입니다. Pandas의 가장 기본적이면서도 실무에서 가장 많이 쓰이는 속성 중 하나인 `shape`의 개념을 다룹니다.

**[EN]** This is the second problem in LeetCode's "Introduction to Pandas" track. The task is to find the number of rows and columns of the given DataFrame `players` and return it as a list. It covers the concept of `shape`, which is one of the most fundamental and frequently used attributes in Pandas.

### Input & Output Example

**Input (`players` DataFrame):**

| player_id | name | age | position | team |
| :--- | :--- | :--- | :--- | :--- |
| 846 | Mason | 21 | Forward | Real Madrid |
| 749 | Riley | 30 | Winger | Barcelona |
| 155 | Bob | 28 | Striker | Manchester United |

**Output:**
`[3, 5]`

---

## 2. Python 코드 구현 (Implementation)

**[KR]** DataFrame 객체 뒤에 `.shape` 속성을 호출하면 `(행의 개수, 열의 개수)` 형태의 튜플(Tuple)이 반환됩니다. 문제의 요구 조건이 `List[int]` 형태이므로, 이 튜플을 `list()` 함수로 감싸주기만 하면 완벽하게 해결됩니다.

**[EN]** accessing the `.shape` attribute of a DataFrame object returns a tuple in the format of `(number of rows, number of columns)`. Since the problem requires the return type to be a `List[int]`, simply wrapping this tuple with the `list()` function perfectly solves the problem.

```python
import pandas as pd
from typing import List

def getDataframeSize(players: pd.DataFrame) -> List[int]:
    # players.shape는 (행, 열) 형태의 튜플을 반환하므로 리스트로 변환합니다.
    # players.shape returns a tuple (rows, columns), so we convert it to a list.
    return list(players.shape)
```

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-1 Get the size of a DataFrame-1" src="https://github.com/user-attachments/assets/9439fb79-1b0d-412e-95c8-8c7377f70a68" />
  </div>
</details>
