<img src="https://img.shields.io/badge/AcornTeam 짜장-3178C6?style=flat&logo=Python&logoColor=white"/>
<h1>AcornTeamJjajang </h1>

## 팀원 : 윤대원, 김동현, 김선우, 권나은, 이하경, 이효민

<h1>주제 : 당신의 주차장은 충분합니까?</h1>

---

# 사용 데이터
| 컬럼명 | 전처리 방향 |  |
| --- | --- | --- |
| 단지코드 | 삭제 |  |
| 총 세대수 |  |  |
| 임대건물구분 | Label Encoding | 아파트 : 0, 상가 : 1 |
| 지역 |  | 노인청소년 비율로 대체 |
| 공급유형 | 삭제 |  |
| 전용면적 | Label Encoding | 전용면적 별 카테고리 구분 |
| 전용면적별 세대수 |  | 공가수 제외한 세대수 컬럼 추가 |
| 공가수 |  |  |
| 자격유형 | 삭제 | A-Z 자격유형 기준 확인 불가 |
| 임대보증금 | 삭제 | 상가 및 매매 결측치 대체 불가 |
| 임대료 | 삭제 | 상가 및 매매 결측치 대체 불가 |
| 지하철역 |  | 지하철 + 버스 = 대중교통 컬럼 추가 |
| 버스정류장 |  |  |
| 단지내주차면수 |  |  |
| 등록차량수 |  |  |


# 주제 선정
### 주차 면수 부족하다 VS 세대당 주차면수 1이상(충분)

- 세대당 자동차 등록대수  
<img src="https://user-images.githubusercontent.com/115984336/215003449-375e4277-0120-420e-9f4d-3d572b4a45c7.png"  width="500" height="300">

  - 주차전쟁 뉴스 크롤링
  <img src="https://user-images.githubusercontent.com/115984336/215007442-412d94dc-288e-4bf9-b581-0a8436a05400.png"  width="500" height="300">

- 서울시 연도별 주차장 확보율(주택 주차장 부족)

<img src="https://user-images.githubusercontent.com/115984336/215003527-cab4a1fe-6113-4a67-980e-bf342913a92b.png"  width="300" height="300"> <img src="https://user-images.githubusercontent.com/115984336/215003541-72299e91-07ff-4502-9787-7d86ba7c15f5.png"  width="300" height="300">

- 법정 주차 대수 선정시 주차수요 원단위 확인(수작업)
  - 객관적 수요 예측 필요
  <img src="https://user-images.githubusercontent.com/115984336/215003488-07a5bddd-d39a-4b97-8b32-e52cdf4a6de4.png"  width="350" height="600">

# 본론
- 주택 건축시 주차 수요를 수작업으로 진행
  - 등록 차량수 예측 모델 필요

1. 상관관계 분석
- 지역별 등록차량 수에 대한 상관관계 분석
<img src="https://user-images.githubusercontent.com/115984336/215003667-e9a75c41-6519-4d60-b0ba-5c97d990f7f7.png"  width="500" height="350">

- 지역별 나이 분포

<img src="https://user-images.githubusercontent.com/115984336/215003622-f06150aa-1a49-4e03-9ed4-45545c902768.png"  width="400" height="300">   <img src="https://user-images.githubusercontent.com/115984336/215003644-974b7f37-b2b2-4c4f-a2a7-c061bc580461.png"  width="400" height="300">

2. 주요 연관 요인 추출

<전용면적별 세대수> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <지역별 주변 대중교통 수>

<img src="https://user-images.githubusercontent.com/115984336/215004227-fefcaae3-62b0-4c61-b7c4-a5ab6fbafd21.png"  width="300" height="250"> &nbsp;&nbsp; <img src="https://user-images.githubusercontent.com/115984336/215004303-454b50a0-93b8-45a4-b180-1e1dadd1ea3f.png"  width="300" height="250">

<주차면수가 부족한 단지와 많은 단지 수> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<단지별전용면적과 등록차량수의 관계>

<img src="https://user-images.githubusercontent.com/115984336/215004314-15bfde2e-a473-46d1-9b46-91d924f224ee.png"  width="300" height="250"> &nbsp;&nbsp; <img src="https://user-images.githubusercontent.com/115984336/215004504-fbc574a3-d5b8-4386-b082-1e12106e6557.png"  width="300" height="250">

<지역별 등록차량 수 및 주차면 수> 

<img src="https://user-images.githubusercontent.com/115984336/215004423-9eaf68aa-2142-490c-8cc0-eb8fc65f4849.png"  width="500" height="300">

<br/>
<br/>

3. 최소 컬럼 기계학습 진행
    - 훈련 모델 : LinearRegression, RandomForest, Ridge, Lasso
    - 오차 : RMSE, MAE
    - Optimizer : SGD
<br/>
<br/>
4. 딥러닝 진행

<img src="https://user-images.githubusercontent.com/115984336/215004532-ac5b3c49-071e-46c2-a15a-2faa8e42828e.png"  width="350" height="600">  <img src="https://user-images.githubusercontent.com/115984336/215004544-7ae6a6ee-07a3-4cd0-9a68-30be8e6b0204.png"  width="400" height="350"> 
    
5. 실제 데이터와 비교
<img src="https://user-images.githubusercontent.com/115984336/215004551-6c8764ec-06fd-4c6c-9216-b7f51bfbb144.png"  width="500" height="350">


# 결론

- 도경계 지역별 차이 예측 -> 세부 경계 진행시 정밀 예측 예상
