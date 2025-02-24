---
aliases:
  - "\bSwitch"
---

---
### Poorly Designed
![[Pasted image 20250224102857.png]]
> [!warning] 브로드캐스트 도메인이 너무 큼
> 브로드캐스트의 도메인이 클 수록 통신하기 위해 ARP를 사용하는데 이때 같은 네트워크에 있으면 모든 PC가 CPU를 사용해야함
> 브로드캐스트 도메인은 작을수록 좋음

전통적인 Switch는 브로드캐스트 도메인을 나눌 수 없음
VLAN을 사용하면 Switch도 브로드캐스트 도메인을 나눌 수 있음

---
### VLAN

Switch에서 물리적인 하나의 네트워크를 논리적으로 분리하는 기술
사용 이유
- 브로드캐스트의 트래픽을 줄임
- 보안 강화

다른 VLAN일때 연결하기 위해는 Router를 사용해서 연결
Router를 연결하기 위해서는 네트워크 대역대를 바꿔야함
-> Router는 각각의 다른 네트워크 주소를 가지고 있어야함.

VLAN을 많이 사용하면 포트가 낭비될 수 있음

중요 연구시설에서는 보안 때문에, 이동이 잦은 곳은  mac base vlan
나머지는 port base vlan

---
### ISL (Inter Switch Link)

802.1Q 사용

Native VLAN
Hub를 호환해주기 위해 만듬
지금은 의미 없음

Trunk Port
: 모든 VLAN이 흘러다닐 수 있는 통로
: Tagged Port
: Tag를 붙여가지고 Trunk Port를 사용한다면 다른 VLAN은 인식이 안됨.
: Trunk Port를 사용하지 않으면 Tag를 안붙이기 때문 다른 VLAN과도 연결이 가능함.

Access Port
: 하나의 VLAN이 흘러다니는 통로
: UnTagged Port

native vlan, default vlan은 1
vlan은 2번부터 사용 가능
보통 10, 20, 30, 40 으로 셋

Trunk port일때만 VLAN을 붙임

Dynamic Trunk Protocol

---
###
Bandwidth : 대역폭
Throughput : 데이터 전송량

24 Port * 1Gbps(대역폭) * 2
 48 Gbps througput

---
### VTP (VLAN Trunk Protocol)

중앙에서 VLAN을 생성하고 보내기 위함

Server mode
vtp 생성

Client Mode
vtp를 생성하지는 못하지만 받긴 해야함
받은거는 동기화함
fowarding 사용

Transparent mode
동기화 받지 않음
받은거는 fowrding해줌

---
### Management IP

Managed Switch