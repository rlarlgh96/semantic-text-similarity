# Semantic Text Similarity(STS)

## 프로젝트 개요
### 대회 소개
<img width="750" src="https://github.com/rlarlgh96/semantic-text-similarity/assets/121072239/b1a8bf53-3704-4291-9618-a1045d4a3d55"><br>
본 프로젝트는 네이버 부스트캠프 AI Tech 6기 NLP 트랙 과정에서 진행한 교육용 대회 프로젝트이다.<br>
Semantic Text Similarity(STS)는 두 문장이 얼마나 유사한지 판단하는 NLP task로, 본 대회에서는 Bert 모델을 사용해 입력으로 주어진 두 문장의 문맥적 유사도를 측정한다.

## 프로젝트 수행 과정
### EDA
- 학습 데이터셋에서 label 분포를 확인한 결과, 다음과 같이 불균형한 분포를 보였다.<br>
<img width="500" src="https://github.com/rlarlgh96/semantic-text-similarity/assets/121072239/80fba964-4337-4fa2-ae38-8a3fe8bb0826"><br>
<img width="500" src="https://github.com/rlarlgh96/semantic-text-similarity/assets/121072239/0aaf3cd0-cbe4-4087-9a85-16585470beb5"><br>

### Data Augmentation
#### Sentence Swap
- 모든 데이터에 대해 sentence1와 sentence2를 뒤바꿔 데이터를 2배로 증강했다.

#### Sentence Copy and Reversal
- label이 0.0점인 데이터로부터 sentence1과 sentence1을 쌍으로 갖는 데이터를 만들어 5.0점 데이터를 증강했다.
- label이 5.0점인 데이터로부터 sentence1과 sentence1을 뒤집은 문장을 쌍으로 갖는 데이터를 만들어 0.0점 데이터를 증강했다.

#### Data Resampling
- 데이터셋의 label 불균형 문제를 해소하기위해 Data Resampling을 진행했다.
- label을 정수 범위(0-1, 1-2, 2-3, 3-4, 4-5)로 나누어 데이터가 가장 많은 범위를 기준으로 오버샘플링을 적용했다.<br>
<img width="500" src="https://github.com/rlarlgh96/semantic-text-similarity/assets/121072239/75fd1793-2a97-4d5a-9bb8-b645957eef68"><br>

## 프로젝트 수행 결과
- 평가 데이터셋에서 모델의 성능이 0.0018점 향상되었다.
  
  | model | score |
  |--------|--------|
  | Baseline | 0.8908 |
  | Data Augmentation | 0.8926 |

## 참고문헌
- Wei, J., & Zou, K. (2019). ***EDA: Easy Data Augmentation Techniques for Boosting Performance on Text Classification Tasks***. 	arXiv:2105.09680 [cs.CL].
