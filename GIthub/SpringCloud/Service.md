![image](https://velog.velcdn.com/images/korea3611/post/19d6ee3d-d8c7-46c0-aa6c-8ccbb1140a2f/image.png)

# 역할
## 동적 서비스 제공자에 대한 접근 정보 필요
### 분산 시스템 구조(MSA, SOA) 에서의 서비스 다중화 IP주소, Port 정보

### 클라우드 Auto Scaling 등에 의한 동적 컨테이너 정보 

# 순서 

## 1. Register service - 요청 확인
### 2. Service Client  - 요청 받음

#### 3. Service A is locate - 요청 값 반환
### 위 과정에서 Load Balance 를 통해 전달 (or Gate Way )


# 서버 다중화
## Cllustering Mode, Peering 

### 

# Graceful Shutdown
## 서비스A 중단 시 GateWat가 인지할 때 까지 Term 발생 그 사이 서비스 A로  Request는 계속 발생하기 때문에 받은 Request를 모두 처리하고 Shutdown되어야 한다.

### 1. Shutdown 상호 인지 시간 최대 30초 

### 3. shutdown 인지 최대 시간 30초 

# API GateWay
## 인증 (Authenotification) 
### 사용자 신원 검증
## 인가(Authorizattion) 
### 요청 권한 부여

## 화이트 리스트
## 응답 캐싱, 속도 제한, 로깅
## 블루 / 그린 (테스트 단위 레벨), 홀딩, 카나리아 배포 등 

## Zuul, SCG 
### WebFlux(Non-Block)
#### 
### SCG

#### 람다식으로 개발을 해야함
### Thread, Portlan 의 제어가 많기에 람다식으로 구성을 해야함 

### underTO 는  Non-block 기반이기에 조심을 해야함  Tomcat(Was) 이랑 다르게 

#### server는 underTo 이고 webClient 를 부를 때 Block 형식으로 보내지 않고 Non-Block 형식으로 보내야함 

##### underTO Core Thread 를 두 개에서 100개로 Block 형식으로 만들 수 있음 
### Zuul -> Netty
#### Circuit Breaker 가 포함되어 있음

#### Netty Handlers

##### 네트워크 프로토콜, 웹서버, Connection 관리, 프록시 작업
#### Inbound Filter 
#### 요청을 proxy 하기전 처리 인종, 라우팅, Request 변경 등


#### Bulkhead
##### 선박이 좌초되는 것 막기 위한 장치
##### 사고가 나는 것을 방지 (사고가 난 지점을 차단시키고 정상화 되어 있는 곳으로 사용)

# Service Mesh

## 기능
### 트래픽 관리

#### 서비스 간의 트래픽 프름 및 API 호출 제어 용아
#### 서킷 브레이커, 타임아웃 및 재시도 구성 단순화


### 보안
#### Zero Trust : 아무 것도 신뢰하지 않고 모든 것을 검증한다. 

#### mTLS : TLS 핸드 쉐이크를 두 번 수행하여 양방향 암호화

### 관찰 가능성 (Observability)


# Service Tracing 

##  spring cloud Sleuth, Jaeger 

### HTTP Header 를 통해서 같은 값을 전달해줌 

### TracerID 는 SpanId 값과 같은 값을 설정해줌 Default 

### Elastic Search, Kibana, Logstash 
#### 많이 사용하므로 중요

### TraceID 를 Client 에서 시작할 수 있게 하는 요구 사항도 존재 

# ExTernalized Configuration

## 필요 이유

### 모든 MSA Pod 에 대한 공통 설정 배포
#### 공통 설정에 대해 모든 MSA 각각의 설정을 수정 후 재 기동
#### 일부 MSA에만 바뀐 설정이 누락되는 오류 발생 위험성 

## CONFIG

### 1. 기동 시 설정정보 요청 
### 2. 설정 형상 조회 (GIt, SVN)

### 3. 변경 설정 배포 
### 4. 설정 갱신(/actuator/refresh)

## Config Server 로컬 classpath 나 filesystem 에서 설정 파일을 로드하는 "native"를 사용할 수 있다.

### 로컬 개발 검증 운영 설정 분리는 Git Branch, Spring Profile 둘 중 하나를 선택해야 한다.

### 1. 미리 profile 파일에 설정 후 
### 여러 곳에 쪼개서 저장을 해야함  파일에 대해서 권한을 분리 시켜놓아야 하기 때문에 !
#### 2. yaml 에서 사용할 것을 가져와야함  


# Spring Cloud OPENFEIGN

## post Mapping 을 통해 API를 호출함 

## 설정에 따라 다르지만 URL에 설정을 한 후 가져올 수 있음 


## 개발이 편하지만 필요 설정이 많이 필요

#### FallBack 

##### 새롭게 만들어야함 

# API Interface
## 프로세스 정의

### 개발 프로세스 정의시
#### 실패 건도 클라이언트에서는 보이도록 설정을 하고 

#### 뒤에 배치를 통하여 지속적으로 제휴사와 고객등록을 하며 일일 대사 ( 일일 단위로 데이테 베이스 합치는 작업을 해야함)




