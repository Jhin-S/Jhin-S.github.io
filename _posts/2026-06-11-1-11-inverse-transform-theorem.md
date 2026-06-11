---
title: "1-11 Inverse Transform Theorem"
date: 2026-06-11 11:43:00 +0900
categories: ["GTx Probability/Random Variables", "Probability and Statistics II: Random Variables – Great Expectations to Bell Curves"]
tags: [probability, statistics, math, inverse-transform, simulation, exponential-distribution]
math: true
---

## 1. 역변환 정리 (Inverse Transform Theorem)

**[KR]** 연속 확률 변수 $X$의 누적 분포 함수(CDF)인 $F(x)$에 변수 $X$ 자체를 대입하여 새로운 확률 변수 $Y = F(X)$를 만든다고 상상해 봅시다. 놀랍게도 이 새로운 확률 변수 $Y$는 원래 $X$가 어떤 분포였는지에 상관없이 **항상 0과 1 사이의 균등 분포 $Unif(0, 1)$를 따르게 됩니다.** 이를 '역변환 정리'라고 부릅니다.

**[EN]** Suppose we have a continuous random variable $X$ with a cumulative distribution function (CDF) denoted as $F(x)$. If we plug the random variable $X$ itself into its own CDF, creating a new random variable $Y = F(X)$, this new variable $Y$ will **always follow a standard Uniform distribution, $Unif(0, 1)$**, regardless of the original distribution of $X$. This elegant property is called the Inverse Transform Theorem.

### 수학적 증명 (Proof)
새로운 확률 변수 $Y = F(X)$ 의 누적 분포 함수를 $G(y)$ 라고 합시다.
$$
G(y) = P(Y \le y) = P(F(X) \le y)
$$
양변에 역함수 $F^{-1}$을 취해줍니다.
$$
= P(X \le F^{-1}(y))
$$
$P(X \le x)$ 의 정의 자체가 CDF인 $F(x)$ 이므로, 괄호 안의 값을 $F$ 에 대입합니다.
$$
= F(F^{-1}(y)) = y
$$
누적 분포 함수가 $G(y) = y$ 인 분포는 오직 구간 $[0, 1]$ 에서의 균등 분포뿐입니다. 따라서 $Y \sim Unif(0, 1)$ 이 증명됩니다.

---

## 2. 역변환 방법론과 시뮬레이션 (Inverse Transform Method)

**[KR]** 이 정리가 통계학과 컴퓨터 공학에서 엄청난 가치를 지니는 이유는 **'난수 생성(Simulation)'** 때문입니다. 엑셀의 `rand()`나 파이썬의 `random()` 같은 기본 함수들은 단순히 0과 1 사이의 균등 분포 난수만을 만들어냅니다. 하지만 역변환 정리를 응용하면, 이 단순한 $U \sim Unif(0, 1)$ 난수를 활용해 우리가 원하는 모든 형태의 연속 확률 분포 난수를 무한히 만들어낼 수 있습니다.

**[EN]** The true power of this theorem lies in computer simulation. Basic programming functions like `rand()` only generate uniform random numbers between 0 and 1. However, by applying the Inverse Transform Method, we can use these simple uniform random numbers ($U \sim Unif(0, 1)$) to generate random variables that follow absolutely any continuous distribution we desire.

* **시뮬레이션 절차 (Method):**
  1. $X$의 CDF인 $F(x)$를 구합니다.
  2. $F(x) = U$ 라고 설정합니다. (이때 $U$는 0과 1 사이의 균등 분포 난수입니다.)
  3. $x$ 에 대하여 식을 정리하여 역함수 $X = F^{-1}(U)$ 를 도출합니다.
  4. 컴퓨터로 $U$ 값을 무작위로 뽑아낸 뒤 역함수에 대입하면, 원하는 분포를 따르는 데이터가 생성됩니다.

---

## 3. 지수 분포 난수 생성 예제 (Generating Exponential RVs)

**[KR]** 대기 시간이나 고장 시간을 모델링할 때 자주 쓰이는 지수 분포 $X \sim Exp(\lambda)$ 를 따르는 가상의 데이터를 컴퓨터로 시뮬레이션해 봅시다.

**[EN]** Let's generate simulated data following an exponential distribution $X \sim Exp(\lambda)$, which is commonly used to model waiting times or machine breakdown times.

1. 지수 분포의 CDF는 다음과 같습니다.
   $$F(x) = 1 - e^{-\lambda x}$$
2. 이를 $U$ 와 같다고 두고 $X$ 에 대해 방정식을 풉니다.
   $$U = 1 - e^{-\lambda x}$$
   $$e^{-\lambda x} = 1 - U$$
   $$-\lambda x = \ln(1 - U)$$
3. 최종적으로 도출된 역변환 생성 공식은 다음과 같습니다.
   $$X = -\frac{1}{\lambda} \ln(1 - U)$$

**결론:** 컴퓨터 프로그램에서 0과 1 사이의 난수 $U$를 10,000번 생성한 뒤, 위 공식의 $U$ 자리에 각각 대입하기만 하면 완벽한 지수 분포 형태를 띠는 10,000개의 데이터 셋(히스토그램)을 순식간에 얻을 수 있습니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="1-11 Inverse Transform Theorem-1" src="https://github.com/user-attachments/assets/3a8fe5ad-b391-44f3-9471-96c85ca7fb7c" />
    <img width="1264" height="1635" alt="1-11 Inverse Transform Theorem-2" src="https://github.com/user-attachments/assets/0ae6dfe4-5854-41e2-a23f-44f7987b1e95" />
  </div>
</details>
