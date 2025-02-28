
---
vmware host client

---
### Bios 세팅
F1 키 눌러서 Bios 모드로 진입

SSD 120GB
SSD 3T

advanced mode

cpu configuration

interl vt-x technology
intel virtualiziotion technology enable
hyper threding

pchconfiguration

---
### ESXI
VMware의 HyperVisor로 서버 가상화해줄 수 있도록 함

DCUI : Direct Console User Interface
VMware Host Client


VMware-workstation 실행해서 설치

VMware-workstaion 실행

Edit > Virtual Network Editor > Change Setting
Bridged : 유선랜카드 선택하고 okay

file > new virtual machine
next > i will > vmware esx 8 > location c / VMs / ESXI-01

날짜 확인

configure management network > network adapter > 랜카드 선택
고정 IP 설정

vm 끈다음에 스토리지 50G 추가 후 데이터스토어를 설정해줘야함

새 데이터 스토어 vmfs 선택


---
### Windows 

typical > Microsoft Windows > Windows Server 2022
설치할 운영 체제 선택 > 데스크탑 환경 > 사용자 지정


ctrl + alt + insert
install vmware tools

snapshot > snapshot manager > take snapshot
go to로 분기점 이동 후 take snapshot하면 분기 생성