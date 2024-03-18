
2023 하계 을지대학교 데이터청년캠퍼스

-   개발 기간 : 23.08.01 ~ 23.08.28
-   사용기술 : EC2,Lambda,Route53,SES,Cognito,DynamoDB,React
-   수상 : 데이터 청년 캠퍼스 우수상 & 클라우드(AWS) 1위
-   맡은 일 : 서버, 백엔드


---

## 1\. 프로젝트 소개

AI MEDICO는 외국인 환자를 대상으로 실시간 통역, 진단 번역, 환자 관리 등을 도와주는 AI 의료 코디네이터 서비스

<img width="576" alt="스크린샷 2024-02-18 오전 10 52 44" src="https://github.com/ejehoon/samo-web1/assets/78858687/8b72ef46-beba-4242-9ffc-76fec70236cc">



## 2\. 프로젝트 목표

AWS 서비스와 openAI gpt를 활용하여 국내 병원에서 외국인 환자들에게 향상된  
진료 서비스를 제공할 수 있는 서비스를 제안

## 3\. 프로젝트 구성원 및 추진체계

### 프로젝트 추진 체계

1.  계획

-   프로젝트 목표 및 방향 설정
-   리소스, 일정, 예산 수립
-   우선순위 결정

2.  설계

-   아키텍처 구성도 구축
-   AWS Tool 선택
-   웹디자인 기획

3.  개발

-   서버 환경 및 웹 개발
-   주요 기능 개발
-   보안 개발

4.  테스트

-   서비스 정확성 및 성능 테스트
-   오류 점검  
    → 지속적인 피드백을 통한 애자일 방법 추진

프로젝트 일정

<img width="749" alt="스크린샷 2024-02-18 오전 10 53 38" src="https://github.com/ejehoon/samo-web1/assets/78858687/a0b8a901-766b-4299-9e67-f9cd145eaed6">


프로젝트 구성도

<img width="750" alt="스크린샷 2024-02-18 오전 10 53 48" src="https://github.com/ejehoon/samo-web1/assets/78858687/5339027f-cf90-499c-b089-5d546e37aab0">


프로젝트 아키텍처

-   AWS 내 사용 서비스

1.  Cloud9 내에서 Amplify 생성
2.  GPT API 연결시키기 위해 Lambda 생성
3.  GraphQL 이용하여 1:N 관계의 DynamoDB 생성
4.  Cognito 사용자 정보의 DynamoDB 생성(Lambda 이용) 5 DynamoDB의 내용을 백업해두기 위해 S3 생성
5.  환자에게 정보를 이메일로 전송하기 위해 SES 생성
6.  Route 53을 통해 도메인 연결

<img width="745" alt="스크린샷 2024-02-18 오전 10 54 02" src="https://github.com/ejehoon/samo-web1/assets/78858687/0b551cda-0dcb-4426-a8b7-e6c5759156c5">



## 4\. 프로젝트 기능

**1\. Login:** 병원 관리자의 계정 생성 및 이용

<img width="763" alt="스크린샷 2024-02-18 오전 10 58 25" src="https://github.com/ejehoon/AI_Medico/assets/78858687/5ce43a8b-30dd-4a32-9696-48cd5373b221">



**2\. Script :** 외국인 환자와 의사 간의 실시간 대화를 음성 혹은 텍스트 입력 (react내부에서 제공하는 음성인식 기능 사용)  
→ 음성에서 텍스트로 변환된 것 혹은 텍스트 입력된 것이 연결된 OPEN AI인 GPT를 이용하여 실시간 번역

<img width="772" alt="스크린샷 2024-02-18 오전 10 54 31" src="https://github.com/ejehoon/samo-web1/assets/78858687/0e943862-7cd1-4291-b55f-01e9aa501d2a">


**3\. Summary :** Script를 토대로 연결된 GPT를 이용하여 요약

<img width="722" alt="스크린샷 2024-02-18 오전 10 54 41" src="https://github.com/ejehoon/samo-web1/assets/78858687/d345d96e-c0fb-4765-9618-01065c167ee3">


