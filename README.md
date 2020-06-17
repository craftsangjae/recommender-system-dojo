## Practical Collaborative Filtering From Scratch

### 목적 

> 현업에 적용 가능한 협업 필터링 구현하기  

### 구성

`scripts/` 폴더 아래에는 스크립트 별로 협업 필터링 알고리즘이 구현되어 있습니다.

1. `Collaborativce Filtering for Large-Scale Service`
    
    * MinHASH & Secondary Indexing을 통해, Single Machine으로도 대규모 데이터 처리 가능한 추천 시스템 구현
    * [하용호님의  추천 시스템 발표자료](https://www.slideshare.net/deview/261-52784785)에서 제시한 방법론을 바탕으로구현
    
2. `Build BPR Using Tensorflow`

    * Tensorflow 2.0 으로 Matrix Factorization의 일종인 Bayesian Personalized Ranking 구현
    * [implicit package](https://implicit.readthedocs.io/en/latest/bpr.html)의 구현 형태를 참조
        * SGD가 아닌 Adagrad로 변형, 배치 학습함
    * [Annoy Package](https://github.com/spotify/annoy)로 추천시스템을 어떻게 Serving할 수 있는지 다룸    
    
3. `Build ALS Using Spark`
    
    * Spark ML 을 이용해 구현 (Spark Tutorial 내용 참조)
    * 참고자료 : [Collaborative Filtering](https://spark.apache.org/docs/2.2.0/ml-collaborative-filtering.html)
    
4. `Neural Collaborative Filtering`

    * [Neural Collaborative Filtering](https://arxiv.org/abs/1708.05031)을 참조하여 구현.
    * 변형 사항 : 논문 내 제시한 Uniform Sampling 대신, 아이템의 분포에 맞춰 Sampling.

### 설명

협업필터링(Collaborative Filtering)은 추천 시스템에서 가장 보편적으로 사용되는 알고리즘입니다. 
협업 필터링은 고객과 아이템 사이의 Interaction 정보들을(예시 : 구매 / 페이지 뷰 / 좋아요 / 구독 등) 통해
고객이 선호하는 제품과 유사한 제품을 찾거나, 고객과 소비 성향이 비슷한 고객군을 찾는 것을 목적으로 합니다. 
협업 필터링에서의 **협업**이 지칭하는 의미는 고객과 아이템 사이의 관계를 통해 정보를 파악한다는 것이고, **필터링**은
파악된 정보를 통해 고객이 선호할만한 제품들을 추려낸다는 것에 있습니다.

협업 필터링은 기술의 역사에 따라 점진적으로 발전해왔습니다. 초기 아마존에서 사용했던 추천시스템으로 알려져 있는 
Item-Based Collaborative Filtering은 대표적인 Memory 기반 협업 필터링으로, 모형의 학습 과정 없이 제품 간 유사도를 도출하여 
유사한 제품을 찾아냅니다. 이러한 방식의 추천시스템은 구조가 간단하고, 실시간으로 새로 추가된 아이템들을 추천할 수 있다는 점이 특징입니다. 그래서
뉴스 추천과 같이 새로운 컨텐츠를 즉시 추천해야 하는 상황에서 특히 선호받고 있습니다.

하지만 Memory-Based Collaborative Filtering은 뻔한 추천, 즉 사용자들이 예상치 못한 추천하지 못해 새로운 구매를 이끌어내는 효과가 약하다는
단점이 존재합니다. 이를 좀 더 개선하기 위해 Matrix Factorization을 필두로 한 Model 기반 추천시스템이 나타났습니다. 
상호작용 정보를 통해, 고객과 아이템의 잠재 변수(latent Factor)를 학습하는 Matrix Factorization은 다른 머신러닝 방법론처럼 
손실함수와 경사하강법을 통해 Latent Factor를 찾습니다. Matrix Factorization의 방법으로는 대표적으로 ALS와 BPR이 존재합니다. 데이터나 운용 환경에 따라서 ALS와 BPR 둘 중에서
어떤 모형을 쓸지를 고려합니다.

그리고 딥러닝 붐이 일어난 후, 협업필터링에서도 딥러닝을 적용한 사례가 속속히 생기기 시작했습니다. 그 중 대표적인 논문이 
[Neural Collaborative Filtering](https://arxiv.org/abs/1708.05031)은 기존의 Matrix Factorization의 수식이
아이템 간, 유저 간 관계를 추론하는 데에 부적합하다는 것을 보여주면서, 그 대안책으로 딥러닝을 활용한 Matrix Factorization을 제시합니다.
아직 해당 모형을 이용한 실증 사례가 소개된 적은 없지만, 많은 개발자들이나 연구자들이 많이 참고하고 있는 모형 중 하나입니다.
 