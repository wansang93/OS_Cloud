## 15-01 Samba 서버-리눅스에서 Windows 폴더 사용

### Samba 서버 소개

- 예전에는 Windows와 Linux/Unix 사이에 프린터나 폴더 등의 자원 공유가 어려웠음
- Samba 서버는 Windows와 Linux/Unix 사이에서 자원을 공유하기 위해 개발
- Linux에서 Windows의 자원을 사용하는 방법과 Windows에서 Linux의 자원을 사용하는 방법으로 나뉨

### 리눅스에서 Windows 폴더와 프린터 사용

![15-01 Samba 서버 구현도1](./assets/15-01Samba서버구현도1.png)

윈도우는 삼바 서버 개념이 없고 공유폴더로 지정하면 끝남

### [실습1] 리눅스에서 Windows 폴더 접근

실습목표
- WinClient의 폴더를 공유, Server에 접근해 사용
- samba 클라이언트 패키지 사용법을 익힘

윈도우 클라이언트에서

share 폴더 연결 끊기 또는 초기화 후에

C 밑에 smbShare 폴더 생성 -> 속성 -> 공유 -> Everyone 추가 -> 읽기/쓰기로 설정, 공유 -> 아니요, 완료

리눅스에서 접근할 사용자를 만들어 놔야 공유 폴더 사용 가능

파워쉘 관리자에서

```powershell
net user root 1234 /add  # 유저 만들기
ipconfig  # IPv4 주소 기억해두기
```

서버 터미널에서

```bash
dnf -y install samba-client
smbclient -L 192.168.111.130  # windows ipconfig 명령어의 숫자로 입력할 것, 비번 1234
mkdir /sambaMount
mount -t cifs //192.168.111.130/smbShare /sambaMount/  # 동기화 시키기
ls -l /sambaMount/
cp /boot/grub2 /sambaMount/
ls -l /sambaMount/  # 파일이 들어있는지 확인
```
