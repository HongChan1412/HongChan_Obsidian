
---
### IP : Internet Protocol
IP는 네트워크의 고유한 주소 체계
IP주소는 네트워크 부분과 호스트 부분으로 구성
10진수로 32비트

--- 
### TCP : Transmission Control Protocol
신뢰성 있는 데이터 전송
통신을 시작하기 전 3-Way Handshake를 통해 연결 설정
통신이 끝나면 4-Way Handshake로 연결 종료

---
### UDP : User Datagram Protocol
TCP와 달리 연결을 설정하는 과정이 없음
데이터를 보내고 확인 없이 끝남
속도가 빠름
신뢰성이 낮음

----
### Subnet Mask
IP 주소를 네트워크 부분과 호스트 부분으로 나누는 32비트 숫자
4개의 8비트 옥텟으로 표현

---
### Subnetting
하나의 네트워크를 여러개의 서브넷으로 나누는 기술
과거 : 낭비되는 IP를 줄이기 위해 사용
현대 : 분리, 관리의 목적으로 사용

---
### Router
서로 다른 네트워크 간의 데이터를 전달하는 장치
라우팅 테이블을 이용해 목적지 IP로 전달
패킷을 전달
3계층 장비

---
### Switch
같은 네트워크 내에서 데이터를 전달하는 장치
Mac 주소를 자동으로 학습
Mac주소로 전달
데이터프레임을 전달
2계층 장비
동시에 여러 PC와 통신 가능함

---
### Hub
브로드캐스트 방식으로 모든 포트로 데이터를 전달하는 장치
1계층 장비
동시에 한대의 PC와 통신 가능함

---
### Gateway
내부 네트워크에서 외부 네트워크로 나가는 출입구 역할

---
### IP Address Class

**Class A** : Network | Host | Host | Host
**Subnet Mask** : 255.0.0.0
0.x.x.x ~ 127.x.x.x

**Class B** : Network | Network | Host | Host
**Subnet Mask** : 255.255.0.0
128.x.x.x ~ 191.x.x.x

**Class C** : Network | Network | Network | Host
**Subnet Mask** : 255.255.255.0
192.x.x.x ~ 223.x.x.x

---
### 네트워크 주소와 브로드캐스트

IP 주소:       11000000.10101000.00000001.00001010 (192.168.1.10)
서브넷 마스크:  11111111.11111111.11111111.00000000 (255.255.255.0)

11000000.10101000.00000001.00001010  (192.168.1.10)
AND
11111111.11111111.11111111.00000000  (255.255.255.0)
\-------------------------------------------------
11000000.10101000.00000001.00000000  (192.168.1.0)

네트워크 주소 : 192.168.1.0

브로드캐스트 주소는 네트워크 주소에서 호스트 부분을 모두 1로 채운 값
11000000.10101000.00000001.11111111 (192.168.1.255)
브로드캐스트 주소 : 192.168.1.255

호스트부분이 모두 0이거나 1인 네트워크 주소, 브로드캐스트 주소는 IP주소로 사용하지 못함
가용 가능한 IP -2

---
### Subnetting

> ISP로부터 받은 주소 : 192.168.5.0
> 20 Subnets 필요

![[Pasted image 20250219192559.png]]

> IP : 202.147.10.0
> Subnet Mask : 255.255.255.0
> 서울 : 50개의 주소 필요
> 대전 : 30개의 주소 필요
> 부산 : 10개의 주소 필요
> **넉넉하게 주소 할당 방법**

![[Pasted image 20250219192714.png]]

> **딱 맞게 주소 할당 방법**

![[Pasted image 20250219192930.png]]

---
### CIDR 표기법
```
202.147.10.0/26
-> Subnet Mask : 255.255.255.192 = 8 + 8 + 8 + 2
-> 1의 개수를 작성

202.147.10.0/24
-> 사용가능한 호스트는 2^8 개로 256개

202.147.10.0/32
-> 사용가능한 호스트는 2^0 개로 1개
-> Only Host(단일 호스트)
```

---
### FLSM

> Fixed Length Subnet Mask
> 고정된 길이의 서브넷 마스크
> IP 낭비가 심해져 VLSM으로 바뀜

### VLSM

> Variable Length Subnet Mask
> 가변적인 길이의 서브넷 마스크
> 정통적인 IP주소 클래스의 의미가 사라져 Classless Inter-Domain Routing(CIDR)이 생김

---
### 사설 IP (Private IP Address)

A Class 10.0.0.0 ~ 10.255.255.255 (10.0.0.0 /8)
B Class 172.16.0.0 ~ 172.31.255.255 (172.16.0.0 /12)
C Class 192.168.0.0 ~ 192.168.255.255 (192.168.0.0 /16)

사설 IP는 사실 인터넷이 가능함
근데 Service Provider(Kt, lg, sk)에서 막아버림
라우터 단에서 올라오는것을 막음 (나오면 큰일나니깐 못나오게 해버림)

외부에서는 사설 IP로 접속이 안됨.

![[Pasted image 20250221090850.png]]

---
### 공인 IP (Public IP Address)
인터넷에서 고유하게 식별되는 IP 주소로, 전 세계에서 접근 가능

---
### 고정 IP (Static IP)
라우터, 서버들은 대부분은 고정 IP
- 서비스를 하고 있는것들은 고정 IP

---
### 유동 IP (Dynamic IP)
인터넷에 접속할 때마다 변경되는 공인 IP 주소

---
### DHCP Server
네트워크 장비에 IP 주소를 자동으로 할당해주는 서버

---
### S-NAT (Source-Network Address Translation)

사설 IP를 공인 IP로 바꿔서 웹으로 보내줌
Source IP를 바꿔줌

1 : 1 -> 공인 IP 1개 : 사설 IP 1개
1 : N -> 공인 IP 1개 : 여러개의 사설 IP
1 : ALL (PAT) : Port Address Translation ->  공인 IP 1개 + 포트 변경 : 여러개의 사설 IP

---
### D-NAT (Destination-NAT)

외부에서 사설 IP로 접속하기 위해 공인 IP였던 Destination IP(공유기의 IP)를 내부 IP로 바꿔줌
1 : N이라면 포트포워딩작업이 필요함
포트포워딩 : 공인 IP의 특정 포트로 접속 시 내부의 IP로 변환해줌

---
### ARP (Address Resolution Protocol)

**IP를 이용해 Mac Address를 알아냄**
Ping을 보낼때 Dst의 물리 주소를 모르기 때문에 첫번째 Ping은 빠짐

> ARP Request : S-Mac에는 Source의 물리주소, D-Mac(Dst의 물리주소)를 FFFF.FFFF.FFFF.FFFF(D-Mac을 모르기 때문에 Broad Cast로 전송), 모든 통신 장치가 받음
> ARP Reply : 알아낸 D-Mac을 S-Mac으로, D-Mac의 src의 물리주소로 응답

알아낸 Mac Address를 ARP Cache Table에 저장함

![[Pasted image 20250221090725.png]]

![[Pasted image 20250221090747.png]]

---
### TTL
> Time-To-Live
> Ping으로 보낼고 응답받을때

Window로 Ping을 보내면 128로 Set
- Router를 거치면 -1 해서 127로 응답 받음
- Router를 거치지 않으면 128로 응답 받음
Linux로 Ping을 보내면 255로 Set

기기 거칠때마다 -1