# NSMC Sentiment Anlaysis with KLUE-BERT
이 프로젝트는 네이버 영화 리뷰 데이터셋(NSMC)을 활용하여 감성 분류(Sentiment Analysis)를 수행하는 딥러닝 모델 학습 파이프라인입니다.
Pre-trained된 KLUE-BERT-base 모델을 Fine-tuning하여 리뷰의 긍정/부정 여부를 판단합니다.
* * *

## 프로젝트 개요
- 데이터셋: Naver Sentiment Movie Corpus (NSMC)
- 기반 모델: klue/bert-base (한국어 처리에 최적화된 BERT)
- 태스크: 이진분류(Binary Classification - 긍정: 1, 부정: 0)
- 라이브러리: Transformers, Datasets, PyTorch, Scikit-learn
