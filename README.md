## ARM 기반 간호 어시스턴트 로봇

## 시연 영상 : https://youtu.be/MnMJ5cEe0sA
## ppt 
#### https://docs.google.com/presentation/d/1NZCnV38TH0ElrKdvknqc87FGtfnRYHoj/edit?usp=sharing&ouid=105592925068746468528&rtpof=true&sd=true

## 📌 프로젝트 개요
본 프로젝트는 **Turtlebot4**과 ROS 2 Humble를 활용하여 병원 내 간호사의 반복적 업무 부담을 줄이기 위해, 약품 전달과 환자 생체징후 확인을 지원하는 로봇을 개발하는 팀 프로젝트입니다.  

---

## 🛠️ 사용 환경
![사용환경](images/사용환경.png)

---

## 🗺 병동 MAP
![병동](images/병동.png)

---

## 🧑‍🤝‍🧑 팀 구성

| 이름 | 역할 |
|------|------|
| 팀장 백홍하 | /robot4/Vision , Main Controller GUI |
| 팀원 이하빈 | /robot4/Vision , ROS 통신 |
| 팀원 장연호 | /robot4/Navigation , EMQX Cloud 통신 |
| 팀원 정찬원 | /robot4/Navigation , 영상 편집 |
| 팀원 이경민 | /robot1/Vision |
| 팀원 최정호 | /robot1/Vision |
| 팀원 문준웅 | /robot1/Navigation , Main Controller GUI |
| 팀원 정민섭 | /robot1/Navigation , 바이탈 체크 기능 개발 |

---

## 📅 작업 일정

| 날짜       | 작업 내용 요약                     |
|------------|------------------------------------|
| 2025.06.23 ~ 2025.06.26 | 프로젝트 기획 및 주제 선정 , 기술 검증​    |
| 2025.06.27 ~ 2025.06.28 | robot1 노드 개발 , robot4 노드 개발 |
| 2025.06.29 ~ 2025.06.30  | ROS 서비스 통신 통합 ,  모니터링 GUI 개발 |
| 2025.07.01 ~ 2025.07.03 | MQTT 메시지 통신 통합 ,   바이탈 체크 노드 개발   |
| 2025.07.03 ~ 2025.07.04 | PPT 제작 ,   문서작업   |
| 개발 기간 | 총 11일        |

---

## 🧩 System 아키텍처
![System Architecture](images/2.png)

## 🧠 Node 아키텍처
![Node Architecture](images/3.png)

## 🔁 System 플로우
![System Flow](images/4.png)




*추가로 알게된 사실*
i_low_bandwidth
압축된 프리뷰 활성화. 고화질 이미지 전송
False
대역폭 줄이기 위한 최적화하면 안나옴 impressed image 안나옴
