# EWP 발전 빅데이터 AI 경진대회 : 발전량 예측제도 참여를 위한 풍력 출력 예측
21.11.12. ~ 21.12.28.

  Team Gaon에서 진행한 EWP의 비공개 내부데이터를 이용하여 하루 뒤의 1시간 단위로 24시간 풍력 발전량을 예측하는 프로젝트 입니다. 
  
  내부 데이터와 기상청의 외부 데이터를 이용하여 전처리를 하고 모델링을 하여 예측 결과 EWP 발전 빅데이터 AI 경진대회에서 최종 본선 4위 결과를 얻었습니다.




- 가상환경 VM 에서의 데이터 전처리
    - 이 대회는 비공개 데이터의 보안성 떄문에 가상환경 VM에서 진행이 되었습니다. 따라서 가상환경에서 주피터 노트북을 이용하여 필요한 라이브러리와 외부 데이터를 임포트 해주고 데이터를 전처리 해주었습니다.
    - 기존 비공개 데이터 (발전기 이용율, 위치, 회전 각도, 인버터 전압 등) 와 기상정보 데이터프레임을 결합해주고 이상치를 제거하여 상관관계 분석하여 모델링을 하기 위한 유의미한 변수만 선별하였습니다.

- 데이터 분석 및 모델링
    - 24시간 뒤 발전량이라는 타겟, 선별된 피쳐와 상관계수가 가장 높은 변수 average_winding_temp 의 피쳐 윈도우(24시간을 shift)를 생성해주고 딥러닝 LSTM 을 이용하여 모델을 생성하였습니다.
    - 테스트 셋에 넣어 실제로 모델이 잘 예측을 반영하는지 발전량을 시각화 하여 유의미한 분포가 띈다는 것을 확인하였습니다.

** 자세한 코드는 [클릭](https://github.com/worldpapa/ewp_windpower/blob/main/wind_power.py) 참고 바랍니다. 
