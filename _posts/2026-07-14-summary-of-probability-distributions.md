---
title: "Summary of Probability Distributions"
date: 2026-07-14 22:07:00 +0900
categories: ["GTx Statistics, Confidence Intervals and Hypothesis Tests", "Probability and Statistics III: A Gentle Introduction to Statistics"]
tags: [probability, statistics, discrete-distribution, continuous-distribution, pmf, pdf, mgf]
math: true
---
이번 글은 GTx의 과정은 아니지만 이 카테고리에 올립니다. 확률과 통계를 공부하며, 분포를 정리해보았습니다.

## 1. 이산형 확률 분포 (Discrete Distributions)

**[KR]** 결과가 정수 단위로 떨어지는 이산형 확률 변수를 모델링하는 대표적인 분포들입니다.

| 분포 이름 (표기법) | 확률 질량 함수 (PMF, $P(X=k)$) | 기댓값 ($E[X]$) | 분산 ($V(X)$) | 적률 생성 함수 ($M_X(t)$) |
| :--- | :--- | :--- | :--- | :--- |
| **베르누이 (Bern(p))** | $p^k q^{1-k}$ | $p$ | $pq$ | $pe^t + q$ |
| **이항 (Bin(n, p))** | $\binom{n}{k} p^k q^{n-k}$ | $np$ | $npq$ | $(pe^t + q)^n$ |
| **기하 (Geom(p))** | $q^{k-1}p$ | $1/p$ | $q/p^2$ | $\frac{pe^t}{1-qe^t}$ |
| **음이항 (Neg Bin(r, p))** | $\binom{k-1}{r-1}p^r q^{k-r}$ | $r/p$ | $rq/p^2$ | $\left(\frac{pe^t}{1-qe^t}\right)^r$ |
| **푸아송 (Pois($\lambda$))** | $\frac{e^{-\lambda} \lambda^k}{k!}$ | $\lambda$ | $\lambda$ | $e^{\lambda(e^t - 1)}$ |
| **초기하 (Hypergeometric)** | $\frac{\binom{a}{k}\binom{b}{n-k}}{\binom{a+b}{n}}$ | $n\left(\frac{a}{a+b}\right)$ | $n\left(\frac{a}{a+b}\right)\left(1-\frac{a}{a+b}\right)\left(\frac{a+b-n}{a+b-1}\right)$ | 없음 |

* **베르누이 분포:** 결과가 성공 아니면 실패, 단 두 가지만 존재하는 실험을 딱 한 번 수행했을 때의 분포입니다.
* **이항 분포:** 성공 확률이 $p$인 베르누이 시행을 독립적으로 $n$번 반복했을 때의 총 '성공 횟수'를 나타냅니다. 각각의 독립적인 베르누이 시행의 합으로 볼 수 있습니다.
* **기하 분포:** 성공 확률이 $p$인 시행을 반복할 때, '첫 번째 성공'이 나올 때까지 걸린 총 시행 횟수의 분포입니다.
* **음이항 분포:** 원하는 성공 횟수 $r$번을 채울 때까지 총 몇 번의 시도를 해야 하는지 모델링합니다. 마지막 $k$번째 시행은 무조건 성공($p$)으로 끝나야 합니다.
* **푸아송 분포:** 정해진 단위 시간이나 공간 내에서 평균적으로 $\lambda$번 발생하는 사건이 정확히 $k$번 일어날 확률을 나타냅니다. 이항 분포에 극한을 취하여 도출할 수 있습니다.
* **초기하 분포:** 공의 개수가 고정된 주머니에서 샘플을 '비복원 추출'로 무작위로 뽑을 때, 특정 공이 몇 개나 섞여 나올지를 계산합니다.

---

## 2. 연속형 확률 분포 (Continuous Distributions)

**[KR]** 데이터가 소수점 아래 무한히 연속적인 값을 가질 수 있는 경우를 모델링하는 분포들입니다.

| 분포 이름 (표기법) | 확률 밀도 함수 (PDF, $f(x)$) | 기댓값 ($E[X]$) | 분산 ($V(X)$) | 적률 생성 함수 ($M_X(t)$) |
| :--- | :--- | :--- | :--- | :--- |
| **균일 (Unif(a, b))** | $\frac{1}{b-a}$ | $\frac{a+b}{2}$ | $\frac{(b-a)^2}{12}$ | $\frac{e^{tb}-e^{ta}}{t(b-a)}$ |
| **지수 (Exp($\lambda$))** | $\lambda e^{-\lambda x}$ | $1/\lambda$ | $1/\lambda^2$ | $\frac{\lambda}{\lambda - t}$ |
| **얼랑 (Erlang($k, \lambda$))** | $\frac{\lambda^k e^{-\lambda x} x^{k-1}}{(k-1)!}$ | $k/\lambda$ | $k/\lambda^2$ | $\left(\frac{\lambda}{\lambda - t}\right)^k$ |
| **감마 (Gamma($\alpha, \lambda$))**| $\frac{\lambda^\alpha e^{-\lambda x} x^{\alpha-1}}{\Gamma(\alpha)}$ | $\alpha/\lambda$ | $\alpha/\lambda^2$ | $\left(\frac{\lambda}{\lambda - t}\right)^\alpha$ |
| **베타 (Beta($a, b$))** | $\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)} x^{a-1}(1-x)^{b-1}$| $\frac{a}{a+b}$ | $\frac{ab}{(a+b)^2(a+b+1)}$ | 닫힌 형태 없음 |
| **와이블 (Weibull($\alpha, \beta$))**| $\alpha\beta(\alpha x)^{\beta-1} e^{-(\alpha x)^\beta}$ | $\frac{1}{\alpha}\Gamma\left(1+\frac{1}{\beta}\right)$ | 복잡한 형태 | 닫힌 형태 없음 |
| **정규 ($N(\mu, \sigma^2)$)** | $\frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$ | $\mu$ | $\sigma^2$ | $e^{\mu t + \frac{1}{2}\sigma^2 t^2}$ |

