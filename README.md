🚨 Scream Detection Project
공장 내 응급 상황 감지를 위한 딥러닝 기반 비명 인식 및 특성 분석 프로젝트입니다.

📂 파일 설명 
1. analysis.ipynb
역할: 프로젝트 초기 탐색 및 데이터 검증용 노트북입니다.

주요 내용:

원본 음성 데이터(.wav)의 로드 및 파형 확인.

Mel-spectrogram 전처리 로직의 기초 설계.

초기 모델 아키텍처 구성 및 기본 성능 테스트.

미사용 이유:

전처리 로직의 구버전: 최신 모델에서 사용하는 노이즈 제거(Denoising) 및 데이터 증강(Augmentation) 로직이 포함되어 있지 않아 현재 모델과 호환되지 않습니다.

구조적 한계: 초기 설계 단계의 단순 CNN 모델로, 복잡한 환경에서의 오탐(False Positive)율이 높고 클러스터링 기반의 세부 분석 기능이 누락되어 있습니다.

호환성 문제: 프로젝트 진행 중 변경된 데이터 경로 및 라이브러리 버전(Keras 3 대응 등)이 반영되지 않아 실행 시 오류가 발생할 수 있습니다.

2. analysis_v2.ipynb (Main)
역할: analysis.ipynb의 한계를 극복하기 위해 재설계된 최신 버전입니다. 성능 고도화 및 상세 분석(성별/국적 추론)이 포함된 최종 작업 노트북입니다.

개선점: 99.8%의 정확도를 달성한 최종 모델과 KMeans 클러스터링을 활용한 상세 판독 로직이 완벽하게 통합되어 있습니다.

주요 내용:

고도화된 전처리: 노이즈 제거 기능이 포함된 preprocess_v2_denoise 적용.

모델 학습: CNN(Convolutional Neural Network) 기반 모델로 정확도 99.8% 달성.

비지도 학습(Clustering): 라벨이 없는 데이터에서 AI가 스스로 특징을 추출하여 성별 및 상황별 그룹화(K-Means Clustering).

통합 판독기: 음성 파일 입력 시 **[비명 여부 / 성별 추정 / 상황 상세 / 확신도]**를 통합 출력하는 함수 구현.

🛠️ 주요 기술 스택 (Tech Stack)
언어: Python 3.12

라이브러리: TensorFlow/Keras, Librosa, Scikit-learn, Matplotlib, NumPy

모델: 2D Convolutional Neural Network (CNN)

📈 프로젝트 성과 (Key Results)
High Accuracy: 테스트 데이터셋 기준 99% 이상의 높은 비명 감지 성공률 확보.

Data Grouping: t-SNE 및 PCA 시각화를 통해 비명 데이터 내의 성별/국적별 특징적 군집 확인.

Practical Implementation: 공장 현장 도입을 고려한 파일 단위 실시간 판독 로직 완성.
