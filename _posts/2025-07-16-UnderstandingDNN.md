---
title: "Understanding Deep Neural Network 정리"
date: 2025-07-16 23:00:00 +0900
categories: [UnderstaindingDNN, Introduction] # 대분류 (사이드바에 표시됨)
tags: [Understanding Deeplearning Neural Network, math, 딥러닝, DNN, Deeplearning, Deep neural network]     # 소분류 (태그 검색에 사용됨)
pin: true                            # 이 포스트를 메인 페이지에 고정
math: true                           # 이 포스트에서 수식(MathJax)을 사용
toc: true                            # 이 포스트에서 목차를 사용
# image: /assets/img/sample.png      # 썸네일 이미지 (선택 사항)
---
# Introduction

- AI는 지능적 행동을 모방하는 시스템 세울 때 고려됨.
- Machine learning 은 관측 데이터를 수학적 모델링해서 Fitting 하는, AI의 하위 집합
- 지금 ML은 폭발적으로 성장해서 "AI"와 거의 유사한 동의어가 됨. (잘못된 인식임)

- DNN은 머신러닝 모델 중 하나이고, 데이터를 모델에 맞추는 과정을 Deep learning 이라고 한다.
- 현시점에서 DNN은 가장 강력하고 현실적인 머신러닝 모델이며, 자주 볼 수 있다.
- 언어를 다른 언어로 번역하거나(NLP), 객체에 대한 이미지를 찾거나(CV), 디지털 조수를 두거나(Speech Recognition) 등의 분야에 공통적으로 쓰이고, 이러한 기능들은 DNN을 통한 power가 있다.
- 해당 책은 이해를 돕기 위한 책. 증명과 코드가 거의 없음. 기존 해답이 없는 곳에 딥러닝 적용이 목표 
- ML은 대략적으로 Supervised, Un-supervised, Reinforcement learning으로 제공됨.
- 각 분류에 대해 다루며, AI 윤리에 대한 간단한 입문서도 포함.

## 1-1 Supervised Learning

Supervised learning: a mapping from input data to an output prediction.

![[Pasted image 20250717000156.png]]
Figure 1.1 - Area of Artificial intelligence

### 1. Regression and Classification problems
