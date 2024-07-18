# Apartment
아파트 실거래가 예측모델 개발
● 목적: 서울 /부산 지역 아파트 실거래가를 예측하는 모델 개발

1. Data OverView

● Train Data: 서울/부산 지역의 약 1,100,000 거래 데이터, 아파트 거래일, 지역 전용면적, 실거래가 정보
(데이터 소스 원천 - https://rt.molit.go.kr/pt/xls/xls.do?mobileAt=)

● Test Data: 실거래가를 제외하고 Train Data와 동일

● Park Data: 서울/부산 지역의 공원에 대한 정보

● Daycare Center Data: 서울/부산 지역의 어린이집에 대한 정보

Data PreProcessing
데이터 확인 후 데이터 동-구 매치 이상 및 Daycare Center 및 Park 정보가 누락이 된 부분이 있어 공공데이터 행정 사이트 크롤링을 통해 아파트 거래건들 매칭작업 진행 

기존 파일에서 Dong에 대한 정보가 다 담겨있지 않아 데이터 매핑 및 Park에 대한 데이터에서는 마포구, 성북구가 존재하지 않아 이부분에 대한 정보 생성

Train 및 Test 데이터를 구 정보를 Key로하여 공원과 보육시설 정보 통합 진행 완료 및 
