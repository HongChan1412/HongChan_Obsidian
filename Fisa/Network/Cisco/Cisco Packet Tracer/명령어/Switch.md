
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
```

#### Global Configuration EXEC 모드
```
Switch (config)# hostname hongchan-Switch
hongchan-Switch (config)#

Switch (config)# vlan 100
Switch (config-vlan)# name Sales
Switch (config-vlan)# exit
Switch (config)# vlan 200
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
```

