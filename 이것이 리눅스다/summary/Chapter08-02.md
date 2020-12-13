## 08-02 원격지 시스템 관리-SSH 서버

### OpenSSH 서버

- 텔넷과 용도는 동일, 보안이 강화
- 텔넷과의 차이: 데이터 전송시 암호화를 함
- 현업에서 사용

### [실습2] OpenSSH 서버 구축

![08-02 OpenSSH 서버 설치 과정](./assets/08-02OpenSSH서버설치과정.png)

1. SSH 서버 확인 및 방화벽 설정
    ``` bash
    $ rpm -qa openssh-server  # openssh-server 설치
    $ systemctl status sshd  # 작동 확인
    $ firewall-config  # 방화벽 ssh 서버 열기(자동으로 열려있는지 확인)
    ```

2. 리눅스 클라이언트에서 SSH 접속 확인하기
    클라이언트 컴퓨터로 로그인 후 터미널에서

    ``` bash
    $ ssh teluser@192.168.111.100
    $ ifconfig  # 접속 확인
    ```

3. 윈도우 클라이언트에서 SSH 접속 확인하기
    1. 한글 iPUTTY를 다운로드 링크 -> [https://github.com/iPuTTY/iPuTTY/releases](https://github.com/iPuTTY/iPuTTY/releases)
    2. `192.168.111.100/22` 로 접속 후 로그인