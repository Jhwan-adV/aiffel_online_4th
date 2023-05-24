# Week 4 - Word Embedding

## INTRO 

단어를 단지 나열된 순서대로 indexing한 one-hot encoding은  단어 간의 관계를 전혀 고려하지 못한다.  
이 문제를 해결하기 위해 단어 간 관계를 학습하여 벡터화하는 **Word Embedding**에 대해 알아본다. 

## 4.1. 분포적 가설(Distributional Hypothesis)
> 단어는 주변 단어들에 의해 정의된다  

단어 간 관계를 파악하기 위해, 수천, 수만 개의 문장을 찾아 머신러닝 비지도학습 모델로 파악한다. 

## 4.2. Word Embedding (Word Vector)
몇천, 몇만 차원을 몇십, 몇백 차원의 벡터로 낮추는 것이 목표  
- Word Embedding의 모든 row는 0이 아닌 숫자

## 4.3. 구현 - GloVe (Stanford) & Word2vec (Google)
### 4.3.1. Glove (Stanford) - 직관적인 Counting을 활용
> 말뭉치(Corpus)의 전 단어를 2차원 배열로 나열 후 함께 등장하는 횟수를 벡터에 저장하는 방식  

벡터의 차원 크기 문제, 0이 상당히 많은 희소행렬 문제가 잔존한다.  
SVD(Singular Value Decomposition)와 PCA(Principle Component Analysis) 알고리즘으로 벡터의 차원을 축소한다.

### 4.3.2. Word2vec (Gogle) - 신경망(neural network) 활용
> 타깃 간 관계를 예측(Classification)하는 문제로서 접근하는 방식

- CBOW(Coutinuous Bag of Words)  
주변 단어들을 통해 타깃 단어를 예측
- Skipgram   
타깃 단어를 통해 주변 단어들을 예측

에측 모델은:   
- 신경망(neural network)으로 구현,  
- SGD(Stochastic Gradient Descent)로 학습된다.  

N $\times$ 1의 Word Embedding이 무작위 숫자로 초기화된 후,  
학습이 거듭되며 주변 단어들과의 관계가 encoding된다.  

## 4.4. Word Embedding의 이점  
- 벡터의 연산을 통해 의미적 관계(Semantic Relation)와 통사적 관계(Syntactic Relation)을 알아낼 수 있다.  

- 엄청난 양의 Corpus로 학습되어, NLP Task의 input으로 활용할 때의 성능 증가 기대 폭이 크다.   
