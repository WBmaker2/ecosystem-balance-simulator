# 🌿 나만의 작은 생태계 균형 시뮬레이터 (Ecosystem Balance Simulator)

[![GitHub Pages](https://img.shields.io/badge/Demo-Live%20Preview-brightgreen?style=for-the-badge&logo=github)](https://wbmaker2.github.io/ecosystem-balance-simulator/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](LICENSE)

> **초등학교 5~6학년 과학 '생물과 환경(생태계 평형)' 단원 연계형 인터랙티브 웹 시뮬레이터**입니다.  
> 외부 API나 라이브러리 설치 없이 순수 클라이언트 사이드(HTML5 Canvas, Boids 자율 에이전트 엔진, Web Audio API 사운드 신시사이저)로 동작합니다.

👉 **[라이브 시뮬레이터 바로가기 (GitHub Pages)](https://wbmaker2.github.io/ecosystem-balance-simulator/)**

---

## 📸 주요 기능 및 화면 구성

```mermaid
flowchart LR
    A["🌱 생산자 (토끼풀)<br/>광합성 성장 & 씨앗 번식"] -->|섭식| B["🐇 1차 소비자 (초원토끼)<br/>Boids 군집 & 천적 회피"]
    B -->|포식| C["🦊 2차 소비자 (붉은여우)<br/>미래 경로 예측 추격"]
    C -.->|사체 및 분해| A
```

### 1. 🐇 자율 에이전트 행동 엔진 (Boids + FSM)
- **생산자 (토끼풀)**: 햇빛과 수분에 비례하여 성장하며 씨앗을 퍼뜨립니다. 초반 전멸 방지를 위한 '휴면 뿌리 발아 시스템'이 내장되어 있습니다.
- **1차 소비자 (초원토끼)**: 평상시 무리를 지어 배회(Wander & Flock)하고, 배가 고프면 성체 풀을 찾아 먹으며(Seek), 여우를 발견하면 최대 속력으로 도주(Flee)합니다.
- **2차 소비자 (붉은여우)**: 토끼의 예상 이동 경로를 계산하여 날렵하게 추격(Pursuit)하고, 동족 간 영역을 유지(Separation)합니다.

### 2. 📈 실시간 데이터 대시보드
- **시계열 꺾은선 그래프 (Time-Series Chart)**: 풀, 토끼, 여우의 개체 수 변동 궤적(로트카-볼테라 평형 파동)과 환경 이벤트 마커를 실시간으로 표시합니다.
- **생태계 피라미드 (Trophic Pyramid)**: 현재 개체 수 비율을 3단 블록으로 시각화하며, 평형이 깨졌을 때 시각적 경보(Shake 애니메이션)가 울립니다.

### 3. 🎯 교과서 연계 3대 탐구 미션
1. **미션 1 [기초 탐구] "평화로운 초원 유지하기"**: 45초 동안 세 생물종이 모두 멸종하지 않고 안정적인 피라미드 비율을 유지하기
2. **미션 2 [역사적 사례] "카이바브 고원의 비극"**: 포식자(여우)가 사라졌을 때 일어나는 초식동물 폭증과 초원 황폐화 관찰 및 형성평가 퀴즈
3. **미션 3 [위기 극복] "갑작스러운 가뭄 위기 극복"**: 풀이 자라지 않는 가뭄 재해 속에서 물 공급과 개체 조절로 생태계 붕괴 막기

### 4. 🎛️ 인터랙티브 조작 도구
- **생물 브러시**: 풀 심기, 토끼 놓기, 여우 놓기, 지우개 도구로 마우스 드래그 및 터치 조작 지원
- **개체 돋보기 HUD**: 특정 동물을 클릭하여 시야 반경(FOV), 목표물 추적 화살표, 에너지 게이지 실시간 관찰
- **환경 변수 슬라이더**: 일조량/강수량, 최대 풀 수용량(K), 토끼 대사량, 여우 속력 조절
- **Web Audio API 절차적 사운드**: 섭식음, 사냥음, 번식 차임벨, 경보음, 미션 성공 팡파르

---

## 🚀 로컬 실행 방법

별도의 서버 설치나 빌드 과정 없이, 브라우저에서 `index.html`을 더블 클릭하면 즉시 실행됩니다.

```bash
# 1. 저장소 클론
git clone https://github.com/WBmaker2/ecosystem-balance-simulator.git

# 2. 브라우저로 실행
open index.html # macOS
```

---

## 🛠️ 기술 스택
- **Markup & Styling**: HTML5, Tailwind CSS (CDN), Pretendard Font
- **Rendering**: HTML5 Canvas 2D API (Dual Canvas: 월드 캔버스 + 실시간 그래프/피라미드)
- **Audio**: Web Audio API (내장 주파수 합성, 무외부 의존성)
- **Optimization**: Spatial Hash Grid ($O(N)$ 근접 이웃 탐색)

---

## 📄 라이선스
MIT License
