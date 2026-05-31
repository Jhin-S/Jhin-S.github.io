---
title: "1-1 Introduction to Probability and Statistics"
date: 2026-05-31 20:45:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, uncertainty, monty_hall, probabilistic_models]
---

## 1. 확률적 모델과 불확실성 (Probabilistic Models & Uncertainty)

**[KR]** 확률적 모델은 기본적으로 **불확실성(Uncertainty)**을 다루는 방법론입니다. 내일 눈이 얼마나 올지, 특정 기업(예: IBM)이 올해 수익을 낼 수 있을지, 주식의 콜/풋 옵션을 사야 할지, 혹은 블랙잭에서 특정 전략을 쓰면 이길 수 있을지 등 현실의 불확실한 문제들을 수학적으로 모델링합니다.

---

## 2. 확률의 실생활 예시 (Examples of Probability)

**[KR]** 불확실성을 계산하는 몇 가지 고전적인 예시는 다음과 같습니다.

### 2.1. 포커 (Poker)
**[KR]** 52장의 표준 카드 덱에서 무작위로 5장의 카드를 뽑을 때, 특정 패가 나올 확률을 계산할 수 있습니다.
* **투 페어(Exactly 2 pairs):** $\approx 0.0475$
* **풀 하우스(Full house):** $\approx 0.00144$
* **플러시(Flush):** $\approx 0.00198$

### 2.2. 조건부 확률 (Boy/Girl Problem)
**[KR]** 어떤 부부에게 두 명의 자녀가 있고, 그중 **적어도 한 명이 아들**이라는 것을 알고 있을 때, **두 자녀 모두 아들일 확률**은 얼마일까요?
1. 두 자녀의 성별 조합은 GG(딸, 딸), BG(아들, 딸), GB(딸, 아들), BB(아들, 아들) 4가지입니다.
2. 적어도 한 명이 아들이라는 조건이 있으므로, GG(딸, 딸) 조합은 제거(Eliminate)됩니다.
3. 남은 3가지(BG, GB, BB) 경우 중 두 명 모두 아들인 경우는 BB 1가지뿐이므로, 구하는 확률 $P(BB)$는 **$1/3$**이 됩니다.

### 2.3. 몬티 홀 문제 (Monty Hall Problem)

**[KR]** 게임 쇼의 참가자(Ask Marilyn)가 3개의 문 중 하나를 선택하는 상황입니다. 하나의 문 뒤에는 자동차가, 나머지 두 개의 문 뒤에는 염소가 있습니다. 
1. 참가자가 문 A를 선택합니다.
2. 진행자(Monty Hall)가 염소가 있는 문 B를 열어서 보여줍니다.
3. 진행자가 문 C로 선택을 바꿀 기회(Switch)를 제안합니다.
이때 참가자는 선택을 바꾸는 것이 유리할까요? 정답은 **"바꾼다(SWITCH!)"**입니다.

---

## 3. 작동 정의: 확률 vs 통계 (Working Definitions)

**[KR]** 확률과 통계는 밀접하게 연관되어 있지만, 다루는 방향성에 차이가 있습니다. 앞으로의 학습 과정에서 각각 50%의 비중으로 다루게 됩니다.

* **확률 (Probability):** 시스템 내에서 발생하는 무작위적 변동성(Random variation)을 설명하는 방법론입니다. (이론적 모델을 바탕으로 미래의 결과를 예측)
* **통계 (Statistics):** 추출된 표본(Sample) 데이터를 사용하여, 그 표본이 추출된 전체 모집단(Population)에 대한 일반적인 결론을 도출하는 학문입니다. (과거의 데이터를 바탕으로 시스템의 특성을 추론)

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-1 Introduction to Probability and Statistics-1" src="https://github.com/user-attachments/assets/c8af8c06-0107-493e-974d-586b95e2b44a" />
    <img width="1264" height="1635" alt="1-1 Introduction to Probability and Statistics-2" src="https://github.com/user-attachments/assets/be779e21-c568-460c-9f9f-338639454be6" />
  </div>
</details>
