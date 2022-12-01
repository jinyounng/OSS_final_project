# OSS_final_project
Open Source SW Final project

1. What you do in your project

   -튜머 데이터 셋을 이용하여 트레인 셋을 4개의 튜머종류에 알맞게 분류하는것
   -data set을 분류하는데 여러 종류의 clasifier가 sklearn 안에 있음
   -이 classifier 중에서 data set에 정확도가 가장 높은 classifier를 찾는다
   -classifier와 더불어 가장 잘 맞는 parameter들을 찾아 높은 정확도를 구현한다.
   
2. Explain the training dataset
   - training dataset
   - ( glioma_tumor, meningioma_tumor, no_tumor, pituitary_tumor)로 분류된다
   - io.imread function을 사용하여 폴더에 있는 모든 사진을 불러온다
   - transform.resize(64,64)를 사용하여 이미지를 64 * 64 로 조정한다
   - color.rgb2gray를 사용하여 이미지의 색을 회색으로 바꾼다
   - 이렇게 생성된 이미지를 np.array로 바꿔준다
   - 마지막으로, train data에 과적합되지 않도록, training, test set으로 나누어준다.
   - 그 후 사용할 classifier에 훈련시킨다
 
 
 3. Explain the algorithm you choos
   - 내가 선택한 classifier SVM, Extratree, randomforest , KNN이다
   - SVM은 Support Vector Machine으로 그룹을 분리하는 방법으로, 데이터들과 거리가 먼 hyperplane을
     선택하여 데이터를 분리하는 방법이다.
     parameter는 4번에서 설명하겠다.
     
   - random forest는 의사결정tree 모델을 여러 개를 훈련시켜서 그 결과를 종합해 예측하는 앙상블 알고리즘이다.
     각 의사결정tree를 훈련시킬 떄 배깅 방식을 사용한다. Train data를 중복을 허용하여 샘플링한 data로
     개별 의사결정Tree를 훈련시킨다.
     
     배깅 방식이란 ?
     bootstrap aggregating으로 bias, variance를 낮추는데 효과적이다.
     train set을 반복 복원 추출하여 train하는 방식
     
   - KNN은 K-Nearist Neighbor으로 최근접 이웃 분류방법이다
     KNN은 주변의 가장 가까운 K개의 데이터를 보고 데이터가 속할 그룹을 판단하는 것이다. 
   
   - ensemble : voting, Bagging, Boosting, Staking
     나는 sklearn ensemble 중 voting 모델을 사용했다.
     voting모델은 soft voting 과 Hard voting 모델이 있는데
     Soft Voting모델은 다수의 classifier의 예측 결과값을 다수결로 최종 Class를 결정하는 것
     Hard Voting모델은 다수의 classifier의 예측 결과값간 확률을 평균내어 최종 class를 결정하는 것
     주로 soft voting모델의 성능이 우수하여 주로 사용된다.
     
  4. Explain hyper-parameter of the function
   4.1 hyperparameter of SVM
     -
   4.2 hyperparameter of Extratree
     -
   4.3 hyperparameter of randomforest
     -
   4.4 hyperparameter of KNN
    - 
