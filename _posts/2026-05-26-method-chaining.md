---
title: "6-1 Method Chaining"
date: 2026-05-26 18:35:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, method_chaining, sort_values]
---

## 1. 메서드 체이닝 (Method Chaining)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙 문제입니다. [cite_start]주어진 `animals` 데이터프레임에서 몸무게(`weight`)가 100을 초과하는 동물들을 찾아내고, 이들을 몸무게 기준 내림차순(무거운 순서대로)으로 정렬한 뒤, 동물의 이름(`name`) 열만 추출하여 반환하는 과정을 다룹니다[cite: 424, 425, 426, 427]. 여러 데이터 조작 단계를 한 줄의 코드로 연결하여 실행하는 **메서드 체이닝(Method Chaining)** 기법을 활용합니다.

**[EN]** This is a problem from LeetCode's "Introduction to Pandas" track. [cite_start]It covers the process of filtering animals weighing strictly more than 100 from the `animals` DataFrame, sorting them in descending order by weight, and then extracting only the `name` column[cite: 424, 425, 426, 427]. This demonstrates **Method Chaining**, a technique where multiple data manipulation steps are linked together in a single line of code.

### Input & Output Example

**Input (`animals` DataFrame):**

| name | species | age | weight |
| :--- | :--- | :--- | :--- |
| Tatiana | Snake | 98 | 464 |
| Khaled | Giraffe | 50 | 41 |
| Alex | Leopard | 6 | 328 |
| Jonathan | Monkey | 45 | 463 |
| Stefan | Bear | 100 | 50 |
| Tommy | Panda | 26 | 349 |

**Output:**

| name |
| :--- |
| Tatiana |
| Jonathan |
| Tommy |
| Alex |

---

## 2. Python 코드 구현 (Implementation)

**[KR]** 메서드 체이닝을 사용하면 코드를 간결하게 작성할 수 있으며, 중간 과정마다 새로운 변수를 할당할 필요가 없어 메모리 효율성 측면에서도 유리합니다.

**[EN]** Using method chaining allows you to write concise code and is advantageous in terms of memory efficiency because you don't need to assign new variables for each intermediate step.

```python
import pandas as pd

def findHeavyAnimals(animals: pd.DataFrame) -> pd.DataFrame:
    # 필터링 -> 정렬 -> 열 선택 과정을 한 줄로 연결합니다.
    # Connects filtering -> sorting -> column selection in a single line.
    result = animals[animals['weight'] > 100].sort_values(by='weight', ascending=False)[['name']]
    return result
```

---

## 3. 코드 상세 분석 (Detailed Analysis of the Chain)

[cite_start]**[KR]** 작성된 한 줄의 코드는 크게 3단계로 나누어 순차적으로 실행됩니다[cite: 430].
1. [cite_start]**필터링 (`animals[animals['weight'] > 100]`):** 몸무게가 100 초과인 행만 추출합니다[cite: 430].
2. **정렬 (`.sort_values(by='weight', ascending=False)`):** 추출된 데이터를 `weight` 열을 기준으로 내림차순(무거운 순) 정렬합니다. [cite_start]`ascending=False`가 내림차순을 의미합니다[cite: 430].
3. [cite_start]**열 선택 (`[['name']]`):** 정렬까지 완료된 데이터프레임에서 오직 `name` 열만 떼어내어 최종 결과로 반환합니다[cite: 430].

[cite_start]**[EN]** The single line of code is executed sequentially in 3 main steps[cite: 430]:
1. [cite_start]**Filtering (`animals[animals['weight'] > 100]`):** Extracts only the rows where the weight is strictly greater than 100[cite: 430].
2. **Sorting (`.sort_values(by='weight', ascending=False)`):** Sorts the filtered data by the `weight` column in descending order (heaviest first). [cite_start]`ascending=False` specifies the descending order[cite: 430].
3. [cite_start]**Column Selection (`[['name']]`):** Selects and returns only the `name` column from the fully sorted DataFrame[cite: 430].

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="6-1 Method Chaining-1" src="https://github.com/user-attachments/assets/a7f29f7f-b4e2-4a30-967f-039dc4fd438b" />
    <img width="1264" height="1635" alt="6-1 Method Chaining-2" src="https://github.com/user-attachments/assets/56481ae2-f7ae-44b2-a79a-6b7c6b5c9f66" />
  </div>
</details>
