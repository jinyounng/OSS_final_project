# OSS_final_project
## Open Source SW Final project

## update in 12/09
## reupdate in 12/12(round2)


### 1. What you do in your project
   -튜머 데이터 셋을 이용하여 트레인 셋을 4개의 튜머종류에 알맞게 분류하는것
   -data set을 분류하는데 여러 종류의 clasifier가 sklearn 안에 있음
   -이 classifier 중에서 data set에 정확도가 가장 높은 classifier를 찾는다
   -classifier와 더불어 가장 잘 맞는 parameter들을 찾아 높은 정확도를 구현한다.
   
### 2. Explain the training dataset
   - training dataset
   - ( glioma_tumor, meningioma_tumor, no_tumor, pituitary_tumor)로 분류된다
   - io.imread function을 사용하여 폴더에 있는 모든 사진을 불러온다
   - transform.resize(64,64)를 사용하여 이미지를 64 * 64 로 조정한다
   - color.rgb2gray를 사용하여 이미지의 색을 회색으로 바꾼다
   - 이렇게 생성된 이미지를 np.array로 바꿔준다
   - 마지막으로, train data에 과적합되지 않도록, training, test set으로 나누어준다.
   - 그 후 사용할 classifier에 훈련시킨다
  
### 3. Explain the algorithm you choose
   - 내가 선택한 classifier는 SVM, Extratree, KNN, voting 이다
   
   - Extra forest classifier는 random forest와 비슷하지만, decision tree를 만들어 낼 때, 훈련 세트 전체를 사용하기 때문에
     bagging이라고는 할 수 없다. 또한, Split을 할 때 무작위로 feature를 선정한다. 아무 feauter를 선정하여 그 feature에 대해
     최적의 Node를 분할한다. 이러한 방식은 과대적합을 막고 test set의 정확도를 높이는 효과를 한다. 또한 속도가 빠르다
     
   - KNN은 K-Nearist Neighbor으로 최근접 이웃 분류방법이다
     KNN은 주변의 가장 가까운 K개의 데이터를 보고 데이터가 속할 그룹을 판단하는 것이다. 
   
   - ensemble : voting, Bagging, Boosting, Staking
     나는 sklearn ensemble 중 voting 모델을 사용했다.
     voting모델은 soft voting 과 Hard voting 모델이 있는데
     Soft Voting모델은 다수의 classifier의 예측 결과값을 다수결로 최종 Class를 결정하는 것
     Hard Voting모델은 다수의 classifier의 예측 결과값간 확률을 평균내어 최종 class를 결정하는 것
     주로 soft voting모델의 성능이 우수하여 주로 사용된다.
   
   -나는 SVM,ExtraTree,KNN을 voting하여 최종결과값을 계산했다.
     
### 4. Explain hyper-parameter of the function
   - SVM의 hyper-parameter:
        1.kernel : 알고리즘에 사용되는 kernel을 결정한다. 
        2.degree : polynomial kernel function에서 차수를 결정한다.
        3.gamma : kernel coefiicient for 'rbf' 'poly' 'sigmoid'
                  즉, 결정경계를 얼마나 유연하게 그릴지 결정한다. 클수록 overfitting 가능성이 높아진다.
        4.coef0 : polynomial kernel에 있는 상수항 r.
        5.C : 오류를 얼마나 허용할 것인지 규제한다.

        등이 있는데, 내가 tuning한 hyper-parameter는 C=11이다.
     
     
   
   - KNN의 hyper-Parameter:
        1.algorithm : nearest neighbor을 계산하는데 사용하는 알고리즘으로 ball_tree, kd_tree, brute가 있다.
        2.metric: 거리 측정 방식을 변경하는 매개변수이다.
        3.n_jobs: neighbor을 검색하기 위해 실행하는 병렬 작업의 수.
        4.n_neighbors : 검색할 이웃의 수
        5.p : metric의 변수 minkowsi의 매개변수이다. p=1이면 맨허튼 거리공식, p=2이면 유클리디안 거리공식을 사용한다.

        여기서 내가 변경한 hyper-parameter는 n_neighbor=1,p=1이다. neighbor수를 최대한 적게 설정하였다.

      - RandomForest의 hyper-Parameter:
        1.n_estimators : decision tree의 개수를 의미한다. 증가시킨다고 해서 성능이 무조건적으로 향상되는 것은 아니다.
        2.max_features : decision tree의 max_features와 동일하다. decision tree에서 고려하는 특징 수, 또는 비율이다.
        3.max_depth : decision tree의 최대 깊이이다.
        4.min_sample_leaf : leaf node가 되기 위해 필요한 최소한의 샘플 데이터 수, 과적합을 제어하는 데 사용된다.
        5.random_state : 난수 seed를 설정한다.


      - ExtraTree의 hyper-Parameter:
        RandomForest의 hyper-parameter와 거의 동일하다.
        내가 변경한 hyper-parameter는 n_estimator와 random_state이다.
        decision Tree의 개수를 늘리고, 난수 seed를 설정해주었다.
     
    
 ### 이 코드의 가장 중요한 feature는 voting방식이였는데,
       어떤 classifier들을 함께 voting해야 가장 좋은 결과가 나오는지 찾아보았고,
       하나의 classifier만 사용하였을때보다, 약 2~5퍼센트정도의 정확도가 높아진다.
       많은 시행착오를 통해 svm,xtree,knn을 사용했을 때 가장 좋은 정확도가 나왔다.

     
## 12/12 update imformation
      round1의 결과가 73퍼센트로 나와 조금 더 수정을 해보았다.
      SVM의 parameter 는 verbose=0, kernel='rbf', C=10, coef0=5,degree=9,gamma=1.2 로 바꿔주었고,
      KNN의 parameter는 n_neighbor은 유지하되, 유클리디안 거리공식을 사용하기 위해p=2로 설정하였다.
      또한, Extra Tree의 최적의 random_state를 찾아 추가해주었다.
   
   각각의 결과값이 올랐기 때문에, voting 후의 결과값에도 변화가 있을 것이다.
     
  
         
