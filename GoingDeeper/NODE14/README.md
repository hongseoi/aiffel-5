# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 신유진


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [V] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 작성한 코드 모두 정상적으로 동작했고, 루브릭에서 평가하는 항목도 전부 다 완성되어 있다.  
- [V] 주석을 보고 작성자의 코드가 이해되었나요?
  > 넵, 블록 및 섹션별로 주석필기가 깔끔하여 직관적으로 이해하기 쉬웠다. 
- [V] 코드가 에러를 유발할 가능성이 없나요?
  > 없음, 모든 코드가 제대로 작동한다.
- [V] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 넵, 어떤 기능을 하는 코드인지 적힌 주석들만 봤을때 작성자가 코드들을 이해하고 작성했음을 확인할 수 있었습니다.
- [V] 코드가 간결한가요?
  > 넵, 간결하고 직관적입니다.
  
# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

```python
# SentencePieceTokenizer train하는 부분에서 저는 도큐먼트를 참고해 한줄로 표기했었는데 한줄씩 푠혈 될 수도 있구나, 코드를 배우고 갑니다.

 # Train SentencePiece tokenizer
    spm.SentencePieceTrainer.train(
        f"--input={lang}_corpus.txt --model_prefix={model_prefix} --vocab_size={vocab_size}" + 
        f" --pad_id={pad_id} --pad_piece=[PAD]" +
        f" --unk_id={unk_id} --unk_piece=[UNK]" +
        f" --bos_id={bos_id} --bos_piece=[BOS]" +
        f" --eos_id={eos_id} --eos_piece=[EOS]" +
        " --model_type=unigram --max_sentence_length=999999")

```

# 참고 링크 및 코드 개선
```python
제가 참고한 도큐먼트는 프로젝트에 나와있는 도큐먼트로 특히 이 페이지를 참고했었습니다.
https://github.com/google/sentencepiece/blob/master/python/sentencepiece_python_module_example.ipynb
```
