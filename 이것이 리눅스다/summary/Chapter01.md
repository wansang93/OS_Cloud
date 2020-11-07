## 01-00 Orientation

이 강의는 ...  
리눅스를 명령어 정도만 사용해 본 사람 추천  
초보자 -> 중급자로 올리는 개념

- 권장 실습 사항
    Intel Core 3세대 이후, RAM 8GB 이상  
    내장 SSD, 외장 SSD의 50GB 이상 여유

## 01-01 가상머신 개념과 VMware 설치

HOST OS: Windows에 이미 설치된 OS
GUEST OS: 가상머신에 설치할 운영체제

멀티부팅은 컴퓨터 한대에서 OS 한개씩 부팅, but 이것은 OS 한개에서 여러개 부팅

가상머신 개념도

![가상머신 개념](./assets/01%20가상머신%20개념.png)

가상머신은 VMware를 사용 할 것

VMWare Pro 와 VMware Plyaer 두 가지가 있는데 한개는 유료 한개는 무료이다.
우리는 두개 다 사용  
Pro에는 snapshot 기능과 가상 네트워크 사용자 설정 기능을 사용  
Plyaer에는 일반적 우리의 작업을 함

선생님 카페 링크 자료실 -> [https://cafe.naver.com/thisislinux?iframe_url=/MyCafeIntro.nhn%3Fclubid=27895721%26tc=naver_search](https://cafe.naver.com/thisislinux?iframe_url=/MyCafeIntro.nhn%3Fclubid=27895721%26tc=naver_search)

VMware Workstaion Pro 15.0.0 다운로드 -> [http://download3.vmware.com/software/wkst/file/VMware-workstation-full-15.5.0-14665864.exe](http://download3.vmware.com/software/wkst/file/VMware-workstation-full-15.5.0-14665864.exe)

설치하면 2가지 프로그램이 있는데 한개는 Pro, 다른 거는 Player 인데 우리는 Player 위주로 사용 함

## 01-02 가상머신 4대 설치

Server, Server_B, Client, Windows_Client 설치하기 기본

1. 가상머신을 저장 할 폴더 4개를 만들기(SSD에 만드는 것을 추천)
2. Player에 가서 Create a New Virtual Machine 클릭
    1. `I will install the operating system later`(OS 나중에 설치) 클릭
    2. `Linux` -> Version 은 `red hat enterprise linux 8` 클릭
    3. 가상머신 이름은 원하는 대로, 폴더 경로는 아까 저장해 둔 폴더로 연결 후 다음
    4. 원하는 저장공간만큼 사용 후 아래에 `Store virtual disk as a single file` 클릭
       - 한개 파일로 저장공간을 하면 보기에 편해서 이렇게 함, 안해도 크게 상관은 없음
       - Server 의 경우 디스크를 `SCSI`로 설정해 오류 발생 방지
    5. 추가, 수정 할 경우 `Customize Hardware` 클릭 -> 수정 -> 끝내기
3. 원하는 가상머신 클릭 후 `Edit Virtual machine settings` 클릭
4. 필요 없는 기능 들 `remove` 필요한 기능 `add` 하고 OK

## 01-03 VMware 특징 및 네트워크 설정

VMware 특징

- 1대의 컴퓨터만으로 실무 환경과 거의 비슷하게 조성 가능
- 운영체제의 특정 시점을 저장하는 스냅숏 기능 사용
- 하드디스크를 여러 개 장착해 테스트 가능
- Suspend 기능: 현재 컴퓨터 상태를 그대로 저장 후 다음에 이어 사용 가능

![가상머신 IP 주소 개념](./assets/01%20가상머신%20IP%20주소.png)

네트워크 설정하기

1. `cmd` -> `ipconfig /all` -> `VMware Network Adapter VMnet8` 의 `IPv4`를 `192.168.111.0`으로 바꾸는게 목적
2. VMware Pro 들어가서 -> `Edit` -> ``Virtual Network Editor`` -> `Change Settings` 클릭
3. VMnet8 클릭 -> Subnet IP 를 `192.168.111.0`로 변경 -> `OK` 클릭