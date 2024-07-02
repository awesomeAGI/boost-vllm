---
description: 'Author: 윤건우'
---

# History of early models (2010 - 2016)

## Cross-modal "Visual-Semantic Embeddings"

'크로스모달'은 서로 **다른 형태의 데이터**(예: 이미지와 텍스트)를 **결합**하여 **의미 있는 임베딩을 생성**하는 것을 의미합니다.

**(1) WSABI (Weston et al 2010)**

초기 크로스모달 임베딩 연구 중 하나로, <mark style="background-color:yellow;">이미지와 텍스트 데이터를 결합하여 더 나은 의미를 도출하려는 시도</mark>입니다.

**(2) DeViSE (Frome et al 2013)**

**Deep Visual Semantic Embedding Model**: 전통적인 시각 모델을 발전시킨 형태로, <mark style="background-color:yellow;">이미지와 레이블 간의 임베딩 벡터를 사용하여 유사성을 측정</mark>합니다.&#x20;

**(3) Cross-Modal Transfer (Socher et al 2013)**

크로스모달 전이 기술을 통해 <mark style="background-color:yellow;">새로운 클래스의 이미지를 이해하고 분류</mark>할 수 있습니다. 예를 들어, 트럭, 자동차, 개 등의 이미지를 학습한 모델이 새로운 클래스(예: 고양이)의 이미지를 처리할 수 있습니다.

## Multimodal distributional semantics (멀티모달 분포 의미론)

Bruni et al. (2014)의 연구는 **이미지와 텍스트 데이터를 결합**하여 **단어의 의미를 더 잘 표현할 수 있는 방법을 제안**했습니다. 이는 멀티모달 데이터의 결합을 통해 **AI의 의미 이해를 능력을 어떻게 향상시킬 수 있는지**를 잘 보여줍니다.&#x20;

알고리즘의 중요 단계는 다음과 같습니다:

step 1) Obtain visual "word vector" via BOVW:&#x20;

1. Identify keypoints and get their descriptors **(주요 지점 식별 및 기술자 획득)**: 이미지에서 주요 지점을 식별하고, 각 지점의 기술자를 획득합니다. 이는 이미지의 특징을 잘 나타내는 정보입니다.
2. Cluster them and map to counts **(클러스터링하고 카운트로 매핑)**: 식별된 기술자들을 클러스터링하고, 각 클러스터를 빈도로 변환합니다. 이를 통해 이미지 내의 중요한 요소들을 요약합니다.

step 2) Concatenate with textual word vector:&#x20;

1. <mark style="background-color:yellow;">시각적 단어 벡터와 텍스트 단어 벡터를 결합</mark>하여, **단어의 의미를 더 풍부하게 표현**합니다. 예를 들어, "달"이라는 단어를 표현할 때, 달의 이미지를 기반으로 한 시각적 정보와 함께 텍스트 정보를 결합합니다.

step 3) Apply SVD to "fuse" information:

1. <mark style="background-color:yellow;">결합된 정보를 단일화된 벡터로 만들기</mark> 위해 특이값 분해(SVD)를 적용합니다. 이를 통해 다양한 형태의 데이터를 효과적으로 결합할 수 있습니다.







