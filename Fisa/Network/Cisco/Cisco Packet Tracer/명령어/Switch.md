
---
#### User EXEC 모드
```
# 일반 사용자 모드
Switch>

# 특권 모드로 변경
Switch> enable
Switch#

Switch > logout
```

#### Privileged EXEC 모드
```
Switch# show ip interface brief

Switch# configure terminal

Switch# show interface trunk

Switch# show vlan

Switch# show cdp neighbors
```

#### Global Configuration EXEC 모드
```
# Switch 이름 변경
# hongchan-Switch로 변경
Switch (config)# hostname hongchan-Switch
hongchan-Switch (config)#

# VLAN 100 생성
Switch (config)# vlan 100
# Sales 라는 이름 부여
Switch (config-vlan)# name Sales
Switch (config-vlan)# exit

# VLAN 200 생성
Switch (config)# vlan 200
# Engineering 라는 이름 부여
Switch (config-vlan)# name Engineering
Switch (config-vlan)# exit

Switch (config)# interface fastEthernet 0/1
Switch (config-if)# switchport access vlan 100
Switch (config-if)# exit

Switch (config)# interface fastEthernet 0/2
Switch (config-if)# switchport access vlan 200
Switch (config-if)# exit

Switch (config)# interface gigabitEthernet 0/1
Switch (config-if)# switchport access vlan 100
Switch (config-if)# exit

Switch (config)# interface gigabitEthernet 0/2
Switch (config-if)# switchport access vlan 200
Switch (config-if)# exit


Switch (config-if)# switchport mode trunk
Switch (config-if)# switchport mode access

Switch (config)# vtp mode client
Switch (config)# vtp mode server

Switch (config)# vtp domain hongchan
Switch (config)# vtp password cisco

Switch (config)# no vlan

Switch (config-if)# interface range fastEthernet 0/2 - 4
```

