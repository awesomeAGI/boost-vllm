---
description: 'Author: 윤건우'
---

# History of early models (2010 - 2017)

## Cross-modal "Visual-Semantic Embeddings"

'크로스모달'은 서로 **다른 형태의 데이터**(예: 이미지와 텍스트)를 **결합**하여 **의미 있는 임베딩을 생성**하는 것을 의미합니다.

**(1) WSABI (Weston et al 2010)**

초기 크로스모달 임베딩 연구 중 하나로, <mark style="background-color:yellow;">이미지와 텍스트 데이터를 결합하여 더 나은 의미를 도출하려는 시도</mark>입니다.

**(2) DeViSE (Frome et al 2013)**

**Deep Visual Semantic Embedding Model**: 전통적인 시각 모델을 발전시킨 형태로, <mark style="background-color:yellow;">이미지와 레이블 간의 임베딩 벡터를 사용하여 유사성을 측정</mark>합니다.&#x20;

**(3) Cross-Modal Transfer (Socher et al 2013)**

크로스모달 전이 기술을 통해 <mark style="background-color:yellow;">새로운 클래스의 이미지를 이해하고 분류</mark>할 수 있습니다. 예를 들어, 트럭, 자동차, 개 등의 이미지를 학습한 모델이 새로운 클래스(예: 고양이)의 이미지를 처리할 수 있습니다.

### [Multimodal distributional semantics](https://www.jair.org/index.php/jair/article/view/10857) (멀티모달 분포 의미론)

Bruni et al. (2014) \[1]의 연구는 **이미지와 텍스트 데이터를 결합**하여 **단어의 의미를 더 잘 표현할 수 있는 방법을 제안**했습니다. 이는 멀티모달 데이터의 결합을 통해 **AI의 의미 이해를 능력을 어떻게 향상시킬 수 있는지**를 잘 보여줍니다.&#x20;

알고리즘의 중요 단계는 다음과 같습니다:

step 1) Obtain visual "word vector" via BoVW:&#x20;

1. Identify keypoints and get their descriptors **(주요 지점 식별 및 기술자 획득)**: 이미지에서 주요 지점을 식별하고, 각 지점의 기술자를 획득합니다. 이는 이미지의 특징을 잘 나타내는 정보입니다.
2. Cluster them and map to counts **(클러스터링하고 카운트로 매핑)**: 식별된 기술자들을 클러스터링하고, 각 클러스터를 빈도로 변환합니다. 이를 통해 이미지 내의 중요한 요소들을 요약합니다.

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-02 17-01-46.png" alt="" width="375"><figcaption><p>Representing images by bag of visual words (BoVW).</p></figcaption></figure>

step 2) Concatenate with textual word vector:&#x20;

1. <mark style="background-color:yellow;">시각적 단어 벡터와 텍스트 단어 벡터를 결합</mark>하여, **단어의 의미를 더 풍부하게 표현**합니다. 예를 들어, "달"이라는 단어를 표현할 때, 달의 이미지를 기반으로 한 시각적 정보와 함께 텍스트 정보를 결합합니다.

step 3) Apply SVD to "fuse" information:

1. <mark style="background-color:yellow;">결합된 정보를 단일화된 벡터로 만들기</mark> 위해 특이값 분해(SVD)를 적용합니다. 이를 통해 다양한 형태의 데이터를 효과적으로 결합할 수 있습니다.

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-03 14-14-26.png" alt="" width="375"><figcaption><p>Multimodal fusion for combining textual and visual information in a semanticmodel.</p></figcaption></figure>

### Neural network versions for multimodal fusion&#x20;

Kiela, D., et al. (2014) \[2]의&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-03 14-20-48.png" alt="" width="563"><figcaption><p>Computing word feature vectors.</p></figcaption></figure>



Lazaridou, A., et al. (2015) \[3]의&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-03 14-27-30.png" alt="" width="563"><figcaption><p>Lin- guistic context vectors are actually associated to classes of words in a tree, not single words.</p></figcaption></figure>

## Beyond words: Sentence level alignment for image descriptions

단어(words)가 모이면 문장(sentence)이 됩니다.&#x20;



### Grounded Compositional Semantics&#x20;

Socher, R., et al., (2014) \[5]

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-03 14-49-28.png" alt=""><figcaption><p>The DT-RNN learns vector representations for sentences based on their dependency trees.</p></figcaption></figure>

### Visual-Semantic Embedding

Kiros, R., et al. (2014) \[6]

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-03 14-52-37.png" alt=""><figcaption><p><strong>Encoder</strong>: A deep convolutional network (CNN) and long short-term memory recurrent network (LSTM) for learning a joint image-sentence embedding. <strong>Decoder</strong>: A new neural language model that combines structure and content vectors for generating words one at a time in sequence.</p></figcaption></figure>

### Visual-Semantic Alignments

Karpathy, A., et al. (2015) \[4]

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-03 14-35-37.png" alt="" width="563"><figcaption><p>Diagram for evaluating the image-sentence score  . Object regions are embedded with a CNN (left). Words (enriched by their context) are embedded in the same multimodal space with a BRNN (right). Pairwise similarities are computed with inner products (magnitudes shown in grayscale) and finally reduced to image-sentence score.</p></figcaption></figure>

### Grounded Sentence Representations

Kiela, D., et al. (2017) \[7]

<figure><img src="../../../.gitbook/assets/Screenshot from 2024-07-03 14-59-36.png" alt=""><figcaption><p><strong>Model architecture</strong>: predicting either an image (Cap2Img), an alternative caption (Cap2Cap), or both at the same time (Cap2Both).</p></figcaption></figure>





## Reference&#x20;

1. [Bruni, E., Tran, N. K., & Baroni, M. (2014). Multimodal distributional semantics. _Journal of artificial intelligence research_, _49_, 1-47](https://www.jair.org/index.php/jair/article/view/10857/25905).
2. Kiela, D., & Bottou, L. (2014, October). [Learning image embeddings using convolutional neural networks for improved multi-modal semantics.](https://aclanthology.org/D14-1005.pdf) In _Proceedings of the 2014 Conference on empirical methods in natural language processing (EMNLP)_ (pp. 36-45).
3. Lazaridou, A., Pham, N. T., & Baroni, M. (2015). [Combining language and vision with a multimodal skip-gram model](https://arxiv.org/abs/1501.02598). _arXiv preprint arXiv:1501.02598_.
4. Karpathy, A., & Fei-Fei, L. (2015). [Deep visual-semantic alignments for generating image descriptions](https://www.cv-foundation.org/openaccess/content\_cvpr\_2015/html/Karpathy\_Deep\_Visual-Semantic\_Alignments\_2015\_CVPR\_paper.html). In _Proceedings of the IEEE conference on computer vision and pattern recognition_ (pp. 3128-3137).
5. Socher, R., Karpathy, A., Le, Q. V., Manning, C. D., & Ng, A. Y. (2014). [Grounded compositional semantics for finding and describing images with sentences](https://direct.mit.edu/tacl/article/doi/10.1162/tacl\_a\_00177/43306/Grounded-Compositional-Semantics-for-Finding-and). _Transactions of the Association for Computational Linguistics_, _2_, 207-218.
6. Kiros, R., Salakhutdinov, R., & Zemel, R. S. (2014). [Unifying visual-semantic embeddings with multimodal neural language models](https://arxiv.org/abs/1411.2539). _arXiv preprint arXiv:1411.2539_.
7. Kiela, D., Conneau, A., Jabri, A., & Nickel, M. (2017). [Learning visually grounded sentence representations](https://arxiv.org/abs/1707.06320). _arXiv preprint arXiv:1707.06320_.

