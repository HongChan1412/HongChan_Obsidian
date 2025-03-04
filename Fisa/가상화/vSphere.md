
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

File > Connect to Server

---
### Workstation Network

Bridge
NAT
Host Only


VMnet8 : NAT
VMnet1 : HostOnly

---
### ESXI VMware 생성

데이터스토어 브라우저 > 디렉토리 생성 > 업로드

가상 시스템 > 새 가상 시스템 > 씬 프로비저닝 > 데이터스토어에 파일 업로드 > 데이터스토어에서 iso 파일 선택해서 CD/Rom 인식

---
### VCSA
vCenter Server Appliance Installation

vCenter : 가상머신과 ESXI 호스트 를 중앙관리하기 위함
- 고 가용성
vCenter를 여러대 두는 이유 : 가상머신과 esx host를 관리하는데 지역적인 위치로 따로 관리
여러 vCenter를 하나의 도메인으로 쓰기 위해 : enhanced linked mode

1. 어느 ESXI에 VCSA 설치할지 결정
	1. 어느 데이터 스토어에 설치할지 결정
	2. 어느 네트워크에 설치할지 결정
2. vCenter 도메인 생성
	1. VCSA.~.com (hostname, domainname)
	2. DNS Server에 IP랑 domainname 등록되어야함
	3. DNS 서버에 고정 IP
	4. 역할 기능 추가
	5. DNS 서버 추가
	6. DNS 관리자.
	7. 도메인 추가
	8. 영역 추가정방향 연결
	9. IP랑 도메인 연결


install > 존재하는 esxi, 172.16.4.41, root, VMware1! > ID, Password 설정

---
### 프로비저닝
씬 프로비저닝 : 쓸때마다 용량을 필요로함
씩 프로비저닝 : 성능이 필요할때
- eager-zeroed : 모두 포맷해서 제공
- lazy-zeroed : 쓸때마다 포맷해서 제공
씬 프로비저닝 -> 씩 프로비저닝 (가능)
씩 프로비저닝 -> 씬 프로비저닝 (불가능)

오버프로비저닝 : 용량 다차기 전에 모니터링

---
### VAMI
vCenter Server Appliance Management Interface

라이센스 확인
데이터센터에서
폴더 생성
add host

permission : 허가
privilege : 권한
role : 역할
