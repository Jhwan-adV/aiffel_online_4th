# AIFFEL Campus Online 4th Code Peer Review Templete
- 코더 : 김재환님
- 리뷰어 : 사재원


# PRT(PeerReviewTemplate)
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.
- [O] 1.코드가 정상적으로 동작하고 주어진 문제를 해결했나요?<br>
-네 잘 동작되며 3가지 모델 학습, 최종 정확도 85%이상 달성 등 프로젝트의 요구사항들을 충족시켰습니다.  

- [O] 2.주석을 보고 작성자의 코드가 이해되었나요?<br>
 -네 주석을 통하여 어떤 의도로 코드를 작성하였는지 판별하기 쉬웠습니다.
```
#코드 길이로 인하여 일부만 발췌
def load_data(train_data, test_data, num_words=10000):
    
    # 훈련 데이터의 중복&결측 데이터 제거
    train_data.drop_duplicates(subset=['document'], inplace=True) 
    train_data = train_data.dropna(how = 'any') 
    
    # 훈련 데이터 토큰화 및 불용어 제거
    X_train = []
    for sentence in train_data['document']:
        temp_X = tokenizer.morphs(sentence) 
        temp_X = [word for word in temp_X if not word in stopwords] 
        X_train.append(temp_X)

    # 사전 word_to_index 구성
    words = np.concatenate(X_train).tolist()
    counter = Counter(words)
    counter = counter.most_common(10000-4)
    vocab = ['<PAD>', '<BOS>', '<UNK>', ''] + [key for key, _ in counter]
    word_to_index = {word:index for index, word in enumerate(vocab)}
    
    # 단어 텍스트 리스트를 사전 인덱스 스트링으로 변환
    def wordlist_to_indexlist(wordlist):
        return [word_to_index[word] if word in word_to_index else word_to_index[''] for word in wordlist]
    
    # 정제된 X_train, X_test 데이터
    X_train = list(map(wordlist_to_indexlist, X_train))
    X_test = list(map(wordlist_to_indexlist, X_test))
    
    # 각각 X_train, y_train, X_test, y_test, word_to_index → 전처리 후 데이터 반환   
    return X_train, np.array(list(train_data['label'])), X_test, np.array(list(test_data['label'])), word_to_index
    
```
- ['X'] 3.코드가 에러를 유발할 가능성이 있나요?<br>
 -아니요 순차적으로 실행시킨다면 에러가 발생하지않았습니다.
 
- [O] 4.코드 작성자가 코드를 제대로 이해하고 작성했나요?<br>
 -네, 함수 선언과 메서드 호출별로 주석을 작성하여 이번 프로젝트에 대해 전반적인 이해가 있었으며<br>
 덕분에 리뷰어 입장에서도 쉽게 이해가 가능하였습니다
 
- [O] 5.코드가 간결한가요?
 -네 적절한 blank line이나 줄바꿈으로 인하여 가독성이 편했습니다.

가독성 좋았던 부분
```
# 학습의 진행
model_rnn_kword2vec.compile(optimizer='adam',
              loss='binary_crossentropy',
              metrics=['accuracy'])
              
epochs = 10  # 몇 epoch를 훈련하면 좋을지 결과를 보면서 바꾸어 봅시다. 

history = model_rnn_kword2vec.fit(partial_X_train,
                    partial_y_train,
                    epochs=epochs,
                    batch_size=512,
                    validation_data=(X_val, y_val),
                    verbose=1)
```

```python
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```
