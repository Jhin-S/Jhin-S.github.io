---
title: "Metacognitive Note-taking: Pandas 핵심 요약"
date: 2026-05-27 15:00:00 +0900
categories: ["Pandas", "Introduction to Pandas"]
tags: [pandas, python, leetcode, dataframe, cheatsheet, metacognition]
---

## 1. 메타인지 학습법: Pandas 총정리 (Metacognitive Summary)

**[KR]** LeetCode의 Pandas 입문(Introduction to Pandas) 트랙에서 다룬 15가지 핵심 기능들을 복습하고 장기 기억으로 전환하기 위한 총정리(Cheat Sheet) 문서입니다. 데이터프레임 생성부터 결측치 처리, 데이터 재구조화, 그리고 메서드 체이닝까지 실무 데이터 분석에서 가장 빈번하게 사용되는 필수 메서드들을 요약했습니다.

**[EN]** This is a cheat sheet designed to review and solidify the 15 core functions covered in LeetCode's "Introduction to Pandas" track. It summarizes the essential methods most frequently used in practical data analysis, ranging from DataFrame creation to missing data handling, data reshaping, and method chaining.

---

## 2. Pandas 핵심 문법 요약 (Core Syntax Cheat Sheet)

### 2.1. 데이터 생성 및 확인 (Creation & Inspection)
* **데이터프레임 생성 (Create):** `pd.DataFrame(data, columns=['col1', 'col2'])`
* **크기 확인 (Size):** `df.shape`를 사용하면 (행의 개수, 열의 개수) 형태의 튜플(Tuple)을 반환합니다.
* **데이터 미리보기 (Preview):** `head()`는 앞에서부터, `tail()`은 뒤에서부터 데이터를 추출합니다.

### 2.2. 데이터 선택 및 열 조작 (Selection & Column Operations)
* **데이터 선택 (`loc` & `[]`):** `df.loc[행 조건, 열 조건]` 구조를 사용합니다.
  * 대괄호(`[]`) 안에 열 이름을 넣으면 열을 추출하고, 조건식을 넣으면 조건에 맞는 행을 필터링하며, 숫자 범위를 넣으면 해당 인덱스의 행을 슬라이싱하여 추출합니다.
* **열 추가 및 삽입 (New Column):** `df['새로운 열'] = 데이터` 형태로 끝에 추가하거나, `df.insert(인덱스, '열 이름', 데이터)`를 통해 원하는 위치에 삽입할 수 있습니다.
* **열 데이터 덮어쓰기 (Modify):** 이미 존재하는 열에 새로운 데이터를 할당하면 기존 데이터가 덮어씌워집니다.
* **열 이름 변경 (Rename):** `df.rename(columns={'old': 'new'})` 형태로 딕셔너리 매핑을 사용합니다.
* **데이터 타입 변환 (Type Casting):** `df['col'].astype(int)`와 같이 `astype()` 메서드를 사용합니다.

### 2.3. 데이터 정제 (Data Cleansing)
* **중복 제거 (Drop Duplicates):** `df.drop_duplicates(subset=['col'])`.
  * `keep='first'`(첫 번째 유지), `keep='last'`(마지막 유지), `keep=False`(중복 데이터 모두 삭제) 옵션을 활용할 수 있습니다.
  * `subset`을 생략하면 모든 열의 값이 완전히 일치해야 삭제됩니다.
* **결측치 제거 (Drop NA):** `df.dropna(subset=['col'])`.
* **결측치 채우기 (Fill NA):** `df['col'].fillna(0)`을 사용하여 결측치를 특정 값으로 일괄 대체합니다.

### 2.4. 데이터 재구조화 및 체이닝 (Reshaping & Chaining)
* **병합 (Concatenate):** `pd.concat([df1, df2])`는 세로로 데이터를 병합하며, 가로로 병합할 때는 `axis=1`을 추가합니다.
* **피벗 (Pivot):** `df.pivot(index='행 기준', columns='열 기준', values='데이터 값')` 형태로 데이터를 넓게 재배치합니다.
* **멜트 (Melt):** `df.melt(id_vars=['기준열'], var_name='새 열', value_name='값 열')`.
  * 가로로 넓은 표를 녹여서 세로로 길게 변환하며, 머신러닝(Machine Learning) 모델 학습 시 데이터 전처리에 자주 사용됩니다.
* **메서드 체이닝 (Method Chaining):** `df[df['col'] > 100].sort_values(by='col', ascending=False)[['col2']]`처럼 필터링, 정렬, 추출 등 여러 과정을 한 줄의 코드로 순차적으로 실행합니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Metacognitive Note-taking-01" src="https://github.com/user-attachments/assets/b0d302ff-bdf2-4ace-b627-0cf321fdf5a7" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-02" src="https://github.com/user-attachments/assets/706d0cdb-b88d-464a-81b0-c3a87e7982bc" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-03" src="https://github.com/user-attachments/assets/5b1217a2-db7c-419e-9f25-47840ee615c4" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-04" src="https://github.com/user-attachments/assets/06b33563-dd24-4447-ba2b-ea2bf6edd3cf" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-05" src="https://github.com/user-attachments/assets/c8f944eb-6a0d-41cf-a2ae-3f22cd080dc1" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-06" src="https://github.com/user-attachments/assets/9a3c7dc2-78aa-45fb-aa8e-0f06201d5f7e" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-07" src="https://github.com/user-attachments/assets/a5e8fb45-eadf-4f2b-ba67-3b662641a05f" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-08" src="https://github.com/user-attachments/assets/7a20bd10-4399-4101-801a-1fb51dc89d2c" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-09" src="https://github.com/user-attachments/assets/0884f6d8-c874-413b-bc7c-6e3325ed69eb" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-10" src="https://github.com/user-attachments/assets/d2bc648e-1076-42c7-8259-e16cd56004b8" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-11" src="https://github.com/user-attachments/assets/bcf9d892-ef1a-47ac-b4a8-8e3dbc11f3ea" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-12" src="https://github.com/user-attachments/assets/392438f1-bdf8-4720-8f84-b49d986721c8" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-13" src="https://github.com/user-attachments/assets/f5533132-ee25-489b-ab2c-0515db9bc97c" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-14" src="https://github.com/user-attachments/assets/ac750bab-8b0e-4885-98a0-98b6ddbd7f95" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-15" src="https://github.com/user-attachments/assets/c96a7d00-1732-4dcd-acee-dd160150dcb1" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-16" src="https://github.com/user-attachments/assets/b4373a97-cfe4-405a-a019-a112adc366c0" />
    <img width="1264" height="1635" alt="Metacognitive Note-taking-17" src="https://github.com/user-attachments/assets/ed565213-be91-4cf8-afcd-d9e0870eba02" />
  </div>
</details>
