# Codes

CLIP은 이미지와 텍스트를 <mark style="background-color:yellow;">동일한 벡터 공간 (vector space)에서 비교</mark>할 수 있도록 임베딩을 생성하는 모델입니다. 이를 통해 이미지와 텍스트 간의 직접적인 비교가 가능합니다.

CLIP 및 유사 모델 (similar models)은 이미지와 텍스트 임베딩을 동일한 벡터 공간에서 비교할 수 있어 다음과 같은 작업을 수행할 수 있습니다:

1. **제로샷 분류 (Zeroshot classification)**: 이미지 임베딩과 클래스 설명을 비교하여 가장 가까운 클래스를 식별할 수 있습니다.
2. **클러스터링 (Clustering)**: 이미지와 키워드 (keywords)를 그룹화하여 관련된 집합을 찾을 수 있습니다.
3. **검색 (Search)**: 대규모 데이터 세트에서 관련된 텍스트나 이미지를 빠르게 찾을 수 있습니다.
4. **생성 (Generation)**: 멀티모달 임베딩을 사용하여 이미지를 생성할 수 있습니다 (_e.g._, stable diffusion).
