---
title: "2-12 Poker Problems"
date: 2026-06-05 15:06:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, poker, combinations, permutations]
math: true
---

## 1. 기본 설정 (Basic Setup)

**[KR]** 조커가 없는 표준 52장의 트럼프 카드 덱에서 무작위로 5장의 카드를 뽑습니다. 카드는 13개의 숫자(Rank: 2, 3, ..., Q, K, A)와 4개의 문양(Suit: ♠, ♡, ♢, ♣)으로 이루어져 있습니다. 전체 5장 카드 조합의 수는 다음과 같습니다.

**[EN]** Draw 5 cards at random from a standard 52-card deck. A deck has 13 ranks (2, 3, ..., Q, K, A) and 4 suits (♠, ♡, ♢, ♣). The total number of possible 5-card hands is the sample space $|S|$.

$$
|S| = \binom{52}{5} = 2,598,960
$$

---

## 2. 포커 족보별 확률 계산 (Probabilities of Poker Hands)

### (a) 투 페어 (2 Pairs)

**[KR]** 두 개의 숫자 쌍과 나머지 하나의 다른 숫자로 이루어진 패입니다. (예: A♠, A♡, 3♢, 3♣, 10♠) ※ 풀 하우스를 제외하기 위해 남은 한 장은 페어의 숫자와 달라야 합니다.

**[EN]** A hand with two pairs and one distinct card. We must avoid drawing a full house.

* 2개의 페어가 될 숫자 2개 고르기 (Select 2 ranks): $\binom{13}{2}$
* 첫 번째 페어의 문양 2개 고르기 (Select 2 suits for 1st pair): $\binom{4}{2}$
* 두 번째 페어의 문양 2개 고르기 (Select 2 suits for 2nd pair): $\binom{4}{2}$
* 남은 1장의 카드를 뽑는 경우 (Select remaining card to complete the hand): 풀 하우스를 방지하기 위해 남은 카드 중 $44$장($52 - 8$)에서 선택.

$$
|\text{2 Pairs}| = \binom{13}{2} \times \binom{4}{2} \times \binom{4}{2} \times 44 = 123,552
$$

$$
P(\text{2 Pairs}) = \frac{123,552}{2,598,960} \approx 0.0475
$$

### (b) 풀 하우스 (Full House)

**[KR]** 같은 숫자 3장(Triple)과 같은 숫자 2장(Pair)으로 이루어진 패입니다. (예: A♣, A♠, 3♡, 3♢, 3♠)

**[EN]** A hand consisting of a 3-of-a-kind and a pair.

* 역할을 할 숫자 2개를 **순서를 고려하여** 고르기 (Select 2 ordered ranks, since the triple and pair are different): $P_{13, 2} = 13 \times 12$
* 페어(2장)의 문양 2개 고르기 (Select 2 suits for pair): $\binom{4}{2}$
* 트리플(3장)의 문양 3개 고르기 (Select 3 suits for 3-of-a-kind): $\binom{4}{3}$

$$
|\text{Full House}| = 13 \times 12 \times \binom{4}{2} \times \binom{4}{3} = 3,744
$$

$$
P(\text{Full House}) = \frac{3,744}{2,598,960} \approx 0.00144
$$

### (c) 플러시 (Flush)

**[KR]** 5장의 카드가 모두 동일한 문양인 패입니다. (스트레이트 플러시 등 모든 종류의 플러시 포함)

**[EN]** All 5 cards are from the same suit. (This includes all kinds of flushes, such as straight flushes).

* 1개의 문양 고르기 (Select a suit): $4$
* 해당 문양 13장 중 5장 고르기 (Select 5 cards from that suit): $\binom{13}{5}$

$$
|\text{Flush}| = 4 \times \binom{13}{5} = 5,148
$$

$$
P(\text{Flush}) = \frac{5,148}{2,598,960} \approx 0.00198
$$

### (d) 스트레이트 (Straight)

**[KR]** 5장의 카드가 문양에 상관없이 연속된 숫자를 이루는 패입니다. (예: 4, 5, 6, 7, 8)

**[EN]** 5 cards of sequential rank, regardless of suit. (This includes all straights).

* 스트레이트가 시작되는 가장 낮은 숫자 고르기 (Select a starting point for the straight: A, 2, 3, ..., 10): $10$가지
* 각각의 5장 카드에 대해 문양 1개씩 고르기 (Select a suit for each card): $4^5$

$$
|\text{Straight}| = 10 \times 4^5 = 10,240
$$

$$
P(\text{Straight}) = \frac{10,240}{2,598,960} \approx 0.00394
$$

### (e) 스트레이트 플러시 (Straight Flush)

**[KR]** 5장의 카드가 연속된 숫자이면서, 문양도 모두 동일한 패입니다.

**[EN]** 5 cards of sequential rank that are all of the same suit.

* 스트레이트가 시작되는 가장 낮은 숫자 고르기 (Select a starting point): $10$가지
* 5장 모두 통일될 문양 1가지 고르기 (Select a suit): $4$가지

$$
|\text{Straight Flush}| = 10 \times 4 = 40
$$

$$
P(\text{Straight Flush}) = \frac{40}{2,598,960} \approx 0.0000154
$$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-12 Poker Problems-1" src="https://github.com/user-attachments/assets/bde15278-e345-4cd3-b4d2-a6fa69539a01" />
    <img width="1264" height="1635" alt="2-12 Poker Problems-2" src="https://github.com/user-attachments/assets/cebf171e-17f7-4f62-8835-d4da25072fa2" />
    <img width="1264" height="1635" alt="2-12 Poker Problems-3" src="https://github.com/user-attachments/assets/f0819dda-83fb-4048-acb1-2ac258a0f367" />
  </div>
</details>
