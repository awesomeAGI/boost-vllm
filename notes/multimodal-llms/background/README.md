---
description: 'Author: 윤건우'
---

# Background

## What is multimodality?

multi + modal&#x20;

* **Multi-**: 라틴어에서 유래한 접두사, **"많은"** 또는 **"다수의"**를 의미합니다. 예를 들어, multilingual(다중 언어의)에서 사용된 "multi-"는 "다중"을 의미합니다
* **Modality**: 영어의 "mode"에서 유래했으며, 이것은 **"방법"** 또는 **"형태"**를 의미합니다. "Modality"는 "mode"에 "ity"를 붙여 명사형으로 만든 단어로, "다양한 방법" 또는 "형태"라는 의미를 내포합니다.

즉, **멀티모달리티**는 단일 형태의 정보 전달 방식에서 벗어나 **다양한 형태의 정보 전달 방식을 의미**합니다. 예를 들어, 교실에서 수업을 할 때 텍스트 책, 사진, 동영상, 소리 등을 모두 활용하는 것이 멀티모달리티의 한 예입니다.



멀티모달리티의 예:

* **교육**: 교사가 수업에서 텍스트, 이미지, 동영상, 음성 등을 모두 활용하여 학생들에게 내용을 전달하는 경우.
* **커뮤니케이션**: 사람들이 말, 몸짓, 표정, 그림 등을 모두 사용하여 의사소통하는 경우.
* **인공지능**: AI 시스템이 텍스트, 이미지, 소리 등의 여러 가지 데이터를 동시에 처리하여 더 정확한 결과를 도출하는 경우.

멀티모달리티의 중요성:

* **현실성 (Faithfulness)**:  **인간의 경험은 본질적으로 멀티모달**입니다. 다양한 감각  모드의 결합 (_e.g._, 인간의  오감)은 정보를 더 풍부하고 효과적으로 전달할 수 있게 해줍니다. AI 연구에서는 <mark style="background-color:yellow;">사람처럼 다양한 형태의 정보를 동시에 처리하고 이해할 수 있게 하여,</mark> 더 자연스러운 상호작용, 더 정확한 이해와 예측, 다양한 데이터 소스의 통합, 강화된 학습 능력, 혁신적인 응용 분야 등을 가능하게 합니다
* **실용성 (Practicality)**: 인터넷과 현대 애플리케이션은 텍스트, 이미지, 비디오 등 멀티모달 데이터를 다룹니다. AI가 이러한 환경에서 제대로 기능하려면 다양한 형태의 데이터를 이해하고 처리할 수 있는 능력이 필수적입니다.
* **데이터 효율성과 가용성 (Data Efficiency and Availablity)**:&#x20;
  * _Efficiency:_ 멀티모달 데이터는 풍부하고 "고대역폭 (high bandwidth)" 데이터입니다. 이는 <mark style="background-color:yellow;">텍스트 데이터보다 더 많은 정보를 담고 있어 학습과 예측에 유리</mark>합니다. 예를 들어, Yann LeCun은 언어를 "내부 데이터 구조를 불완전하게 직렬화한 것 (an imperfect, imcomplete, and low-bandwidth serialization protocol for the internal data structures)"이라고 표현하면서, 멀티모달 데이터가 학습에 더 적합하다고 설명합니다.
  * _Scaling:_ 더 많은 데이터가 더 나은 결과를 낳습니다. 고품질 텍스트 데이터가 부족해지고 있는 상황에서, 멀티모달 데이터는 AI 학습을 위한 새로운 고품질 데이터 소스로 작용할 수 있습니다.

> Multimodality is one of the main frontiers of the new foundation model revolution.

## Multimodal brains&#x20;

맥거크 효과 - [McGurk effect](https://youtu.be/jtsfidRq2tw?si=zw3cWPCit\_6aMjgA) (McGurk & MacDonald, 1976)

* 동일한 발음이 말소리를 내는 사람의 입 모양에 따라 다르게 들리는 현상.

<figure><img src="../../../.gitbook/assets/17e0473ec7c307f65-ezgif.com-video-to-gif-converter.gif" alt=""><figcaption><p>ㅇ모래반지 빵야빵야 모래반지 빵야빵야 </p></figcaption></figure>

* 모래반지 빵야빵야&#x20;
* 머리 만지지 말란 말이야&#x20;
* 뭘 마실지 빨리 말해&#x20;
* 뭘봐 이 xx럼아&#x20;



본 포스팅에서는 가장 많이 연구되는 <mark style="background-color:yellow;">NLP 중심의 multimodality를 정리합니다</mark>.

* 즉, <mark style="background-color:yellow;">**text +**</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">one or more other modalities</mark> (e.g., images, speech, audio, olfaction, etc.)

## Outline&#x20;

1. History of early models (2010 - 2016)
2. Features and fusion&#x20;
3. Contrastive models&#x20;
4. Multimodal foundation models&#x20;
5. Evaluation
6. Beyond images: Other modalities&#x20;
7. Where to next?

## Reference

* [Stanford CS224N NLP with Deep Learning | 2023 | Lecture 16 - Multimodal Deep Learning](https://youtu.be/5vfIT5LOkR0?si=rZc\_I4UYBOHQlQ7C), Douwe Kiela, Stanford Online Youtube. --- ([한국어 자막](https://youtu.be/FV0TtqoT7dE?si=fLiMhOSzGZmQb6LM)).
* [한땀한땀 딥러닝 컴퓨터 비전 백과사전](https://wikidocs.net/149482).
