---
Date Added: 2025-09-01
tags:
  - embeddingretrieval
  - LIMITdataset
status:
source: https://arxiv.org/abs/2508.21038
created: 2025-09-01
channel name: 게시판
Length: 1587자
Month: 09
Quarter: Q3-2025
Rating:
---
> [!요약정보]
> 이 논문은 임베딩 기반 검색의 이론적 한계를 분석하고, 특히 단일 벡터 임베딩 패러다임이 가지는 근본적인 제약에 주목한다. 연구의 주요 내용은 다음과 같다.
> 
> - 임베딩 차원이 top-k 검색 결과로 반환될 수 있는 문서 집합의 수를 제한한다는 것을 이론적으로 증명한다. 즉, 임베딩 차원이 작으면 다양한 검색 요구를 충족시키기 어렵다.
> - k=2인 경우에도 이러한 제한이 발생함을 실험적으로 보인다. 이는 최적화를 통해 임베딩을 조정하더라도 이론적 한계를 극복하기 어렵다는 것을 의미한다.
> - 실제적인 시나리오를 반영한 LIMIT 데이터셋을 구축하여 최첨단 모델들을 평가한 결과, 간단한 질의에 대해서도 모델들이 실패하는 것을 확인한다.
> - 기존 연구에서는 임베딩의 한계가 비현실적인 질의 때문이라고 가정했지만, 본 연구는 간단하고 현실적인 질의에서도 이론적 한계가 나타날 수 있음을 보여준다.
> - 연구 결과는 현재의 단일 벡터 임베딩 방식의 한계를 지적하고, 이러한 근본적인 제한을 해결할 수 있는 새로운 방법론의 필요성을 강조한다.
> 
##### AI Summary
**On the Theoretical Limitations of Embedding-Based Retrieval**
- 이 논문은 단일 벡터 임베딩 패러다임의 근본적 한계를 실증한다. 임베딩 차원에 의해 top-k로 반환될 수 있는 문서집합 수가 제한되며, k=2 실험과 LIMIT 데이터셋에서 최첨단 모델들도 간단한 질의에서 실패함을 보인다.
- 핵심포인트: 임베딩 차원은 반환 가능한 top-k 조합 수를 제한함
- 핵심포인트: 현실적이고 단순한 질의에서도 이론적 한계가 관찰됨
- 핵심포인트: LIMIT 데이터셋에서 SOTA 모델 실패 확인

---
##### Contents
[Submitted on 28 Aug 2025]
Title: On the Theoretical Limitations of Embedding-Based Retrieval
Authors: Orion Weller, Michael Boratko, Iftekhar Naim, Jinhyuk Lee

Abstract: Vector embeddings have been tasked with an ever-increasing set of retrieval tasks over the years, with a nascent rise in using them for reasoning, instruction-following, coding, and more. These new benchmarks push embeddings to work for any query and any notion of relevance that could be given. While prior works have pointed out theoretical limitations of vector embeddings, there is a common assumption that these difficulties are exclusively due to unrealistic queries, and those that are not can be overcome with better training data and larger models. In this work, we demonstrate that we may encounter these theoretical limitations in realistic settings with extremely simple queries. We connect known results in learning theory, showing that the number of top-k subsets of documents capable of being returned as the result of some query is limited by the dimension of the embedding. We empirically show that this holds true even if we restrict to k=2, and directly optimize on the test set with free parameterized embeddings. We then create a realistic dataset called LIMIT that stress tests models based on these theoretical results, and observe that even state-of-the-art models fail on this dataset despite the simple nature of the task. Our work shows the limits of embedding models under the existing single vector paradigm and calls for future research to develop methods that can resolve this fundamental limitation.

---
##### description Links
- https://arxiv.org/abs/2508.21038
- https://arxiv.org/pdf/2508.21038
- https://arxiv.org/html/2508.21038v1
- https://doi.org/10.48550/arXiv.2508.21038

---
##### Reflection

---