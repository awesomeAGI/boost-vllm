---
description: 'Author: 윤건우'
---

# Codes

**CLIP은** 이미지와 텍스트를 <mark style="background-color:yellow;">동일한 벡터 공간 (vector space)에서 비교</mark>할 수 있도록 <mark style="background-color:yellow;">임베딩을 생성하는 모델</mark>입니다. 이를 통해 **이미지와 텍스트 간의 직접적인 비교가 가능**합니다.

CLIP 및 유사 모델 (similar models)은 이미지와 텍스트 임베딩을 동일한 벡터 공간에서 비교할 수 있어 다음과 같은 작업을 수행할 수 있습니다:

1. **제로샷 분류 (Zeroshot classification)**: 이미지 임베딩과 클래스 설명을 비교하여 가장 가까운 클래스를 식별할 수 있습니다.
2. **클러스터링 (Clustering)**: 이미지와 키워드 (keywords)를 그룹화하여 관련된 집합을 찾을 수 있습니다.
3. **검색 (Search)**: 대규모 데이터 세트에서 관련된 텍스트나 이미지를 빠르게 찾을 수 있습니다.
4. **생성 (Generation)**: 멀티모달 임베딩을 사용하여 이미지를 생성할 수 있습니다 (_e.g._, stable diffusion).

## 실습: Connecting Text and Images&#x20;

{% code lineNumbers="true" %}
```bash
!wget -O swan_and_duck.png https://as1.ftcdn.net/v2/jpg/03/19/39/26/1000_F_319392607_iGQGIxm6Uydj0R3rWJXNuqJtd24LqkJP.jpg
!wget -O chickens.png https://as1.ftcdn.net/v2/jpg/04/01/75/08/1000_F_401750896_7TNLyhRdBo3KT5pHe78S8YoQKXLo7zJ5.jpg
!wget -O birds_flying.png https://t3.ftcdn.net/jpg/02/10/17/32/240_F_210173237_39JkhlPSEfkl4WhLNgirxLPX2nO2HgLB.jpg
```
{% endcode %}

{% code title="Load inputs " lineNumbers="true" %}
```python
import numpy as np
from PIL import Image

# -- Load images
img_list = ['./swan_and_duck.png',
            './chickens.png',
            './birds_flying.png']
images = [Image.open(path).resize((512, 512)) for path in img_list]

# -- Captions
captions = ["There are many swans and ducks",
            "Chickens playing on the ground",
            "A pair of birds flying in the sky"]
```
{% endcode %}

```bash
!pip install transformers==4.41.2
```

{% code title="OpenCLIP" lineNumbers="true" fullWidth="false" %}
```python
from transformers import CLIPTokenizerFast, CLIPProcessor, CLIPModel

model_id = "openai/clip-vit-base-patch32"

# -- Load a tokenizer to preprocess the 'text'
tokenizer = CLIPTokenizerFast.from_pretrained(model_id)

# -- Load a processor to preprocess the 'images'
processor = CLIPProcessor.from_pretrained(model_id)

# -- Main model for generating 'text and image embeddings'
model = CLIPModel.from_pretrained(model_id)
```
{% endcode %}

OpenCLIP을 사용하여 <mark style="background-color:orange;">이미지와  이미지 캡션의 임베딩을 생성</mark>하려면 **세 가지 모델**이 필요합니다:

* 텍스트를 위한 토크나이저 (tokenizer)
* 이미지를 위한 전처리기
* 처리된 입력을 임베딩으로 변환하는 메인 모델&#x20;

{% code title="Tokenizer" lineNumbers="true" %}
```python
# -- Tokenize the caption about the input
inputs = tokenizer(captions, padding=True, truncation=True, return_tensors="pt")
```
{% endcode %}

캡션을&#x20;

캡션이 전처리되었으면 다음 단계에서 임베딩을 생성합니다.

{% code title="Text embedding" lineNumbers="true" %}
```python
# -- Create a text embedding
text_embedding = model.get_text_features(**inputs)
```
{% endcode %}

이미지 임베딩을 생성하기 전에, <mark style="background-color:yellow;">모델이 요구하는 크기와 형태에 맞추기 위해</mark> 이전에 생성한 전처리기를 사용하여 이미지를 전처리해야 합니다.

{% code title="Preprocessing image " lineNumbers="true" %}
```python
# -- image preprocessing 
processed_image = processor(text=None, images=image, return_tensors='pt')['pixel_values']
print(processed_image.shape) # (B,3,224,224) 
```
{% endcode %}

전처리 과정에서 원본 이미지는 모델의 입력 요구사항을 충족시키기 위해 224x224 픽셀로 크기가 조정됩니다.

{% code title="Image embedding" lineNumbers="true" %}
```python
# -- Create a image embedding
image_embedding = model.get_image_features(processed_image)
print(image_embedding.shape)
```
{% endcode %}

전처리된 이미지를 임베딩으로 변환합니다. <mark style="background-color:yellow;">생성된 이미지 임베딩은 텍스트 임베딩과 동일한 형태를 가지므로</mark> **직접 비교가 가능**합니다.

{% code title="Calculating the similarity" lineNumbers="true" %}
```python
# -- Normalize the embeddings
text_embedding /= text_embedding.norm(dim=-1, keepdim=True)
image_embedding /= image_embedding.norm(dim=-1, keepdim=True)

# -- Calculate their similarity
text_embedding = text_embedding.detach().cpu().numpy()
image_embedding = image_embedding.detach().cpu().numpy()

score = np.dot(text_embedding, image_embedding.T)
print(score)
```
{% endcode %}

유사성 (similarity)을 더 분석하기 위해 **임베딩을 정규화**한 후 **점곱(dot product)**을 통해 코사인 유사도(cosine similarity)를 계산하면 0과 1 사이의 값을 얻을 수 있습니다.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Similarity scores between images and texts</p></figcaption></figure>

## Reference

1. Radford, A., Kim, J., Hallacy, C., Ramesh, A., Goh, G., Agarwal, S., Sastry, G., Askell, A., Mishkin, P., Clark, J., & others (2021). Learning transferable visual models from natural language supervision. In International conference on machine learning (pp. 8748–8763)
2. [Hands on Large Language Models](https://learning.oreilly.com/library/view/hands-on-large-language/9781098150952/ch05.html#transformers\_for\_vision), 2024.
