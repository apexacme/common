# common
공통 모듈



## 팀원 역할 협의
팀장 : 협의역할  
기획자1,2 : 외부 API 및 이벤트 데이터 분석, 네이밍, 스팩 정의  
개발자1,2 : 그냥 아무것도 모른다고 생각하고, 개발만  

## 깃헙 계정을 김상훈씨에게 알려주어서 아래의 github project clone
https://github.com/lgcns-bootcamp  

## 시나리오 url
https://github.com/sw300/event-storming/wiki  

## 각 팀에 마추어 프로젝트 clone 및 개발
git clone https://github.com/lgcns-bootcamp/goods.git  


## host 정보 수정하여 kafka 접속
- mac / linux  
sudo vi /etc/hosts  
35.194.123.133	kafka-0.example.com  
35.200.31.104	kafka-1.example.com  
35.243.91.239	kafka-2.example.com  

- window  
C:\Windows\System32\drivers\etc\hosts  


## 구글 클라우드 접속
https://console.cloud.google.com  
id:  
pw:  


## 쿠버네티스 클라우드 접속
gcloud container clusters get-credentials standard-cluster-1 --zone asia-northeast1-a --project electric-block-238113  

## cloud console 에서 간단한 쿠버네티스 명령어
#### pod 관련
```
kubectl get pods  
kubectl logs podname -f  
```
#### service 관련
kubectl get svc

## cloud console 에서 다른 서비스 접근 및 다른서비스 http 확인
```
kubectl exec -it httpie bin/bash  
http common:8080  
http common:8080/userInfoes  
exit  
```

## kafka 이벤트 확인 명령어
### 로컬
#### 토픽 리스트 보기
#### orderTopic 토픽으로 메세지 보내기 
#### 클러스터에서 카프카 orderTopic 토픽 데이터 확인


### 클러스터
#### 토픽 리스트 보기
```
kubectl -n kafka exec my-kafka-0 -- /usr/bin/kafka-topics --zookeeper my-kafka-zookeeper:2181 --list
```
#### orderTopic 토픽으로 메세지 보내기
``` 
kubectl -n kafka exec -ti my-kafka-0 -- /usr/bin/kafka-console-producer --broker-list my-kafka:9092 --topic orderTopic
```
#### 클러스터에서 카프카 orderTopic 토픽 데이터 확인
```
kubectl -n kafka exec -ti my-kafka-0 -- /usr/bin/kafka-console-consumer --bootstrap-server my-kafka:9092 --topic orderTopic --from-beginning
```


