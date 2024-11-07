# VapeCops 프로젝트 🚭

**딥러닝 기반의 실시간 흡연자 감지 시스템**

---

## 개요
VapeCops 프로젝트는 공공장소에서의 흡연 여부를 자동으로 감지하고, 흡연자로 판단될 경우 경고음을 울리는 이동식 로봇 시스템입니다. Python, OpenCV, TensorFlow 등 다양한 딥러닝 및 컴퓨터 비전 기술을 사용하여, 실시간으로 흡연자를 탐지하는 기능을 구현했습니다. 이 프로젝트는 공공장소의 비흡연 환경을 조성하고 관리하는 데 기여할 수 있습니다.

## 주요 기능
- **실시간 흡연자 감지**: MobileNet 모델을 사용해 실시간으로 흡연 여부를 분석합니다.
- **경고음 발생**: 흡연자가 감지되면 경고음을 울려 비흡연 구역 내 금연을 유도합니다.
- **이동식 로봇 플랫폼**: Raspberry Pi 및 Coral USB Accelerator를 탑재한 로봇에 구현하여 이동성과 높은 처리 속도를 확보하였습니다.

## 기술 스택
- **언어**: Python
- **프레임워크 및 라이브러리**: TensorFlow, OpenCV
- **모델**: MobileNet
- **하드웨어**: Raspberry Pi, Coral USB Accelerator

## 설치 및 실행 방법
### 1. 필수 패키지 설치
Python과 필요한 라이브러리를 설치합니다.
```bash
pip install tensorflow opencv-python
```

### 2. 모델 파일 다운로드
사전 학습된 MobileNet 모델 파일을 다운로드하고, 프로젝트 디렉토리 내에 `model` 폴더를 생성하여 넣습니다.

### 3. 코드 실행
Raspberry Pi에서 Coral USB Accelerator를 연결하고, 메인 스크립트를 실행합니다.
```bash
python detect_smoking.py
```

## 프로젝트 구조
```
VapeCops/
├── model/                  # MobileNet 모델 파일
├── scripts/
│   ├── detect_smoking.py   # 메인 실행 파일
│   └── utils.py            # 유틸리티 함수
├── README.md
└── requirements.txt        # 필수 패키지 목록
```

## 결과 및 성과
- 흡연자 감지 정확도: **90% 이상**의 신뢰도로 흡연자를 정확히 감지
- 경고음 발동: 흡연자가 탐지되었을 때 실시간 경고음 발동 기능 구현
- 이동성 확보: 로봇 플랫폼에서의 테스트 완료, 공공장소에서의 이동성 입증

## 참고 자료
- [TensorFlow MobileNet 모델](https://www.tensorflow.org/api_docs/python/tf/keras/applications/MobileNet)
- [Coral USB Accelerator](https://coral.ai/products/accelerator/)

---

이 `README.md`는 프로젝트의 핵심을 깔끔하게 설명할 수 있도록 작성한 예시입니다. 프로젝트의 구체적인 파일이나 명령어에 따라 수정하시면 더욱 완성도 있는 `README.md`가 될 것입니다.
