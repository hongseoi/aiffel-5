# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 신유진


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [-] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 작성한 코드 모두 정상적으로 동작했고, 루브릭에서 물어보는 코드는 다 작성했지만 영어단어가 제대로 출력되지 않아서 한번 같이 고민해보고싶다. 
- [V] 주석을 보고 작성자의 코드가 이해되었나요?
  > 넵, 블록 및 섹션별로 주석필기가 깔끔하여 직관적으로 이해하기 쉬웠다. 
- [V] 코드가 에러를 유발할 가능성이 없나요?
  > 에러는 없지만, preprocessing을 통과하는 과정에서 객체 안에 담겨진 정보가 제대로 전달이 안된것같다. 코드 자체는 모두 다 에러없이 정상적으로 작동하지만 영어단어가 출력되지 않아서 한번 같이 고민해보고싶다.
- [V] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 넵, 어떤 기능을 하는 코드인지 적힌 주석들만 봤을때 작성자가 코드들을 이해하고 작성했음을 확인할 수 있었습니다.
- [V] 코드가 간결한가요?
  > 넵, 간결합니다.
  
# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

```python
# 데이터 전처리 하는 과정에서 lang이 eng일때 전처리를 해준 후 
from konlpy.tag import Mecab
from tensorflow.keras.preprocessing.text import Tokenizer

# 전처리 함수
def preprocess_sentence(sentence, lang, s_token=False, e_token=False):
    sentence = sentence.lower().strip()
    
    if lang == 'en':
        sentence = re.sub(r"([?.!,])", r" \1 ", sentence)
        sentence = re.sub(r'[" "]+', " ", sentence)
        sentence = re.sub(r"[^a-zA-Z?.!,]+", " ", sentence)
    elif lang == 'ko':
        mecab = Mecab()
        sentence = ' '.join(mecab.morphs(sentence))
    
    sentence = sentence.strip()
    
    # decoder의 입력 문장과 라벨로 사용할 출력 문장에 꼭 필요
    if s_token:
        sentence = '<start> ' + sentence  #여기 부분에서 sentence안에 담겨진 정보가 없는것이 아닌가하는 생각이 듭니다. print로 출력해보면서 한번 시도해보는게 어떨가요..?

    if e_token:
        sentence += ' <end>'
    
    return sentence
```

# 참고 링크 및 코드 개선
```python
저는 node11에 나와있는 preprocessing_sentence 코드를 그대로 작성후 토큰화 할때 mecab()을 사용했었습니다. 
또는 preprocessing_sentence에서 mecab() 활용해보려고 한다면, 위에서 언급한 내용처럼 print()로 출력해보면서 debugging 해보시는 게 어떨까요..? 
sentence 쯤에서 객체가 전달되지 않은것 같네요..

```
