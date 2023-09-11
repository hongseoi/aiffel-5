# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 김성진


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
    - 문제를 해결하는 완성된 코드란 프로젝트 루브릭 3개 중 2개, 
      퀘스트 문제 요구조건 등을 지칭
        - 해당 조건을 만족하는 코드를 캡쳐해 근거로 첨부
     
> 1. 챗봇 훈련데이터 전처리 과정이 체계적으로 진행되었는가?

- augmentation 으로 3만개 이상의 데이터셋 구축은 진행되지 않았습니다.

> 2. transformer 모델을 활용한 챗봇 모델이 과적합을 피해 안정적으로 훈련되었는가?


- loss 값으로 볼 때 안정적으로 훈련이 되었습니다.
```python
Epoch 1, Loss: 7.0205: 100%|██████████| 146/146 [00:20<00:00,  7.21it/s]
Epoch 2, Loss: 4.9967: 100%|██████████| 146/146 [00:15<00:00,  9.18it/s]
Epoch 3, Loss: 4.1966: 100%|██████████| 146/146 [00:16<00:00,  9.03it/s]
Epoch 4, Loss: 3.5220: 100%|██████████| 146/146 [00:16<00:00,  8.89it/s]
Epoch 5, Loss: 2.8643: 100%|██████████| 146/146 [00:16<00:00,  8.73it/s]
```

> 3. 챗봇이 사용자의 질문에 그럴듯한 형태로 답하는 사례가 있는가?

- 질문에 그럴듯한 형태로 답이 되었습니다.

```python
('몇일정도 썸타?', '정해져 있지는 않지만 길지 않은게 서로에게 좋을 거예요.'), ('또 지각하네', '더 일찍 일어나세요.'), ('오해하는 거 같은데 어떡하지?', '오해할만한 일이 생겼을때는 솔직하게 이야기하고 풀어보세요.')
```
    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
  주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드가 무슨 기능을 하는지, 왜 그렇게 짜여진건지, 작동 메커니즘이 뭔지 기술.
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

> 단어사전 생성
```python
# 전체 단어사전 구축
combined_corpus = tokenized_que_corpus + tokenized_ans_corpus_with_start_end
combined_corpus = [str(sentence) for sentence in combined_corpus]

# 단어사전 생성 위한 Tokenizer 객체 생성

tokenizer = tf.keras.layers.TextVectorization(
    output_mode="int",
    max_tokens=5000,  # 원하는 최대 토큰 수로 설정
    output_sequence_length=50  # 원하는 최대 시퀀스 길이로 설정
)
tokenizer.adapt(combined_corpus)
```
  
- [ ]  **3. 에러가 난 부분을 디버깅하여 문제를 “해결한 기록을 남겼거나” 
  ”새로운 시도 또는 추가 실험을 수행”해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 문제에서 요구하는 조건에 더해 추가적으로 수행한 나만의 시도, 
      실험이 기록되어 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

> 코드의 마지막 부분을 제외한 곳에는 에러가 없습니다.
> 마지막 부분은 아직 해결되지 않았습니다.

```python
AttributeError: 'TextVectorization' object has no attribute 'bos_id'
```
  
- [ ]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.
    
- [x]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 하드코딩을 하지않고 함수화, 모듈화가 가능한 부분은 함수를 만들거나 클래스로 짰는지
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화했는지
        - 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부합니다.

> 함수화, 모듈화가 적절히 되었습니다.
```python
def build_corpus(src_sentences, tgt_sentences, tokenizer, max_length=40):
    que_corpus = []
    ans_corpus = []
    unique_pairs = set()  # 중복 검사용 집합

    for src, tgt in zip(src_sentences, tgt_sentences):
        src = preprocess_sentence(src)
        tgt = preprocess_sentence(tgt)

        # 소스와 타겟의 토큰화
        src_tokens = tokenizer(src)
        tgt_tokens = tokenizer(tgt)

        # 일정 길이 이상인 문장 및 중복 문장 필터링
        if len(src_tokens) > max_length or len(tgt_tokens) > max_length:
            continue
        pair = (src, tgt)
        if pair in unique_pairs:
            continue

        # 유효한 문장인 경우 코퍼스에 추가
        que_corpus.append(src)
        ans_corpus.append(tgt)
        unique_pairs.add(pair)
        
    print(unique_pairs)
    return que_corpus, ans_corpus
```

# 참고 링크 및 코드 개선
```
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
```

> 결과가 잘 나오네요. 
> 회고와 에러 수정만 하시면 될 것 같습니다. :)