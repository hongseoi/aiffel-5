# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 윤상현


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [:laughing:] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
- [:laughing:] 주석을 보고 작성자의 코드가 이해되었나요?
- [:laughing:] 코드가 에러를 유발할 가능성이 없나요?
  > 문제 없을 듯 합니다. 잘 짜여져있습니다.
- [:laughing:] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 중요 부분의 코드에 대해 정확하게 알고 계셔서, 제대로 이해하셨다고 판단됩니다.
- [:laughing:] 코드가 간결한가요?
  > 간결할 수 없는 흐름인데, 비교적 간결하게 잘 작성하신 것 같습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

```python
# 인코더 설계 시작
embedding_dim = 128
hidden_size = 256

# 인코더
encoder_inputs = Input(shape=(text_max_len,))

# 인코더의 임베딩 층
enc_emb = Embedding(src_vocab, embedding_dim)(encoder_inputs)

# 인코더의 LSTM 1
encoder_lstm1 = LSTM(hidden_size, return_sequences=True, return_state=True, dropout=0.4)
encoder_output1, state_h1, state_c1 = encoder_lstm1(enc_emb)

# 인코더의 LSTM 2
encoder_lstm2 = LSTM(hidden_size, return_sequences=True, return_state=True, dropout=0.4)
encoder_output2, state_h2, state_c2 = encoder_lstm2(encoder_output1)

# 인코더의 LSTM 3
encoder_lstm3 = LSTM(hidden_size, return_sequences=True, return_state=True, dropout=0.4)
encoder_outputs, state_h, state_c = encoder_lstm3(encoder_output2)

레이어 통과 과정을 쭉 나열하여 LSTM까지 가는 부분이 좋았습니다.
직관적이며 이해가 쉬웠습니다.
```

# 참고 링크 및 코드 개선
```python
None
```
