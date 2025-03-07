
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

시간설정과 백업 가능

라이센스 확인
데이터센터에서
폴더 생성
add host

permission : 허가
privilege : 권한
role : 역할

Administrator와 No Access가 동시에 존재할때 Administrator가 우선
사용자에게 직접 권한이 항상 우선

복구할때는 restore, 백업한 파일 선택

소스 mac 해시 기준 라우팅

---
### FTP Server

datastore 에 Filezila server 올리기
ftp server에서 filezila server 설치
클라이언트에서 filezila client 설치

---
### Datastores

VMware가 사용할 공간

VMFS : 사용하려면 무조건 포맷
NFS : Network File System
vSAN
vSphere Virtual Volumes

윈도우즈 끼리 파일 공유는 SMB
NFS

---
### 윈도우즈 공유 폴더 만들기
브릿지 모드
IP 할당
방화벽 : 공용네트워크 방화벽 해제

서버 관리자 > 도구 > 컴퓨터 관리 > 로컬 사용자 및 그룹 > 사용자 > 새 사용자 > 다음 로그온 시 사용자가 반드시 암호 변경 체크 해제 > 만들기
파일 생성 > 속성 > 공유 > 고급 공유 > 권한 > 추가 > 고급 > 찾기 > 생성한 사용자 클릭 > 확인 > 모든 권한 부여
파일 탐색기에 \\ip

서버 관리자 > NFS 설치
새 공유 > NFS 공유 - 빠른 > 사용자 지정 경로 입력 > 공유 이름 > 서버 인증 없음, 매핑되지 않은 사용자 엑세스 사용, UID/GID 별로 매핑되지 않은 사용자 엑세스 허용 > 공유 사용 권한 추가, 호스트에 IP 입력 or all machines, 공유 사용 권한 읽기 쓰기, 루트 엑세스 허용

ESX호스트에 새 스토리지 > 데이터 스토어 추가 >  NFS > NFS3 > 폴더 : /4share, 서버 : IP > 

---
### iSCSi
역할 > ISCI 대상 서버 > 

가상 디스크 생성 > 위치 > 이름 > 크기 > 대상  > 엑세서 서버 추가 및 허용

로컬에서 iscsi 초기자 > 대상 
컴퓨터 관리 > 저장소 > 디스크 관리에서 확인

ISCSI 서버에서 엑세스 서버를 esxi 서버 IP 할당 > VM kernel 어댑터 추가, 안쓰는 IP 할당 > 스토리지 어댑터 > 소프트웨어 어댑터 추가 > ISCSI 어댑터 추가 > 네트워크 포트 바인딩 > 추가 > 동적검색 > ISCSI 서버 추가 > 스토리지 다시 검색 > 디바이스 새로고침  > 디바이스 발견되면 새 데이터 스토어 VMFS로 추가

---
### Template & Clone

Convert to Template : 시간 없고, 용량 없으면 바로 변환 가능
Clone > Clone to Template : 복사 후 Template으로 변환하기 때문에 시간이 많이 걸려도 기존 VM 사용 가능
폴더 생성 > Template 생성
그냥 Clone 하면 IP 충돌할 수 있음

Windows VM 생성 > 시스템, 정보 변경 > IP 변경 > convert to template
vCenter > 정책 및 프로파일 > VM 사용자 지정 규격 만들기 > template으로 vm 생성 > 바뀐 Sid, ip, 시스템 정보 변경 확인

IP, SID, PC 이름이 중복되면 안됨.
VM Customazation Config에서 알맞게 바꿔줘야함.

리눅스는 perl이 설치되어있어야함.

컨텐츠 라이브러리 : iso, ova, template파일을 관리하기 위해 사용

---
### 메모리, 하드 추가

전원 끄기 > 메모리 Hot 사용 > 전원 키기 > 메로리 증가

---
### Migrate

VM의 메모리는 esxi에 저장되어 있기 때문에 다른 esxi로 옮기면 옮긴 VM에 메모리의 정보도 esxi에 저장해야함

---
### vMotion

Cold Migration
VMKernel
- Hot Migration
- 켜져있는 상태에서 마이그레이션 하기 위해 vMotion용 전용 kernel이 필요함
- 트래픽을 많이 잡아서 따로 나누는게 좋음

---
### 