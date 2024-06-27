# Codes

**CLIP은** 이미지와 텍스트를 <mark style="background-color:orange;">동일한 벡터 공간 (vector space)에서 비교</mark>할 수 있도록 <mark style="background-color:orange;">임베딩을 생성하는 모델</mark>입니다. 이를 통해 **이미지와 텍스트 간의 직접적인 비교가 가능**합니다.

CLIP 및 유사 모델 (similar models)은 이미지와 텍스트 임베딩을 동일한 벡터 공간에서 비교할 수 있어 다음과 같은 작업을 수행할 수 있습니다:

1. **제로샷 분류 (Zeroshot classification)**: 이미지 임베딩과 클래스 설명을 비교하여 가장 가까운 클래스를 식별할 수 있습니다.
2. **클러스터링 (Clustering)**: 이미지와 키워드 (keywords)를 그룹화하여 관련된 집합을 찾을 수 있습니다.
3. **검색 (Search)**: 대규모 데이터 세트에서 관련된 텍스트나 이미지를 빠르게 찾을 수 있습니다.
4. **생성 (Generation)**: 멀티모달 임베딩을 사용하여 이미지를 생성할 수 있습니다 (_e.g._, stable diffusion).

## 실습: Connecting Text and Images&#x20;

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







## Reference

1. Radford, A., Kim, J., Hallacy, C., Ramesh, A., Goh, G., Agarwal, S., Sastry, G., Askell, A., Mishkin, P., Clark, J., & others (2021). Learning transferable visual models from natural language supervision. In International conference on machine learning (pp. 8748–8763)
2. [Hands on Large Language Models](https://learning.oreilly.com/library/view/hands-on-large-language/9781098150952/ch05.html#transformers\_for\_vision), 2024.
