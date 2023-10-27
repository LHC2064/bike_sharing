# 공유 자전거 데이터 분석 및 수요 예측
## 개요
코로나19로 인해 공유경제가 빠르게 성장하면서 시장이 확대되고 있다. 그 중 서울시 공유 정책  ’따릉이’ 의 만족도는 매우 높은 것으로 집계 되었다. 자전거 수요 예측이 가능하면 대여소 마다 적절한 자전거 수를 배치할 수 있고, 사람들의 만족도는 더욱 높아질 것이다. 이에 본 프로젝트에서는 자전거 대여수에 영향을 미치는 요인들을 분석하고 자전거 수요를 예측할 수 있는 모델 개발을 목표로 한다.
- 관련 URL
  - “코로나19로 인해 공유경제 빠른 성장 및 시장 확대돼”
    - https://www.busaneconomy.com/news/articleView.html?idxno=262858
  - 서울시 공유정책 이용 만족도 ‘따릉이’가 가장 높아
    - https://www.onews.tv/news/articleView.html?idxno=108365
  - 오·박 시장의 ‘두 바퀴 협치’… 서울시민 두 발이 편해졌다
    - https://go.seoul.co.kr/news/newsView.php?id=20220328012014
## 데이터
- 출처
    - Kaggle 의 ‘London bike sharing dataset’ 활용
    - https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset
- 개수
    - 9개의 columns과 17,414개의 rows로 구성되어 있음
- 변수
    - **cnt** : 시간대별 자전거 이용수
    - **t1** : 실제 온도
    - **t2** : 체감 온도
    - **hum** : 습도(%)
    - **wind_speed** : 풍속(km/h)
    - **Weather_code** : 날씨상태 (1=clear, 2=few clouds, 3=broken clouds, 4=cloudy, 7=rain, 10=rain with thunderstorm, 26=snowfall, 94=freezing fog)
    - **Is_holiday** : 공휴일인지 아닌지 (0=not holiday, 1=holiday)
    - **is_weekend** : 주말인지 아닌지 (0=not weekend, 1=weekend)
    - **season** : 계절 (0=spring, 1=summer, 2=fall, 3=winter)
## 결론
- 요약
    - 기온, 습도가 자전거 이용수와 상대적으로 상관관계가 높았음
    - 평일 출퇴근 시간대 이용수가 많음
    - 평일과 주말이 이용시간대가 차이가 남
    - 여름 (7~9월)에 이용수가 많고, 겨울엔 굉장히 적음
    - 밤 시간대에 이용수가 적음
    - 자전거 대여 수 예측을 위해 is_night, is_rushHour 변수를 적용해보았을 때 is_rushHour 는 의미가 없었지만 is_night 변수는 일부 모델에 효과가 있었음
    - XGboost 알고리즘이 가장 효과적이었음
## 코드
- londonbike.ipynb: EDA 및 모델링 통합 코드
