# Port8090 MiniProject

### 🍀 Member

<table>
  <tbody>
    <tr>
      <td align="center"><a href="https://github.com/dayeah512"><img src="https://avatars.githubusercontent.com/u/145834715?v=4" width="100px;" alt=""/><br /><sub><b>남다예</b></sub></a><br /><sub><b>팀원</b></sub><br /></td>
      <td align="center"><a href="https://github.com/byepingu"><img src="https://avatars.githubusercontent.com/u/145783010?v=4" width="100px;" alt=""/><br /><sub><b>변영은</b></sub></a><br /><sub><b>팀원</b></sub><br /></td>
      <td align="center"><a href="https://github.com/hyul77"><img src="https://avatars.githubusercontent.com/u/100561170?v=4" width="100px;" alt=""/><br /><sub><b>이준혁</b></sub></a><br /><sub><b>팀원</b></sub><br /></td>
      <td align="center"><a href="https://github.com/bbundnam"><img src="https://avatars.githubusercontent.com/u/145851524?v=4" width="100px;" alt=""/><br /><sub><b>정세홍</b></sub></a><br /><sub><b>팀원</b></sub><br /></td>
      <td align="center"><a href="https://github.com/soljeong"><img src="https://avatars.githubusercontent.com/u/72812330?v=4" width="100px;" alt=""/><br /><sub><b>정솔</b></sub></a><br /><sub><b>팀원</b></sub><br /></td>
      <td align="center"><a href="https://github.com/DaSeul-Seo"><img src="https://avatars.githubusercontent.com/u/67898022?v=4" width="100px;" alt=""/><br /><sub><b>서다슬</b></sub></a><br /><sub><b>팀장</b></sub><br /></td>
    </tr>
  </tbody>
</table>

### 📽️ 시연영상

https://github.com/DaSeul-Seo/Port4045/assets/67898022/2b5ced5c-610b-425b-aaf7-50b20c8976c5

### ✍️ 개발 목적 및 목표

- 본 프로젝트는 Crawling으로 구한 Data를 Hadoop에 축적하고 필요한 Data를 꺼내 활용하며 Yolo를 통해 Object Detection를 구현해 Django로 서비스를 제공하는 Port8090팀의 미니 프로젝트이다.
- 비정형 데이터인 Image를 커스텀 학습 모델인 Yolo를 통해 Labeling을 할 수 있게 된다. 이를 통해 Input으로 받을 정보들 중 text뿐만 아니라 Image를 받아 처리할 수 있게 된다.
- 현재 서비스를 지원할 때 Input을 받아 처리할 수 있는 형태는 text가 제일 편하다. 하지만 앞으로 Port8090팀이 본 Project를 진행할 때 음식 관련한 아이디어를 가지고 있기 때문에 text뿐만 아니라 Image를 Input을 받아 다양한 서비스를 제공할 수 있는 토대를 문서로 기록해 서비스를 구축하고자 한다.
- 시작날짜 : 2024년 01월 23일
- 완료날짜 : 2024년 01월 26일

### 🛠 개발환경 및 아키텍쳐

![dev_environment](./readMeImg/dev_environment.png)

![flow](./readMeImg/flow.svg)


## 🖥️ Crawling
1. 개인 크롤링 작업
2. 최종
  - 구글 이미지 검색
  - 총 18,336 데이터 수집
  - 정제 총 18,280 데이터 완료

## 🧠 Deep Learning (YOLOv8)
- YOLO (You Only Looks Once)sms 빠른 처리속도를 이용하여 실시간 Object detection이 가능한 딥러닝 모델
- YOLOv5
  - 2020년 6월 출시
  - YOLOv4와 비교하여 객체 검출 정확도에서 10% 이상 향상되었으며, 더 빠른 속도와 더 작은 모델 크기를 가짐
- YOLOv8
  - 2023년 1월 출시
  - 개체 감지, 인스턴스 세분화 및 이미지 분류 모델을 train하기 위한 통합 프레임워크 로 구축됨
- YOLOv8를 사용한 이유
  - 가장 최신의 모델을 사용하기 위해
### 1. V1

| DataSet  | Labels | Pre-Trained Model Version |
| :---:         |     :---:      |          :---: |
| Train : 16636개의 jpg 파일  | 822개 Labels | YOLOv8n.pt |
| Valid : 1644개의 jpg 파일  |   |

### 2. V2

#### GPU

| DataSet  | Labels | Pre-Trained Model Version |
| :---:         |     :---:      |          :---: |
| Train : 16636개의 jpg 파일  | 822개 Labels | YOLOv8m.pt |
| Valid : 1644개의 jpg 파일  |   |

#### CPU

| DataSet  | Labels | Pre-Trained Model Version |
| :---:         |     :---:      |          :---: |
| Train : 14624개의 jpg 파일  | 15개 Labels | YOLOv8n.pt |
| Valid : 3656개의 jpg 파일  |   |

### 3. V3

| DataSet  | Labels | Pre-Trained Model Version |
| :---:         |     :---:      |          :---: |
| Train : 1200개의 jpg 파일  | 10개 Labels | YOLOv8n.pt |
| Valid : 300개의 jpg 파일  |   |

### V3 Results
![0](./readMeImg/val_batch0_labels.jpg)
![1](./readMeImg/hamberger.png)
![2](./readMeImg/bread.png)
![3](./readMeImg/ghamberger.png)


## 💡 Issue
### Crawling
1. Selenium Version 문제
    - 웹크롤링시, XPATH 표기법의 변경으로 인해 동일한 사진만 저장되는 경우 발생
    - ❗ 문법 업데이트에 유의 필요

2. 세션을 유지하지 않고 여러 차례 request를 보내서 사이트에서 접속 차단당한 이슈.

### YOLO
1. 예측 결과 사진파일에 바운딩박스가 미검출.
    - 학습 조건
      - class 10
      - train_img 100
      - valid_img 50
      - epoch 10
      - model version : YOLOv5
    - 원인
      - 학습량이 지나치게 적은 나머지 confidence score가 confidence threshold를 넘지 못해서 생긴 이슈.
      - 성능이 중요하지 않은 상황이라도 어느 정도는 정확성에 의의를 둬야 함.

### Hadoop
1. Hadoop을 사용하지 않을 수 없을 만큼 많은 양의 데이터를 수집하려고 했지만, 크롤링이 생각보다 쉽지 않았다.

### Django Web
1. 이미지 경로 문제
    - 결과 화면에서 출력하는 것이 목표
    - 이미지 경로를 static 폴더로 하지 않으면, url 문제가 발생
      - 출력화면 url이 이미지 파일의 root 경로로 작용하기 때문
      - ex. 원하는 경로는 'A/B/d.jpg'인데, 현재 화면이 'A/B/C'라서, img src='d.jpg'로 이미지 경로 지정해도 'A/B/C/d.jpg'로 찾아감
    - 임시방편으로, static 폴더 안에 결과 이미지(result.jpg) 저장하여 {% static 'result.jpg' %}로 해결
2. DB 꼬임 문제
    - DB model 변경하면서 생긴 문제
    - migration 폴더 삭제해도 해결되지 않아 기존 DB 초기화 후 DB 재접속, 초기화하여 해결

## ⭐ 개선점
### Dev
- 학습 전 이미지 전처리
- 예측 결과 이미지에서 동일 라벨이 추출되었을 경우 confidence score가 가장 높은 값만 선택해서 표시
- 예측 결과 이미지 Filter 적용 문제 해결 필요
- 결과를 csv 파일로 저장해서 진행 => DB로 했어야 함
