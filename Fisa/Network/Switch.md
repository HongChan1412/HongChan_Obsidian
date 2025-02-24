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
