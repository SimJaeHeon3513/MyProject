# NSMC Sentiment Anlaysis with KLUE-BERT
이 프로젝트는 네이버 영화 리뷰 데이터셋(NSMC)을 활용하여 감성 분류(Sentiment Analysis)를 수행하는 딥러닝 모델 학습 파이프라인입니다.
Pre-trained된 KLUE-BERT-base 모델을 Fine-tuning하여 리뷰의 긍정/부정 여부를 판단합니다.
* * *

## 프로젝트 개요
- 데이터셋: Naver Sentiment Movie Corpus (NSMC)
- 기반 모델: klue/bert-base (한국어 처리에 최적화된 BERT)
- 태스크: 이진분류(Binary Classification - 긍정: 1, 부정: 0)
- 라이브러리: Transformers, Datasets, PyTorch, Scikit-learn

## 상세 수행 과정
### 1. 데이터 전처리 및 정제(Data Proprocessing)
- **노이즈 제거:** 정규표현식을 활용하여 한글과 공백을 제외한 특수문자, 숫자 등을 제거하여 학습 효율을 높였습니다.
- **결측치 및 중복 처리:** 전처리 후 발생한 빈 문자열과 중복된 리뷰 데이터를 제거하여 데이터의 품질을 확보했습니다.
- **데이터 구성:** 약 15만 건의 훈련 데이터와 5만 건의 테스트 데이터를 사용하여 모델의 일반화 성능을 검증했습니다.

### 2. 토크나이징 및 데이터셋 구축(Tokenization)
- **KLUE-BERT Tokenizer:** klue/bert-base 전용 토크나이저를 사용하여 한국어 특성에 맞는 토큰화를 수행했습니다.
- **데이터 규격화:** 최대 문장 길이를 64로 설정하고, Padding 및 Truncation을 적용하여 모델 입력 규격을 통일했습니다.
- **Hugging Face Datasets:** 효율적인 데이터 관리를 위해 datasets 라이브러리를 활용하여 학습용/검증용 데이터셋을 구축했습니다.

### 3. 모델학습(Model Training)
- **Fine-tuning:** 사전학습된 BERT 모델 위에 분류 헤드(Classification Head)를 추가하여 NSMC 데이터에 최적화했습니다.
- **학습설정:**
  - Epochs: 3
  - Batch Size: 32
  - Optimizer: AdamW
  - Mixed Precision: fp16을 적용하여 GPU 메모리 사용량을 최적화하고 학습 속도를 향상시켰습니다.
- 최적 모델 저장: 학습 과정 중 검증 성능이 가장 높은 지점의 가중치를 자동으로 저장하도록 설정했습니다.

### 4. 성능 평가(Evalutation)
- **평가 지표:** Accuracy(정확도), Precision(정밀도), Recall(재현율), F1-score를 통해 모델을 다각도로 평가했습니다.
- **최종 성능:** 테스트 데이터셋 기준 약 89%의 정확도를 달성했습니다.
- **시각화:** Confusion Matrix를 통해 긍정/부정 각각의 분류 성능을 시각적으로 확인했습니다.

### 프로젝트 결과 및 기대 효과
- **한국어 특화 성능:** 일반 BERT 모델보다 한국어 언어 특성을 잘 반영하는 KLUE-BERT를 사용하여 높은 분류 정확도를 확보했습니다.
- **감성 분석 활용:** 구축된 파이프라인은 여오하 리뷰뿐만 아니라 쇼핑물 후기, 커뮤니티 반응 분석 등 다양한 한국어 텍스트 감성 분석 서비스로 확장 가능합니다.










