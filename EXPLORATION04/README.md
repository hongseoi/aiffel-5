# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 홍서이
- 리뷰어 : 손정민


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [ ] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > kaggle 제출 점수가 기준치 110000을 초과했습니다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 각 과정에 대한 주석을 써주셔서 어떤 의도로 작성한 코드인지 이해하기 쉬웠습니다. 또한 마크다운을 사용해 추가적인 설명을 제공해 코드 이해에 도움을 주었습니다.
- [ ] 코드가 에러를 유발할 가능성이 없나요?
  > jupiter notbook 특성상 코드를 수정하거나 삭제해도 재실행하지 않으면 작동되는 부분 때문인지, 특히 변수명에서 오류가 있었으나 이름만 고쳐주면 해결되는 부분이었습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 전처리, 시각화를 상황에 맞춰 적절히 사용하였고, 데이터의 분포를 보고 정규화가 필요한 요소를 잘 파악했습니다. 모델 부분에서도 평가 수단의 특성이나 사용한 모델, 기법을 잘 이해하고 작성한 것으로 보입니다.
- [X] 코드가 간결한가요?
  > 대부분의 코드를 함수로 작성하였고, 작성한 함수에 대한 설명을 주석을 통해 제공했습니다. 함수명과 변수명 또한 직관적으로 어떤 역할을 수행하는지 알 수 있게 작성했습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

```python
# 예시: 주석 사용
# check distribution

def check_distribution(df, col=1):
    row = int(df.shape[1] / col)

    count = 1
    columns = df.columns
    
    fig, ax = plt.subplots(row, col, figsize=(12,20))
    for i in range(row):
        for j in range(col):
            sns.kdeplot(data=df[columns[count]], ax=ax[i][j])
            ax[i][j].set_title(columns[count], fontsize=15)
            count += 1
            if count == df.shape[1]:
                break
    plt.subplots_adjust(wspace=0.5, hspace=1)
                
check_distribution(df, col=2)
```
```python
#예시: 간결한 코드
# handling missing values

def check_missing(data):
    msno.matrix(data)
    
    # double check!
    for c in data.columns:
        print('{} : {}'.format(c, len(data.loc[pd.isnull(data[c]), c].values)))
```

# 참고 링크 및 코드 개선
```python
def get_gs_result(
    model, train, y, param_grid={'n_estimators': [50, 100], 'max_depth': [1, 10] }, verbose=2, n_jobs=5):
    
    grid_model = GridSearchCV(
        model, param_grid=param_grid, 
        scoring='neg_mean_squared_error', 
        cv=5, verbose=verbose, n_jobs=n_jobs)
    
    grid_model.fit(train, y)

    params = grid_model.cv_results_['params']
    score = grid_model.cv_results_['mean_test_score']
    
    results = pd.DataFrame(params)
    results['score'] = score
    
    results['RMSLE'] = np.sqrt(-1 * results['score'])
    results = results.sort_values('RMSLE')

    return results
```
```python
get_gs_result(
    LGBMRegressor(random_state=random_state), train, y)

# grid search에서 하이퍼 파라미터 튜닝을 위한 param_grid를 함수 내부에 넣어서 사용했는데,
# 이러면 모든 모델에 대해 같은 값만을 탐색할 수 있다는 단점이 있습니다.
# 각 모델의 하이퍼 파라미터를 살펴보고 함수 외부에서 넣어주는 식으로 변경하면
# 각각의 모델에 더 적합한 하이퍼 파라미터를 설정하고 성능을 높일 수 있을 것 같습니다.
```
