## 08-03 원격지 시스템 관리-XRDP 서버

### XRDP 서버

- X 윈도우 환경으로 원격접속을 사용하고 싶을 때
- 원격지로 그래픽 화면 전송, 속도가 느림

### XRDP 서버 구축

![08-03 XRDP 서버 구축 과정](./assets/08-03XRDP서버구축과정.png)

### [실습3] XRDP 서버 설치

실습 목표

- X 윈도우 접속이 가능한 XRDP 서버를 구축
- Windows에서 VNC 클라이언트 사용

1. 터미널에서 설치 후 방화벽 설정

    ``` bash
    dnf -y install epel-release  # 추가 패키지를 설치할 수 있는 저장소 설치(CentOS8에서 제공 안해서 다운)
    dnf -y install xrdp  # xrdp 서버 다운로드
    systemctl restart xrdp  # 재시작
    firewall-config  # 방화벽
    ```

    `영구적`으로 설정 후 -> `포트` -> `추가` -> `3389` -> 상단에 `옵션` -> `Firewalld 다시 불러오기`

2. Windows에서 `Window` + `R` -> `mstsc` -> 로그인 후 사용

### 3가지 원격 서버의 비교

![08-03 원격접속 서버별 비교표](./assets/08-03원격접속서버별비교표.png)
