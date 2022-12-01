# OSS_final_project
Open Source SW Final project

1. What you do in your project

   -튜머 데이터 셋을 이용하여 트레인 셋을 4개의 튜머종류에 알맞게 분류하는것
   -data set을 분류하는데 여러 종류의 clasifier가 sklearn 안에 있음
   -이 classifier 중에서 data set에 정확도가 가장 높은 classifier를 찾는다
   -classifier와 더불어 가장 잘 맞는 parameter들을 찾아 높은 정확도를 구현한다.
   
2. Explain the training dataset
   - training dataset
   - ( glioma_tumor, meningioma_tumor, no_tumor, pituitary_tumor)로 분류됨
   - io.imread function을 사용하여 폴더에 있는 모든 사진을 불러옴
   - transform.resize(64,64)를 사용하여 이미지를 64 * 64 로 조정한다
   - color.rgb2gray를 사용하여 이미지의 색을 회색으로 바꾼다
   - 이렇게 생성된 이미지를 np.array로 바꿔준다
   - 마지막으로, train data에 과적합되지 않도록, training, test set으로 나누어준다.
   - 그 후 사용할 classifier에 훈련시킨다
 
 
 3. Explain the algorithm you choos
   - 내가 선택한 classifier는 SVM이다, 즉 Support Vector machine이다.
   - SVM은 분류를 위한 기준 선을 정의하는 모델이다.
   - 
