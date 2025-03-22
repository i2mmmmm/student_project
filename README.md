### 다음 시험에서 나는 몇 점을 받을까?

---

❔ **문제 정의**  

가설 : 수강생의 과거 정오표 데이터를 통해 다음 시험 정/오답 예측을 할 수 있다.  
　　　취약한 유형을 파악해 성적 향상을 기대해 볼 수 있다.

---

📊 **EDA**

- **데이터 변수 설명**
  
**문항정오답표**  
learnerID : 학생 ID  
learnerProfile : 학생 정보 (Gender;학년등급;학년)  
testID : 시험지 ID  
assessmentItemID : 문제 ID  
answerCode : 채점결과 (0:틀림, 1:맞음) **Target**  
Timestamp : 응시 일자  
  
**문항IRT**  
testID : 시험지ID  
assessmentItemID : 문제 ID    
difficultyLevel : 난이도 (-5~5)  
discriminationLevel : 변별도 (0~∞)  
guessLevel : 추측도(0~1)  
Timestamp : 데이터 생성 일자  
knowledgeTag : 지식체계번호  

**응시자IRT**  
learnerID : 학생 ID  
learnerProfile : 학생 정보  
testID : 시험지 ID  
theta : testID 에 대한 응시자의 능력 수준(-5~5)  
realScore : 진점수  
Timestamp : 데이터 생성 일자  

---
   
🎛️ **Modeling**  

baseline = 0.661 (최빈값)  
시간 순서 정렬 후 최근 데이터 20% test set,  
남은 데이터 중 최근 데이터 20% val set  
남은 데이터 train set  
- xgboost : 0.865
- RandomForest : 0.932 ☑️  
하이퍼파라미터 -> max_depth = 20, max_features = 0.7273, n_estimators = 52

---

📓 **회고**

처음 Python으로 진행한 프로젝트라서 굉장히 재미있었다.  
다만 아직 활용할 줄 아는 모델이 많지 않고, feature engineering 단계가 부족하게 느껴졌다.  
진점수의 영향이 큰 것 같아 진점수를 제외한 예측을 다시 한번 진행해봐야겠다.  
그리고 실제 모의고사를 바탕으로 분석을 해서 배포까지 해보고싶다.
