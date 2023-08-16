# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 김석영


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [O] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네. 다양한 이미지들로 해당 문제의 평가기준들을 확인/충족하였습니다.
  > 평가문항 1~3까지의 각각의 상세기준들을 모두 충족하였습니다.
- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네 각 tast별 주제와 각 코드별 의미를 텍스트와 주석으로 상세히 기재해 코드 이해에 어려움이 없었습니다.
- [O] 코드가 에러를 유발할 가능성이 없나요?
  > 이미지 주소도 함수화했고, 특별히 에러를 유발할 특이 사항은 없어 보입니다.
- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > Task의 구분이 세분화돼 있고, 각 task에 대한 설명이 상세하므로, 제대로 된 이해를 바탕으로 코드가 작성이 돼 있는 것으로 보입니다.
- [O] 코드가 간결한가요?
  > 꼭 필요한 코드들로 간결하게 작성이 돼 있다고 할 수 있습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

```python
# BRG가 아닌 RGB 순서로 변경
colormap = np.zeros((256, 3), dtype = int)
ind = np.arange(256, dtype=int)

for shift in reversed(range(8)):
    for channel in range(3):
        colormap[:, channel] |= ((ind >> channel) & 1) << shift
    ind >>= 3
    
seg_color = (128,128,192)
seg_map = np.all(output==seg_color, axis=-1) 
print(seg_map.shape) 
plt.imshow(seg_map, cmap='gray')
plt.show()
```

# 참고 링크 및 코드 개선
```python
필요에 따라 선택적으로 함수화 할 수 있는 부분도 있을 것 같습니다.
```
