# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 :


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
- [] 주석을 보고 작성자의 코드가 이해되었나요?
  > 코드에 대한 주석이 상세하여 이 코드를 짠 이유가 무엇인가 확인하기 쉬웠습니다.
- [] 코드가 에러를 유발할 가능성이 없나요?
  > 이해한 내용에서는 문제 없어보입니다. Project1의 figure 범위 부분이 전처리 등으로 변경될 수 있는 부분도 감안하고 코드를 짜주셨네요.
- [] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 문제에서 제시한 내용들에 대한 코드가 빠짐없이 존재하고, 문제에서 제시한 내용 이상으로 확인하고자 하는 내용 등을 추가로 확인하는 부분이 있어 이해에 문제 없이 진행하셨다고 생각합니다.
- [] 코드가 간결한가요?
  > Project2의 subplot 부분을 좀 더 압축해서 작성할 수 있을 것 같습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

```python
작동 방식은 Exploration 노드1에서 학습한 내용 기반입니다. 
```

# 참고 링크 및 코드 개선
```python
# Project2, subplot
# 'year', 'month', 'day', 'hour', 'minute', 'second' 컬럼을 subplot으로 하나씩 그리기
plt.subplot(2, 3, 1)
sns.countplot(data=df, x='year')
plt.title('Year')

plt.subplot(2, 3, 2)
sns.countplot(data=df, x='month')
plt.title('Month')

plt.subplot(2, 3, 3)
sns.countplot(data=df, x='day')
plt.title('Day')

plt.subplot(2, 3, 4)
sns.countplot(data=df, x='hour')
plt.title('Hour')

plt.subplot(2, 3, 5)
sns.countplot(data=df, x='minute')
plt.title('Minute')

plt.subplot(2, 3, 6)
sns.countplot(data=df, x='second')
plt.title('Second')

#제가 작성했던 코드인데, 각 subplot에 할당할 내용만을 간추려서 작성할 수 있어 간결한 작성에 도움이 될 것 같습니다.
fig, axes = plt.subplots(2, 3, figsize=(15, 10))

sns.countplot(x='year', data=train, ax=axes[0, 0])
sns.countplot(x='month', data=train, ax=axes[0, 1])
sns.countplot(x='day', data=train, ax=axes[0, 2])
sns.countplot(x='hour', data=train, ax=axes[1, 0])
sns.countplot(x='minute', data=train, ax=axes[1, 1])
sns.countplot(x='second', data=train, ax=axes[1, 2])
```