* **균일 분포:** 특정 구간 $[a, b]$ 안에서 모든 값의 발생 확률(밀도)이 동일한 분포입니다.
* **지수 분포:** 평균적으로 단위 시간당 $\lambda$번 발생하는 사건이 있을 때, '첫 번째 사건이 일어날 때까지 걸린 대기 시간'을 나타냅니다.
* **얼랑 분포:** 원하는 사건이 정확히 $k$번 터질 때까지 걸리는 대기 시간을 모델링하며, 독립적인 지수 분포를 $k$개 더한 것과 같습니다. (단, $k$는 양의 정수입니다.)
* **감마 분포:** 얼랑 분포의 파라미터 $k$를 감마 함수($\Gamma$)를 이용하여 실수 $\alpha$의 영역으로 확장한 일반화된 분포입니다.
* **베타 분포:** $0$과 $1$ 사이의 값만 가지므로 확률 그 자체를 확률 변수로 다룰 때 매우 유용합니다. 두 개의 모양 매개변수 $a, b$에 의해 형태가 유연하게 변합니다.
* **와이블 분포:** 고장률이 일정한 지수 분포의 비현실적인 가정을 극복하기 위해 만들어진 분포로, 부품이 마모되어 시간이 지날수록 고장률이 오르거나($\beta > 1$) 안정화되어 낮아지는($\beta < 1$) 상황을 반영합니다.
* **정규 분포:** 가장 정상적이고 일반적인 데이터 흐름을 나타내는 종 모양의 대칭 분포입니다. 평균이 0이고 분산이 1인 경우를 특별히 표준 정규 분포라고 부릅니다.

<br>

---

<details>
  <summary style="cursor: pointer; font-weight: bold; color: #0076ff; user-select: none;">📝 Jhin의 원본 손필기 노트 보기 / View Original Handwritten Notes (Click)</summary>
  <div style="display: flex; justify-content: center; margin-top: 15px;">
    <img width="1264" height="1635" alt="Summary of Probability Distributions-01" src="https://github.com/user-attachments/assets/d580a115-ddce-4a34-a21d-5f0cad53a3f9" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-02" src="https://github.com/user-attachments/assets/bb9d010a-5901-4c66-b29d-1e6c24cfe488" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-03" src="https://github.com/user-attachments/assets/20622cfd-1ea7-420d-9ef5-549337e40fa2" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-04" src="https://github.com/user-attachments/assets/0270eff5-c19f-4d55-acb1-7203c37ddbe7" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-05" src="https://github.com/user-attachments/assets/3e73f06d-6d96-45a5-98c9-6c82f08ce8f6" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-06" src="https://github.com/user-attachments/assets/0547b82b-b7f1-4186-b821-653534868db5" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-07" src="https://github.com/user-attachments/assets/543f2745-f06d-467e-937b-de078fa2a8c0" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-08" src="https://github.com/user-attachments/assets/ac07ea46-6d8c-49c7-9ae6-85e760407509" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-09" src="https://github.com/user-attachments/assets/297acb6c-7ab2-4130-a138-476019e0c2ce" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-10" src="https://github.com/user-attachments/assets/b1e86b57-d9db-4556-b2af-e87815015f06" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-11" src="https://github.com/user-attachments/assets/07bb2733-8ce0-4edc-bddf-c93cdafdd6e4" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-12" src="https://github.com/user-attachments/assets/d75c7781-1cce-46d0-a56d-8f7fb3a8447e" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-13" src="https://github.com/user-attachments/assets/cc6d66ce-5831-466d-ad39-356b5e254797" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-14" src="https://github.com/user-attachments/assets/69e2fe14-772a-4e71-a132-b85b3f96bedc" />
    <img width="1264" height="1635" alt="Summary of Probability Distributions-15" src="https://github.com/user-attachments/assets/77051245-01e2-4ab7-a9a1-ffe2a0b7b99b" />
  </div>
</details>
