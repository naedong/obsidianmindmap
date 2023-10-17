# Cloud

## 제작 비화
### Netfilx 가 적극 참여하였으며 라이브러리 중 Netfilx 명이 있다.


## Libs
### Spring-Cloud Config
#### 설정을 외부화 시키겠다. 
#### Config 서버 설정 및 적극 이용

### Spring-Cloud Bus
#### 설정과 관련되어 있음

### Spring-Cloud Netflix 
#### Eureka, Zuul, Hystrix, Ribbon
##### Zuul (EOS = End Of Service)

### Spring-Cloud Connsul 
#### Service Discovery

### Spring-Cloud Gate Way
#### Zuul을 이어받아 사용
#### WebFlux 기반으로 사용 

### Spring-Cloud OpenFeign 
#### Http-Client 
#### 기존이랑 다른 점은 선언적으로 사용

### Spring-Cloud Open Service Broker
### Spring-Cloud Sleuth
#### 중요 Log와 같은 역할
#### 서버 호출 시 찾기 힘든것을 찾을 수 있게 

### Spring-Cloud Stream
#### 미들웨어 통신(kafka, RabbitMQ 등)
### Spring-Cloud Applications 
#### 독립형 외부미들웨어 통신


###  Spring-Cloud Data Flow 
#### MSA 기반 배치 for Kubernetes 
##### Kubernetes 중요 
##### 서버 크기는 Auto Scale Out (사용자 및 수요에 따라 자동 크기 조절 병렬로)을 가능하게 만든 역할

### Spring-Cloud Task 
#### 단기 MSA 기반배치 제공
### Spring-Cloud Contract 
#### MSA E2E 테스트

### Spring-Cloud Function
#### Services Archtecture (Faas, Baas ) 가 새로 등장 
##### 서비 요청 확인 시 서비스 후 죽음
##### 이에 따라 Core를 줄여 가볍게 만들 수 있음































