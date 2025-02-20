
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

---
### 공인 IP (Public IP Address)

---
### 고정 IP (Static IP)
라우터, 서버들은 대부분은 고정 IP
- 서비스를 하고 있는것들은 고정 IP

---
### 유동 IP (Dynamic IP)

---
### DHCP Server
IP를 자동으로 뿌려줌

---
### S-NAT (Source-Network Address Translation)

사설 IP를 공인 IP로 바꿔서 웹으로 보내줌
Source IP를 바꿔줌

1 : 1
1 : N
1 : ALL (PAT) : Port Address Translation - Port를 변환해서 보냄

---

### D-NAT (Destination-NAT)

외부에서 사설 IP로 접속하기 위해 공인 IP였던 Destination IP(공유기의 IP)를 내부 IP로 바꿔줌
1 : N이라면 포트포워딩작업이 필요함
포트포워딩 : 공인 IP의 특정 포트로 접속 시 내부의 IP로 변환해줌

---
### ARP (Address Resolution Protocol)

**IP를 이용해 Mac Address를 알아냄**
Ping을 보낼때 Dst의 물리 주소를 모르기 때문에 첫번째 Ping은 빠짐

> ARP Request : Dst의 물리주소를 FFFF.FFFF.FFF로 (Dst의 물리주소를 모르기 때문에 Broad Cast로 전송), 모든 통신 장치가 받음
> ARP Reply : Dst의 물리주소를 알아냈기 때문에 (Src의 물리주소를 알기 때문에 Unicast로 전송), Dst에 물리주소가 저장되어 있음

알아낸 Mac Address를 ARP Cache Table에 저장함