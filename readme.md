# 질병별 중환자실 입실 기간 예측 프로젝트 (ICU Length of Stay Prediction by Disease Type)
> ⚠️Alert: DATASET NOT INCLUDED because of License issue

### 프로젝트 소개

고령화로 인해 중환자실 수요가 증가하고 있으나, 공급이 이를 따라가지 못하고 있으며, 의료 파업 등으로 인해 가용 중환자실 병상도 감소하고 있습니다. 본 프로젝트는 이러한 문제를 해결하기 위해 MIMIC-IV 데이터셋을 활용하여 중환자실 입실 기간(Length of Stay, LOS)을 예측하는 모델을 구현합니다.

### 주요 기능 요약

- **데이터 전처리**: 결측치 처리, 이상치 제거, 시계열 변환 등
- **모델 학습**: RNN, LSTM, GRU, Transformers 모델을 이용한 ICU 입실 기간 예측
- **성능 평가**: MAE, MSE, R²를 통한 성능 평가 및 모델 튜닝
- **결과 해석**: 예측 결과 및 성능 지표를 통한 결과 해석과 활용 방안 제시

### 프로젝트 목표

1. ICU 환자의 입실 기간 예측 (Length of Stay, LOS)
2. 예측에 가장 유의한 생체 신호(feature)와 시계열 단위 탐색

이 프로젝트는 병원 자원 관리 최적화를 통해 환자 관리 효율성을 높이는 것을 목표로 합니다.

### 프로젝트 실행 방법

1. **환경 설정**: Python 3.8 이상, 가상 환경 생성 후 필요한 라이브러리 설치 (`requirements.txt` 파일 참고)
2. **데이터 다운로드**: MIMIC-IV 데이터셋 다운로드 및 필요한 csv 파일 준비
3. **전처리 및 EDA 수행**: `preprocessing.py` 파일 실행
4. **모델 학습**: `train_model.py` 파일을 사용하여 심혈관 및 감염성 질병 데이터에 대한 모델 학습
5. **결과 분석**: 학습된 모델을 이용해 예측 결과를 시각화 및 분석
    
### 활용 데이터셋

- **patients.csv**: 환자의 기본 정보 (성별, 나이, 인종 등)
- **icustays.csv**: ICU 입원 기간 정보
- **chartevents.csv**: 환자의 생체 신호 정보
- **diagnoses_icd.csv**: 환자의 진단 정보
- **d_icd_diagnoses**: 진단 내용 사전
- **d_items.csv**: 이벤트 내용 사전

### 모델 학습 방법

#### 심혈관 질병 데이터셋

- **데이터 준비**: 심혈관 데이터셋 (6, 12, 18시간), 데이터 스케일링, 시계열 구조 변환
- **모델 구조**: RNN, LSTM, GRU, Transformers  모델을 기본으로 사용하며, Attention 및 Dropout 기법을 적용하여 모델 성능을 향상시킴
- **성능 평가**: MAE, MSE, R² 평가 지표 사용, Validation 및 Training Loss 시각화

#### 감염성 질병 데이터셋

- **데이터 준비**: 감염성 데이터셋 (6, 12, 18시간), 데이터 스케일링, 시계열 구조 변환
- **모델 구조**: RNN, LSTM, GRU, Transformers 모델과 함께 Attention 및 Dropout 기법 적용
- **성능 평가**: MAE, MSE, R² 평가 지표 사용, Validation 및 Training Loss 시각화

### 주요 생체 신호

- **심혈관 질병 환자**: 심박수, 동맥혈압(수축기/이완기), 호흡수, 혈당, 체온, 산소 포화도 등 16가지 지표
- **감염성 질병 환자**: 심박수, 동맥혈압, 호흡수, 혈당, 글래스고 혼수 척도(GCS) 점수 등 15가지 지표

### 결과 해석 및 인사이트

- **심혈관 질병**: 18시간 단위의 데이터로 모델 학습 시 가장 낮은 MAE와 RMSE 값을 보였으며, 긴 시간 단위의 데이터가 모델 학습에 유리함을 확인
- **감염성 질병**: 6시간 단위와 18시간 단위에서 비슷한 성능을 보였으며, 시간 단위의 변화가 모델 성능에 큰 영향을 미치지 않음

### 프로젝트 한계점

1. 샘플 수가 적어 환자 그룹을 감염성 및 심혈관계 질병 환자로 한정함
2. 시간 부족으로 인해 시간 구간을 6, 12, 18시간으로 한정
3. 다중 진단 환자의 복잡성을 충분히 반영하지 못함

### 사용 기술 및 도구

- **프로그래밍 언어**: Python
- **라이브러리**: NumPy, Pandas, Scikit-learn, TensorFlow, Keras
- **시각화 도구**: Matplotlib, Seaborn
- **EDA 및 전처리**: 결측치 보간, 이상치 처리, 데이터 스케일링, 시계열 변환
  
### 참고 문헌

- [MIMIC-IV 데이터 세트와 기준 알고리즘의 공정성 평가: ICU 입원 기간 예측에 대한 응용, 컬럼비아 대학](https://ar5iv.labs.arxiv.org/html/2401.00902)
- [Prediction of Intensive Care Unit Length of Stay in the MIMIC-IV Dataset](https://www.mdpi.com/2076-3417/13/12/6930)

### 팀 구성

- 김수성, 노은선, 백지헌, 윤지형

### 라이선스

이 프로젝트는 MIT 라이선스를 따릅니다.



