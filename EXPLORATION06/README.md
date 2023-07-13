# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 손정민


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 수염 이미지를 적당한 위치에 잘 붙였고, 문제점에 대한 고찰 역시 잘 작성했다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 각 과정에 함수의 역할, 함수 속 코드까지 주석을 달아 어떤 기능을 하는지 파악하기 쉬웠다. 또한 적절한 마크다운의 사용으로 시각 자료와 각 과정에 대한 설명을 제공하였다.
```python
  # Position the sticker

for dlib_rect, landmark in zip(dlib_rects, list_landmarks):
    print (landmark[30]) # nose index is 30
    x = landmark[30][0] # nose location x
    y = landmark[30][1] - dlib_rect.height()//2  # nose location y
    w = h = dlib_rect.width() # The number of pixels occupying the horizantal area of the face //2
    print (f'(x,y) : ({x},{y})')
    print (f'(w,h) : ({w},{h})')
```

- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 에러 없이 잘 동작했다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 주석을 단계별로 상세하게 달았고 생길 수 있는 문제점에 대한 답변도 알맞게 작성했다. 스티커 위치를 잡는 부분에서도 사용 방법을 잘 이해하고 작성한 것으로 보인다.
- [X] 코드가 간결한가요?
  > 필요없는 과정 없이 적절하게 처리했고 변수명 역시 보기 편하고 직관적인 이름을 사용하였다. 


# 참고 링크 및 코드 개선
```python
sticker_area = img_show[refined_y:refined_y+img_sticker.shape[0], refined_x:refined_x+img_sticker.shape[1]]

img_show[refined_y:refined_y+img_sticker.shape[0], refined_x:refined_x+img_sticker.shape[1]] = \
    np.where(img_sticker==0,sticker_area,img_sticker).astype(np.uint8)
```
스티커의 검은 부분(표시되어야 할 부분)이 투명화가 되고 배경이 흰 색으로 표시되었는데, 컬러가 있고 배경이 검은색인 노드의 왕관 스티커와는 다르게 우리가 사용한 이미지는 보여야 할 부분이 검은색이어서 검은색을 sticker_area로 표시하고 나머지를 img_sticker로 표시하는 위 코드에서 문제가 생긴 것으로 보인다.
```python
sticker_area = img_show[refined_y:refined_y+img_sticker.shape[0], refined_x:refined_x+img_sticker.shape[1]]

img_show[refined_y:refined_y+img_sticker.shape[0], refined_x:refined_x+img_sticker.shape[1]] = \
    np.where(img_sticker==255,sticker_area,img_sticker).astype(np.uint8)
```
이렇게 작성하면 흰색 부분이 sticker_area로 대체되고 나머지가 img_sticker로 표시된다. 또는,
```python
(img_sticker==0, img_sticker, sticker_area)
```
로 작성하여도 똑같이 표시된다.(검은 부분만 표시하고 나머지는 sticker_area로 대체)

#### 반투명한 스티커 만들기
```python
img_show[refined_y:refined_y+img_sticker.shape[0], refined_x:refined_x+img_sticker.shape[1]] = \ 
    cv2.addWeighted(sticker_area, 0.5, np.where(img_sticker==255, sticker_area, img_sticker)\
      .astype(np.uint8), 0.5,0)
```
여기에서 0.5는 가중치이다. img_show[~] np.where 밖에 cv2.addWeighted()를 사용해주면 sticker_area에 기본으로 0.5의 가중치가 적용되고, np.where()에 따라 색깔을 가진(배경을 제외한) 스티커 구역에 가중치 0.5, 그 외 구역은 sticker_area로 대체되어 0.5가 적용된다. 따라서 스티커는 살짝 투명하게 보이고 이외의 배경은 원본대로 보이게 된다.