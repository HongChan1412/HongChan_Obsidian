---
aliases:
  - "\bRouter"
---

---
#### 공통
```
# 사용가능한 명령어 확인
Router# ?

# 
ctrl + shift + 6
```
#### User EXEC 모드
```
# 일반 사용자 모드
Router> 

# 특권 모드로 변경
Router> enable
Router#

Router> logout
```

#### Privileged EXEC 모드
```
# 시간 확인
Router# show clock

# 라우터의 모든 인터페이스 상태와 IP 주소를 요약
Router# show ip interface brief

# 버전 확인
Router# show version

# 설정 모드로 진입
Router# configure terminal 

# 현재 설정 정보 확인
Router# show runnung-config

# 현재 설정 정보 저장
Router# copy running-config startup-config

Router# disable
Router>
```

#### Global Configuration EXEC 모드
```
# hostname 변경
# hongchan-router로 변경
Router(config)# hostname hongchan-router
hongchan-router(config)#

# 비밀번호 설정
# cisco로 패스워드 설정
hongchan-router(config)# enable password cisco

# 배너 설정
# motd : Message-of-the-Day
hongchan-router(config)#banner motd $  
Enter TEXT message. End with the character '$'.  
# 배너에 보여줄 텍스트
This system is under real-time monitoring.  
Unauthorized users please disconnect immediately  
$

# 첫 번째 인터페이스 선택
Router(config)# interface gigabitEthernet 0/1
# IP 주소 및 서브넷 마스크 설정
Router(config-if)# ip address 172.16.0.1 255.255.0.0
# 인터페이스 활성화
Router(config-if)# no shutdown

Router(config)# interface gigabitEthernet 0/2
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

# 현재 모드에서 한 단계 위로 이동
Router(config-if)# exit
# 가장 밑 단계로 이동
Router(config-if)# end

```

> [!info] 중요
> 메모리에 저장되어 있기 때문에 꺼지면 설정한 값들이 날라감
> -> 날라가지 않게 할려면 NVRAM에 현재의 설정 정보 저장
>```
>Router# copy running-config startup-config
>```
>

