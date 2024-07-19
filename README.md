# Apartment
아파트 실거래가 예측모델 개발
● 목적: 서울 /부산 지역 아파트 실거래가를 예측하는 모델 개발

1. Data OverView

● Train Data: 서울 지역의 약 750,000 거래 데이터, 아파트 거래일, 지역 전용면적, 실거래가 정보
(데이터 소스 원천 - 국토부 거래공개시스템 https://rt.molit.go.kr/pt/xls/xls.do?mobileAt=)

예)
dong: "목동"과 같은 동 명칭에 대한 정보입니다.
apt : “롯데캐슬퍼스트”와 같이 아파트명에 대한 정보입니다.
exclusive_use_area : “35.55”와 같이 매매대상의 전용면적에 대한 정보입니다.
year_of_completion : “2002”과 같이 아파트의 건축 연도를 나타내는 정보입니다.
transaction_year_month : 거래연월을 나타내는 정보입니다.
floor : "3층"과 같이 아파트의 층수를 나타내는 정보입니다.
Top10 : 아파트 시공사 중 상위 10개의 브랜드인지 확인하는 정보입니다.

● Test Data: 실거래가를 제외하고 Train Data와 동일 (27,000여개의 데이터)

외부 데이터
● Park Data: 서울 지역의 공원에 대한 정보 - 공공데이터

● Daycare Center Data: 서울 지역의 어린이집에 대한 정보 - 공공데이터

(추가 예정)
지하철역 위치 정보
버스 정류장 위치 정보
금리 변동 추이
통화량 변동 추이
종합주가지수 변동 추이

Data PreProcessing
데이터 확인 후 데이터 동-구 매치 이상 및 Daycare Center 및 Park 정보가 누락이 된 부분이 있어 공공데이터 행정 사이트 크롤링을 통해 아파트 거래건들 매칭작업 진행 

Train 및 Test 데이터를 구 정보를 Key로하여 공원과 보육시설 정보 통합 진행 완료 및 Train & Test 데이터 재추출

● 아파트 명 괄호제거 및 유명 시공회사 시공여부 등 다양한 값 데이터 전처리 진행 

● Exclusive use Area, Price Log 변환

로그변환 목적:  log의 역할은 큰 수를 같은 비율의 작은 수로 바꿔주고 복잡한 계산을 심플하게 만든다. 로그를 취하는 순간 그 수는 지수가 되어버리니, 값이 작아짐으로써 정규성을 높이고 분석에서 정확한 값을 얻을수 있다.
  
![image](https://github.com/user-attachments/assets/aa10a4b3-5898-4912-a6c8-20b4b88070a2)

● RMSE(Root Mean Square Error) 평균제곱근 오차 사용 

![image](https://github.com/user-attachments/assets/3ecf2bbf-bd77-4322-a7a4-82a5668b6a41)


실제값과 예측값값의 차이를 제곱하여 더한 후 평균을 구하는 값인 MSE를 사용하는데 있어 오차값이 크게 도출되는 경우 속도의 영향을 줄 수 있는 단점이 존재하여 해당되는 식에 Root를 추가한 RMSE를 사용

● Model Selection 
1. LinearRegression

![image](https://github.com/user-attachments/assets/366683a5-edcf-4316-b43a-541c209c91b4)

2. RidgeRegression

![image](https://github.com/user-attachments/assets/27a4dd96-db94-482c-9557-55b314024c93)

3. lassoRegression

![image](https://github.com/user-attachments/assets/88c3d16c-65ca-4ab2-b7b1-77894203cfd3)


4. Elastic Net Regression
   
![image](https://github.com/user-attachments/assets/dd2b96a1-3a69-4868-a64e-8d77d4f0226b)


5. XGBRegressor

   ![image](https://github.com/user-attachments/assets/dba0f447-6380-4144-b4e4-8756a3187bba)

6. LGBMRegressor

![image](https://github.com/user-attachments/assets/dd9f8446-ab20-4bb7-a072-10dcb1ab6730)

● Total Score 

![image](https://github.com/user-attachments/assets/652ef474-2838-47af-a85b-8b8ca7153aea)

● Feature Importance

![image](https://github.com/user-attachments/assets/5e9a0a73-4b57-47f1-a826-4ade1c2e36c8)



