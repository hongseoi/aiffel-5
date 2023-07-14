# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 홍수정


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 리뷰를 tokenizing,encoding하여 모델 학습을 완료했으나 test accuracy가 0.85 이상이 되지 않음
  > word2vec을 이용한 모델 개선을 진행하지 못함
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 진행 중간에 수치를 배정한 이유에 대해 md 혹은 주석으로 설명을 충분히 함
  > ex.
  > 데이터셋 내 문장길이 분포는 10~20 사이가 가장 빈도가 높다.
  > 데이터셋 내 문장길이의 평균은 약 16이다.
  > 따라서 최대 문장 길이는 (평균 + 2*표준편차)인 16 + 24 = 40으로 설정할 것이다.
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 코드가 문제가 될 부분은 확인 되지 않음
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 리뷰 데이터를 모델학습 시키는 부분을 데이터 정제부터 차례로 진행한 부분에서 충분한 이해가 있다고 생각함
- [x] 코드가 간결한가요?
  > loss/accuracy를 그리는 plot들의 경우 따로 loss, acc으로 저장하지 않고 그릴 수 있을 것으로 보이지만,
  > 취향의 문제로 여겨질 수 있는 부분으로 충분히 간결하다고 생각함

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

```python
작동 방식은 Exploration 노드1에서 학습한 내용 기반입니다. 
```

# 참고 링크 및 코드 개선
```python
# 데이터가 순차적으로 정렬되어 있는 경우도 존재하여 index로 분리를 한다면
# np.random function을 이용하여 분리하는 것도 권장 드립니다.

# 훈련셋, 검증셋 고르기
train_rand_idxs = np.random.choice(50000, 700)
val_rand_idxs = np.random.choice(10000, 300)

X_train = X_train[train_rand_idxs]
Y_train = Y_train[train_rand_idxs]
X_val = X_val[val_rand_idxs]
Y_val = Y_val[val_rand_idxs]

#https://wikidocs.net/28952
```
