### 명령어

```
# 일반 사용자 모드
Router>   
# 특권 모드로 변경
Router> enable

# 라우터의 모든 인터페이스 상태와 IP 주소를 요약
Router# show ip interface brief

# 설정 모드로 진입
Router# configure terminal 
# 첫 번째 인터페이스 선택
Router(config)# interface gigabitEthernet 0/1
# IP 주소 및 서브넷 마스크 설정
Router(config-if)# ip address 172.16.0.1 255.255.0.0
# 인터페이스 활성화
Router(config-if)# no shutdown
# 현재 모드에서 한 단계 위로 이동
Router(config-if)# exit

Router(config)# interface gigabitEthernet 0/2
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
```

---

PC1 - Switch1 - Router - Switch2 - PC2
PC1
IP : 172.16.2.1
Subnet Mask : 255.255.255.0

PC2
IP : 10.1.10.100
Subnet Mask : 255.0.0.0

> IP 설정은 Config > INTERFACE > FastEthernet0
> Gateway 설정은 Config > Setting

`PC1`과 `PC2`를 연결해주기 위해서는 각각 PC에 Gateway를 할당해줘야함
`PC1 Gateway` : 172.16.0.1
`PC2 Gateway` : 10.0.0.1 

---
### TTL
> Time-To-Live
> Ping으로 보낼고 응답받을때

Window로 Ping을 보내면 128로 Set
- Router를 거치면 -1 해서 127로 응답 받음
- Router를 거치지 않으면 128로 응답 받음
Linux로 Ping을 보내면 255로 Set

기기 거칠때마다 -1

---