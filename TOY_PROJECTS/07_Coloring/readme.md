# AIFFEL Campus Online 4th Code Peer Review Templete
- 코더 : Kim Jaehwan
- 리뷰어 : Kim Donggyu


# PRT(PeerReviewTemplate)
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.
- [O] 1.코드가 정상적으로 동작하고 주어진 문제를 해결했나요?

First task was done!
```
The task's codes were too many.
So, there is no evidence, but it doesn't mean that it weren't done.
```

Second task was done!
```python
# Visualization
plt.plot(history.history['loss'], label='train')
plt.plot(history.history['val_loss'], label='test')

plt.title('Train & Test Loss')
plt.legend()
plt.show()
```
Third task was done!
```python
# Compare target headlines and predicted headlines
for i in range(0,8):
    print("Original text: ", seq2text(encoder_input_test[i]), "\n")
    print("Original headlines: ", seq2summary(decoder_input_test[i]))
    print("Predicted headlines: ", decode_sequence(encoder_input_test[i].reshape(1, threshold_text)))
    print("\n")
```

```
Original text:  cbi filed chargesheet kanpur gst commissioner chand bribery case chand first senior officer gst department established last year face corruption charges agency officials said cbi also charged wife others corruption criminal conspiracy among others  

Original headlines:  gst in case 
Predicted headlines:   cbi officers booked for corruption of yr old
```

```
# Test Extract Summarization
print('Summary with Extraction:\n')
print(summarize(text, ratio=0.5))

```

```
# Result of Abstract Summarization
print("Summary with Abstraction:\n")
print(decode_sequence(encoder_input_test[2].reshape(1, threshold_text)))
```

```
Extract Summarization has more grammatical sentences, and longer than Abstract summary.
Abstract Summarization uses more general words. Some text doesn't make sense.
```
There is conclusion too.

- [O] 2.주석을 보고 작성자의 코드가 이해되었나요?

Yeah, I can understand what he did.
There are some reasons, why i think so.

```
# Build encoder
encoder_model = Model(inputs=encoder_inputs, outputs=[encoder_outputs, state_h, state_c])

# Decoder - Tensor indicating states of 1 time-step ahead
decoder_state_input_h = Input(shape=(hidden_size,))
decoder_state_input_c = Input(shape=(hidden_size,))

# Decoder - Embedding Layer
dec_emb2 = dec_emb_layer(decoder_inputs)

# Decoder - LSTM preserve and use state_h and state_c
decoder_outputs2, state_h2, state_c2 = decoder_lstm(dec_emb2, initial_state=[decoder_state_input_h, decoder_state_input_c])
```

```
# Decoder - Attention Layer (hidden state layer)
decoder_hidden_state_input = Input(shape=(threshold_text, hidden_size))
attn_out_inf = attn_layer([decoder_outputs2, decoder_hidden_state_input])
decoder_inf_concat = Concatenate(axis=-1, name='concat')([decoder_outputs2, attn_out_inf])

# Decoder - Output Layer
decoder_outputs2 = decoder_softmax_layer(decoder_inf_concat) 

# Decoder Result
decoder_model = Model(
    [decoder_inputs] + [decoder_hidden_state_input,decoder_state_input_h, decoder_state_input_c],
    [decoder_outputs2] + [state_h2, state_c2])
```

Every codes have some comment like that.
So, I can understan what the code do.
It is very kind.

- [X] 3.코드가 에러를 유발할 가능성이 있나요?

Because each code is very simple, and consists of only one expression.
So, I think there is no error in the code.

```
# Integer Seq → Word Seq ('text')
def seq2text(input_seq):
    temp=''
    for i in input_seq:
        if (i!=0):
            temp = temp + src_index_to_word[i]+' '
    return temp

# Integer Seq → Word Seq ('headlines')
def seq2summary(input_seq):
    temp=''
    for i in input_seq:
        if i not in [0, 1, 2]:
            temp = temp + tar_index_to_word[i]+' '
    return temp
```

Because the variable's name was "temp", at first, some review can got confused.
But, if you read in detail, the code is also very simple.
Simple code wouldn't make a big mistake, I believe.

- [O] 4.코드 작성자가 코드를 제대로 이해하고 작성했나요?

```
encoder_input_train = pad_sequences(encoder_input_train, maxlen=threshold_text, padding='pre')
```
Above code in the Node 11 work for creation padding sequence.
You use **'pre'** rather than **'post'**
Why you use it.

:: Due to the characteristics of RNN, weights are concentrated in the back, but if padding is piled up behind, there is a possibility that the weights will be lost.

You use a lot of **lambda** functions, can you explain it?

:: I know that it can also be called an anonymous function, It can express a function simply.

- [O] 5.코드가 간결한가요?
```python
def decode_sequence(input_seq):
    # get state of encoder from the sequence
    e_out, e_h, e_c = encoder_model.predict(input_seq)

    # <SOS token>
    target_seq = np.zeros((1,1))
    target_seq[0, 0] = tar_word_to_index['sostoken']

    stop_condition = False
    decoded_sentence = ''
    while not stop_condition: # Repeat loop until stop_condition == True

        output_tokens, h, c = decoder_model.predict([target_seq] + [e_out, e_h, e_c])
        sampled_token_index = np.argmax(output_tokens[0, -1, :])
        sampled_token = tar_index_to_word[sampled_token_index]

        if (sampled_token!='eostoken'):
            decoded_sentence += ' ' + sampled_token

        #  <EOS token> or length_limit == STOP!
        if (sampled_token == 'eostoken'  or len(decoded_sentence.split()) >= (threshold_headline-1)):
            stop_condition = True

        # Update the target sequence (length ==1)
        target_seq = np.zeros((1,1))
        target_seq[0, 0] = sampled_token_index

        # Update the state
        e_h, e_c = h, c

    return decoded_sentence
```
The code is one of the longest code in the project (or even it can be called notebook).
There are lots of lines, but each line was simple.
Every single expression have only one features.
And its readability is good.

# 참고 링크 및 코드 개선
No, there is no idea to suggest something.

I just refer the rubric.

