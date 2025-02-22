
---
![[Pasted image 20250221112429.png]]
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