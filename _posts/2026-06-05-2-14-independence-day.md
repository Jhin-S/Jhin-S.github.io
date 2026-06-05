---
title: "2-14 Independence Day"
date: 2026-06-05 16:11:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics I: A Gentle Introduction to Probability"]
tags: [probability, statistics, math, independence, disjoint, theorem]
math: true
---

## 1. 독립의 정의 (Definition of Independence)

**[KR]** 두 사건 $A$와 $B$가 일어나는 데 있어서 서로 어떠한 영향도 주지 않을 때, 이를 서로 **독립(Independent)**이라고 합니다. 수학적으로는 두 사건의 교집합(동시에 일어날) 확률이 각각의 사건이 일어날 확률의 곱과 같을 때 독립으로 정의합니다.

**[EN]** Two events $A$ and $B$ are independent if the probability of their intersection equals the product of their individual probabilities.

$$
P(A \cap B) = P(A)P(B)
$$

* **Remark 1:** 만약 $P(A) = 0$ 이라면, 사건 $A$는 다른 어떤 사건과도 무조건 독립이 됩니다. 
* **Remark 2:** 두 사건이 물리적으로 완전히 연관이 없어 보여야만 독립인 것은 아닙니다. 주사위 굴리기 같은 한 가지 행동 안에서 정의된 두 사건이라도 위의 수식만 만족하면 독립이 될 수 있습니다.

### 조금 더 자연스러운 해석 (More Natural Interpretation)
**[KR]** $P(B) > 0$일 때, $A$와 $B$가 독립이라면 **조건부 확률**의 정의에 의해 다음이 성립합니다. 즉, $B$가 일어났다는 정보가 $A$가 일어날 확률에 아무런 영향을 주지 못한다는 뜻입니다.

**[EN]** Suppose $P(B) > 0$. If $A$ and $B$ are independent, then:

$$
P(A \vert B) = \frac{P(A \cap B)}{P(B)} = \frac{P(A)P(B)}{P(B)} = P(A)
$$

---

## 2. 독립에 관한 추가 정리 (Bonus Theorems)

### 정리 1: 여사건의 독립 (Independence of Complements)
**[KR]** 만약 $A$와 $B$가 독립이라면, $A$와 $B$의 여사건($\bar{B}$) 또한 서로 독립입니다.
**[EN]** If $A$ and $B$ are independent, then $A$ and $\bar{B}$ are also independent.

* **Proof:**
  전체 확률의 법칙에 의해, $P(A) = P(A \cap B) + P(A \cap \bar{B})$ 입니다.
  
$$
P(A \cap \bar{B}) = P(A) - P(A \cap B)
$$

  여기서 $A$와 $B$가 독립이므로 $P(A \cap B) = P(A)P(B)$를 대입합니다.
  
$$
P(A \cap \bar{B}) = P(A) - P(A)P(B) = P(A)(1 - P(B)) = P(A)P(\bar{B})
$$

### 정리 2: 독립과 서로소의 차이 (Don't confuse independence with disjointness!)
**[KR]** 사건이 일어날 확률이 0보다 클 때, 두 사건은 **동시에 '독립'이면서 '서로소(배반사건)'일 수 없습니다.** 사실 이 둘은 거의 정반대의 개념입니다.

**[EN]** If $P(A) > 0$ and $P(B) > 0$, then $A$ and $B$ cannot be both independent and disjoint at the same time. In fact, independence and disjointness are almost opposites.

* **Proof & Interpretation:** 만약 $A$와 $B$가 서로소($A \cap B = \emptyset$)라면, $P(A \cap B) = 0$이 됩니다. 하지만 $P(A)P(B)$는 0보다 크므로, $P(A \cap B) \neq P(A)P(B)$ 가 되어 절대 독립일 수 없습니다.
  직관적으로 생각해 보면, $A$와 $B$가 서로소일 때 $A$가 일어났다는 것을 알게 되면 $B$는 '절대 일어날 수 없다'는 엄청난 정보를 얻게 되는 셈입니다. 즉, 강력한 영향을 주고받으므로 독립이 아닙니다.

---

## 3. 세 개 이상 사건의 독립 (Extension to more than two events)

**[KR]** 여러 개의 사건 $A_1, A_2, \dots, A_n$이 서로 독립이려면, 단순히 모든 사건의 교집합 확률이 개별 확률의 곱과 같아야 할 뿐만 아니라, 그들 중 **어떤 부분 집합(Subset)을 뽑아서 교집합을 구해도 개별 확률의 곱과 같아야 합니다.**

**[EN]** $A_1, A_2, \dots, A_n$ are independent if:
$$P(A_1 \cap \dots \cap A_n) = P(A_1) \times \dots \times P(A_n)$$
AND **all subsets of $\{A_1, \dots, A_n\}$ are also independent.**

### 독립 시행 (Independent Trials)
**[KR]** 한 번의 실험(Trial) 결과가 다른 실험의 결과에 아무런 영향을 미치지 않을 때, 이를 독립 시행이라고 합니다. 독립 시행의 확률은 고민할 것 없이 **각각의 확률을 단순히 곱해주기만 하면 됩니다.**

**[EN]** Perform $n$ trials of an experiment such that the outcome of one trial is independent of the outcomes of the other trials. For independent trials, you just multiply the individual probabilities.

* **Example:** 동전 3개를 무작위로 던질 때 (Flip 3 coins independently)
  * 첫 번째 동전이 앞면(H)일 확률 = $\frac{1}{2}$ (나머지 동전의 결과와 상관없음)
  * 첫 번째 동전이 앞면(H)이고, 세 번째 동전이 뒷면(T)일 확률 = $P(\text{1st H})P(\text{3rd T}) = \frac{1}{2} \times \frac{1}{2} = \frac{1}{4}$

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="2-14 Independence Day-1" src="https://github.com/user-attachments/assets/10032da2-129e-483d-9bd9-2c7aafca1a86" />
    <img width="1264" height="1635" alt="2-14 Independence Day-2" src="https://github.com/user-attachments/assets/0b1914db-eacb-425c-864b-f3e3d15339e9" />
    <img width="1264" height="1635" alt="2-14 Independence Day-3" src="https://github.com/user-attachments/assets/40992e36-6de2-488e-839a-cf137418d011" />
    <img width="1264" height="1635" alt="2-14 Independence Day-4" src="https://github.com/user-attachments/assets/3074b444-5033-4a48-b923-e15b5e3ca632" />
  </div>
</details>
