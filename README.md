# VapeCops 프로젝트 🚭

**딥러닝 기반의 실시간 흡연자 감지 및 경고 시스템**

---

## 개요
VapeCops 프로젝트는 공공장소에서 흡연 여부를 실시간으로 감지하고, 흡연자로 판단되면 경고음을 울리는 이동식 로봇 시스템입니다. 딥러닝과 컴퓨터 비전 기술을 활용해 공공장소의 비흡연 환경 조성을 목표로 합니다.

## 주요 기능
- **실시간 흡연자 감지**: MobileNet 모델을 통해 흡연 여부를 실시간으로 분석합니다.
- **경고음 발생**: 흡연자가 감지되면 경고음을 울려 비흡연 구역 내 금연을 유도합니다.
- **이동식 로봇 플랫폼**: Raspberry Pi 및 Coral USB Accelerator를 탑재한 로봇에 모델을 배포하여 원활한 실시간 감지가 가능합니다.

## 기술 스택
- **언어**: Python
- **프레임워크 및 라이브러리**: TensorFlow, OpenCV
- **모델**: MobileNet
- **환경**: Jupyter Notebook(모델 학습), Raspberry Pi(모델 배포)

## 설치 및 실행 방법

### 필수 요구사항
- **Python 3.8** (라즈베리파이와 Jupyter Notebook 환경에서 Python 3.8을 권장)
- **가상환경 사용 권장**

### 1. Jupyter Notebook에서 모델 학습하기
프로젝트는 Jupyter Notebook 환경에서 학습 코드를 실행하여 모델을 트레이닝합니다. 가상환경을 설정한 후, 아래 명령어로 노트북 환경을 실행하세요.
```bash
jupyter notebook
```

**학습 코드 실행**: `smoking_classification.ipynb` 파일을 열어 MobileNet 모델을 트레이닝합니다. 학습이 완료되면 모델 파일(.tflite)을 다운로드하여 저장합니다.

### 2. 라즈베리파이에 모델 배포하기

#### 1) 라즈베리파이 설정 및 필수 패키지 설치
라즈베리파이에서 프로젝트를 클론한 후, `requirements.txt` 파일을 사용하여 필요한 패키지를 설치합니다.
```bash
sudo apt update
sudo apt install python3-pip
pip3 install -r requirements.txt
```

#### 2) 모델 파일 및 스크립트 배포
트레이닝 완료 후 생성된 모델 파일(.tflite)을 라즈베리파이로 전송합니다. USB, scp 등 방법으로 파일을 복사한 뒤, 프로젝트 디렉토리에 배치합니다.

#### 3) Coral USB Accelerator 설정 (필요한 경우)
```bash
echo "deb https://packages.cloud.google.com/apt coral-edgetpu-stable main" | sudo tee /etc/apt/sources.list.d/coral-edgetpu.list
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
sudo apt update
sudo apt install libedgetpu1-std
```

### 3. 데이터셋 준비

사용자가 직접 데이터셋을 준비해야 합니다. 데이터셋은 다음과 같은 구조를 따라야 합니다:
```
data/
├── train/
│   ├── smoking/
│   │   ├── image1.jpg
│   │   ├── image2.jpg
│   └── notsmoking/
│       ├── image1.jpg
│       └── image2.jpg
├── validation/
│   ├── smoking/
│   │   ├── image1.jpg
│   └── notsmoking/
│       └── image1.jpg
```

데이터셋은 `train`과 `validation` 폴더로 구성되며, 각각 `smoking` 및 `notsmoking` 폴더가 필요합니다. 이미지 파일은 각 폴더에 맞는 클래스에 배치해 주세요.

### 4. 프로젝트 실행
라즈베리파이에서 아래 명령어로 흡연자 감지 시스템을 실행합니다.
```bash
python3 detect_smoking.py
```

## 프로젝트 구조
```
VapeCops/
├── model/                        # 학습된 MobileNet 모델 파일
├── scripts/
│   ├── detect_smoking.py         # 라즈베리파이 실행 스크립트
│   └── utils.py                  # 유틸리티 함수
├── notebooks/
│   └── smoking_classification.ipynb # Jupyter Notebook 학습 코드
├── README.md
└── requirements.txt              # 필수 패키지 목록
```

## 결과 및 성과
- 흡연자 감지 정확도: **90% 이상의 신뢰도**
- 실시간 경고음 발동 기능 구현 완료
- 로봇 이동성 확보를 통해 공공장소에서의 비흡연 환경 조성 기여

## 참고 자료
- [TensorFlow MobileNet 모델](https://www.tensorflow.org/api_docs/python/tf/keras/applications/MobileNet)
- [Coral USB Accelerator](https://coral.ai/products/accelerator/)

---

이제 Python 3.8과 가상환경 사용 권장 사항이 포함되어, 프로젝트 환경 설정이 더욱 명확해졌습니다.
