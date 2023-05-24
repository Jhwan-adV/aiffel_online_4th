# Week 2 - 순서를 고려하지 않은 단어 처리법

> 문장을 이해하는 데 순서가 중요핧까?  
- 순서가 중요한 작업과 처리 방법  
- **그렇지 않은 작업과 처리 방법**
___  
## 2.1. 순서를 고려하지 않은 방법
### **BoW(Bag of Words) Vector**
각 단어의 column vector를 합하여 문장을 표현한 vector  
BOW vector의 숫자는 각 index 단어의 빈도수  

### **N-gram**
<u>최소한의 순서를 고려하자는 차원에서 도입</u>  

>n-gram = 인접한 단어 n개의 단어 뭉치  

문장의 첫 단어부터 n-gram으로 나누어 BoW Vector를 생성  
- (예) n-gram = 2의 BoW 벡터   
"나는 애니메이션 영화 보는 것을 좋아해."  
['나는 애니메이션', '애니메이션 영화', '영화 보는', '보는 것을', '것을 좋아해']  

단어 수가 많을수록 Vocabulary가 기하급수적으로 증가한다.  
주로 n-gram = 2~3 정도의 수준으로 진행  


### **TF-IDF(Term Frequency - Inverse Document Frequency)**
<u>빈도 수에 비해 중요도는 낮은 단어</u>를 가려내기 위한 방법  

> TF(Term Frequency) - 문장 내에서의 **단어 빈도**  
DF(Document Frequency) - 해당 단어가 등장하는 **총 문장 수**  

두 지표가 보는 대상이 다르다는 점을 기억하면 이해하기 좋다.  
TF는 **단어가 자주 등장하는지**를 확인하고 싶은 것  
DF는 **단어가 아무 문장에나 등장하는가**를 확인하고 싶은 것

두 지표를 고려한 TF-IDF 점수는 다음과 같아진다.

$$ TF-IDF\,score =  tf\times \frac{log(N)}{df}$$  

등장하는 문장의 수가 많을수록,   
다시 말해 아무 문장에나 등장할수록 **중요도가 떨어진다.**  
이를 반영하기 위해 DF 점수를 분모에 둔 것이다.  
<br>
___
<br>  

## 2.2. BoW(with N-gram), TF-IDF의 단점
1. 순서를 고려하지 않은 방법인만큼, 순서가 중요한 문제에 사용하기 어렵다.  
    - 순서가 중요하지 않은 일: topic classification, document retrieval  
    - 순서가 중요한 일: machine translation  
<br>

2. One-hot Vector의 근본적인 한계  
    - N $\times$ 1로 벡터화하기 때문에, N에 따라 벡터가 지나치게 커진다.
        - 희소행렬(Sparse matrix) 문제
        - 차원은 커지지만 정작 벡터에는 0이 가득하다
        - 의미없는 데이터가 자원을 지나치게 많이 할애하는 것  
    <br>    
    - 단어 간의 관계를 표현하지 못함  
        - 단순히 단어 순서대로 index를 부여했기 때문  
        - '책상 / 테이블', '공책 / 필기장' 등 동의어, 유의어 처리에 약함
    