**4\. Medical Reports :** 의사가 환자의 진단을 입력한 후 연결된 OPEN AI인 GPT를 이용하여 진단 형식 안의 내용 그대로 번역  
**5\. DB :** Cognito 사용자 정보의 DynamoDB, 1:N 관계의 DynamoDB (Patient, Script, Diagnosis)

<img width="769" alt="스크린샷 2024-02-18 오전 10 54 53" src="https://github.com/ejehoon/samo-web1/assets/78858687/b5ce1bd7-9fff-4455-94b7-666e6bb0e841">

**6\. Info :** 1:N 관계의 DynamoDB를 이용하여 각 병원의 환자 정보를 나타내줌  
→ SES를 사용하여 각 환자에게 Script&Summary와 Medical Reports의 정보를 이메일로 전송

<img width="765" alt="스크린샷 2024-02-18 오전 10 55 09" src="https://github.com/ejehoon/samo-web1/assets/78858687/bf5baaf1-2c3d-45b4-a460-11a07f8a9abe">


**7\. 보안 및 배포**

<img width="740" alt="스크린샷 2024-02-18 오전 10 55 19" src="https://github.com/ejehoon/samo-web1/assets/78858687/0198e4ed-1de2-44f9-a0d3-185e9c3d987f">


## 5\. 프로젝트 기대효과 및 추가계획

1.  프로젝트 기대효과

-   해외 병원 방문 부담 감소
-   병원 서비스 만족도 향상 및 병원 홍보 효과
-   병원 고객층 다양화 및 외국인 환자 유치 발전 가능성 증가
-   의료 시스템 발전 기여

2.  프로젝트 추가 계획

-   멀티 리전 Amazon API Gateway, Route 53 지리적 위치 라우팅 등을 사용하여 해외로의 서비스 배포 고려
-   각 나라의 병원에 방문하는 외국인 환자 국적을 분석하여 나라마다 우선순위로 어떤 언어를 설정할지 결정
-   추후 의료 용어 식별 고도화 가능

---

## 6. 문제 및 해결과정:

실시간 통번역과 진단번역에 사용하려던 AWS comprehend medical, transcribe medical 서비스가 낮은 음성 인식률의 문제를 해결하기 위해 React에서 제공하는 음성인식 서비스를 도입하였고 번역서비스는 비교를 통해보다 높은 정확도를 가진 GPT를 선택하여 API를 연결하였습니다.
프로젝트 마무리를 하는도중 CPU 자원을 초과하여 협업하던 cloud9 환경에 접속할 수 없는 이슈가 발생하였습니다.
이를 해결하기 위해 모두가 Cloud9 환경에서 나오고
CloudWatch를 모니터링 하며 Cpu 사용량 지표가 낮아진 후 한명이 접속하여 git push를 하고 EC2를 더욱 높은 사양으로 스케일 업해 문제를 해결하였습니다.


## 7. 결과 및 성과: 
마감날 배포까지 완료하여 최종 발표를 성공적으로 마무리하였습니다. 데이터 청년 캠퍼스 우수상과 함께 클라우드 사용부분 (AWS)에서 1위를 달성하였습니다.



## 8. 기여한 점 :
AWS comprehend medical, transcribe medical과 GPT를 비교할 수 있게 A/B테스트를 진행하였습니다.
팀원들과의 협업을 위해 Cloud9에 개발환경을 세팅하고 git으로 유지관리를 하였습니다.




[PPT 발표자료](https://docs.google.com/presentation/d/1NPoMbiN7A91xVRwXv3Y_7JrpbP1mxt1Z/edit?usp=sharing&ouid=109867150069623460304&rtpof=true&sd=true)

[계획서](https://drive.google.com/file/d/1yzpFANxw6SBFVWThBLT4Le2W_0gFo0mz/view?usp=sharing)

[회의록](https://drive.google.com/file/d/1T1jFfpsIGiqj2f1oq9VU7z6-lY_Y5UzZ/view?usp=sharing)
