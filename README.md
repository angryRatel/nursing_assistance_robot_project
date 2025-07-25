
# 🤖 ARM 기반 간호 어시스턴트 로봇

> 병원 내 간호사의 반복 업무를 줄이기 위해 약품 전달 및 환자 생체징후 확인이 가능한 ROS2 기반의 간호 어시스턴트 로봇을 개발한 프로젝트입니다.

---
### 📄 더 자세한 내용은 아래의 PDF 또는 발표 자료에서 확인하실 수 있습니다.
---

## 🎥 시연 영상  
[![Demo Video](https://img.youtube.com/vi/MnMJ5cEe0sA/0.jpg)](https://youtu.be/MnMJ5cEe0sA)

## 📑 발표 자료  
https://docs.google.com/presentation/d/1NZCnV38TH0ElrKdvknqc87FGtfnRYHoj/edit?usp=sharing

---

## 1. 📊 개발 과정
### 프로젝트 배경

- 의료 인력 부족과 간호사 업무 과중으로 인한 서비스 질 저하
- 반복적인 간호 업무 자동화 필요성 대두
- 대만 대형 병원 자동화 로봇 도입으로 전문 케어 집중 및 직무 만족도 향상 사례
- 의료 현장의 휴게시간 부족, 과도한 업무량 등 근무환경 문제로 인한 사고 위험

> **목표** :  반복적 간호 업무를 자동화하여 간호사의 업무 부담을 줄이고, 환자에게 집중할 수 있는 의료 환경 조성


###  📅 작업 일정

| 날짜       | 작업 내용 요약                     |
|------------|------------------------------------|
| 2025.06.23 ~ 2025.06.26 | 프로젝트 기획 및 주제 선정 , 기술 검증​    |
| 2025.06.27 ~ 2025.06.28 | robot1 노드 개발 , robot4 노드 개발 |
| 2025.06.29 ~ 2025.06.30  | ROS 서비스 통신 통합 ,  모니터링 GUI 개발 |
| 2025.07.01 ~ 2025.07.03 | MQTT 메시지 통신 통합 ,   바이탈 체크 노드 개발   |
| 2025.07.03 ~ 2025.07.04 | PPT 제작 ,   문서작업   |
| 개발 기간 | 총 11일        |


### 📷 사용 환경
![사용환경](images/사용환경.png)


---


### 🗺 병동 지도
![병동](images/병동.png)
---

## 2. 🛠 주요 기능
- YOLOv8 기반 약품 탐지 및 Depth 위치 추정
- SLAM 기반 자율 주행 및 정밀 지도 작성
- 비접촉 rPPG 방식의 생체징후(심박, SpO2, 혈압) 측정
- MQTT 기반 클라우드 통신 (병동 로봇 위치 동기화)
- Web 기반 GUI: 요청 발송, 위치 확인, 상태 모니터링

---

## 3. 💡 도전 과제 & 해결

| 문제 | 해결 방법 |
|------|------------|
| Depth 해상도 부족 | 해상도를 480p로 향상하여 거리 오차 감소 |
| 영상 압축으로 인한 화질 저하 | `i_low_bandwidth=False` 설정으로 압축 해제 |
| ROS 통신 병합 지연 발생 | MQTT Cloud 기반 통신으로 전환 → 평균 35% 네트워크 절약 |
| 이미지 처리 실시간성 부족 | 병렬 처리 구조 설계 (스레드 분리)로 프레임 지연 감소 |
| rPPG 측정 정확도 부족 | RGB 정규화 + CHROM 필터 적용으로 정확도 개선 |


---

## 4. 👥 팀원 역할 분담
| 이름 | 역할 |
|------|------|
| 백홍하 | Vision, GUI |
| 이하빈 | Vision, ROS 통신 |
| 장연호 | Navigation, MQTT |
| 정찬원 | Navigation, 영상 편집 |
| 이경민, 최정호 | robot1 Vision |
| 문준웅 | robot1 Navigation, GUI |
| 정민섭 | robot1 Navigation, 바이탈 체크 기능 |

프로젝트는 팀원 전체의 협업을 바탕으로 진행되었으며, 핵심 기능은 역할에 따라 분담하여 개발하였습니다

---

## 5. 🎯 성과 및 결과물
- 두 대의 TurtleBot4가 병동 내 협력 자율주행
- 약품 탐지 정확도 95% 이상 달성
- 비접촉 방식의 생체징후 측정 기능 구현
- 실시간 GUI 및 클라우드 기반 통신 환경 구축

---

## 6. 📈 프로젝트 결과 (목표와 성과)
- **목표**: 반복적인 간호 업무 자동화  
- **성과**:
  - 자율 주행 기반 약품 전달 및 환자 위치 접근 성공
  - rPPG 바이탈 체크 기능 탑재
  - 병동 GUI 모니터링 시스템 완성
  - MQTT 기반 병동 내 로봇 간 통신 완성

---

## 7. 📸 프로젝트 화면 및 기능 데모

### 개별 시나리오

---

### 1) 🏥 제조실  
![시나리오 1](https://github.com/user-attachments/assets/f46c4487-bd00-44d8-a1ff-8cf17a8d720c)


#### 상세 동작 흐름

**① 약품 탐지 및 위치 추정**  
- 요청 수신 → Nav2로 선반 앞 도착  
- YOLOv8 모델을 통해 약품 탐지  
- Depth 카메라로 거리 측정 → TF2 변환을 통해 map 좌표 추출  

**② 약품 위치로 이동 및 전달 준비**  
- 추정된 좌표로 로봇 이동  
- MQTT를 통해 robot1과 위치 정보 공유  
- 랑데부 포인트에서 전달 대기  

---

### 2) 🛏 병실  
![시나리오2](https://github.com/user-attachments/assets/72cff4be-17c5-457c-a431-aeaebe92f2b5)

#### 상세 동작 흐름

**① 환자 ID 인식**  
- 병실 도착 후 회전 → ArUco 마커 탐지로 환자 ID 확인  
- 마커 거리 1m 이내 도달 시 정지  

**② 환자 얼굴 감지 및 바이탈 측정**  
- 얼굴 감지 (Face Detection)  
- rPPG 적용: 심박수, 산소포화도, 혈압 추정  
- GUI로 결과 전송  

---

### 3) 🤖 로봇 협업  
![시나리오 3](https://github.com/user-attachments/assets/359776c8-ef37-49c6-985e-9f082ad1503d)

#### 상세 동작 흐름

**① 좌표 공유 및 동기화**  
- robot1: 현재 좌표 → MQTT Publish  
- robot4: 해당 좌표 Subscribe → 이동

**② 랑데부 지점 도착 및 약품 전달**  
- 두 로봇 모두 도착 시 flag 전송  
- robot4 → 약품 전달  
- robot1 → 병실로 출발, robot4 → 도킹 위치 복귀  

---

  
## 8. ✍ 후기 및 향후 개선 사항
- ROS 노드 간 병렬 처리 구조 부족 → 쓰레드 기반 개선 필요
- PID 제어 및 라이다 기반 장애물 회피 추가 예정
- rPPG 영상 처리 지연 → 압축 해제 후 실시간성 확보
- 카메라 센서 향상 및 RGB 필터 튜닝 필요

---

## 9. 🎓 개인적 성찰 및 배운 점
- ROS2 통신 구조와 노드 기반 설계에 대한 실무 이해도 향상
- 네트워크 및 센서 융합 기술 (MQTT, OAK-D) 실습
- 팀원과의 적극적인 협업, 코드 통합 및 실시간 문제 대응 능력 향상
- ROS 환경에서의 자율주행, Vision, GUI 모듈 통합 경험

---

## 10. 🚀 개선 및 확장 아이디어
- PID 제어 기반 정밀 위치 이동 기능 추가
- RFID 기반 약품 관리 및 자동문 연동
- 병실별 스마트 인프라 연계 (IoT 확장)
- 관리자용 GUI 및 모바일 연동 인터페이스 설계
- 긴급 상황 대응용 음성 안내 및 센서 감지 기능 추가

---

### 🧩 시스템 아키텍처
![System Architecture](images/2.png)

### 🧠 Node 아키텍처
![Node Architecture](images/3.png)

### 🔁 System 플로우
![System Flow](images/4.png)

---

> 본 프로젝트는 병원 환경에 특화된 ROS2 기반의 간호 로봇 시스템으로, 자율주행, 비전, 생체 인식, 클라우드 통신, GUI 등을 통합한 종합적 솔루션 구축을 목표로 하였습니다.
