## 04-13 필수 개념과 명령어-nmtui 명령 실습, SELinux 개념

### 파이프, 필터, 리디렉션

- 파이프(pipe)
  - 두 개의 프로그램을 연결해 주는 연결통로의 의미
  - ```|``` 문자를 사용
  - 예) ```ls -l /etc | more```: /etc를 more 형식으로 보여주기
- 필터(filter)
  - 필요한 것만 걸러주는 명령어
  - ```grep```, ```tail```, ```wc```, ```sort```, ```awk```, ```sed``` 등
  - 주로 파이프와 같이 씀
  - 예) ```ps -ef | grep bash```
    - ```ps -ef```는 프로세스 작동 중인 것만 보기
    - ```| grep bash```는 bash가 있는 것만 추출
- 리디렉션(redirection)
  - 표준 입출력의 방향을 바꿔 줌
  - ```>``` 문자를 사용
  - 예) ```ls -l > list.txt```: ls -l 의 결과를 list.txt로 작성

### 프로세스, 데몬

데몬: 백그라운드 프로세스의 일종, 사용자의 요청을 기다리고 있다가 요청이 발생하면 이에 적절히 대응하는 리스너와 같은 역할

프로세스

- 정의: 하드디스크에 지정된 프로그램이 메모리에 로딩되 활성화 된 것
- 포그라운드(Foreground Process)
  - 실행하면 화면에 나타나서 사용자와 상호작용을 하는 프로세스
  - 대부분의 응용프로그램
- 백그라운드(Background Process)
  - 실행은 됬지만 화면에 나타나지 않고 실행되는 프로세스
  - 백신, 서버 데몬 등
- 프로세스 번호
  - 각각의 프로세스에 할당된 고유번호
- 작업 번호
  - 현재 실행되고 있는 백그라운드 프로세스의 순차번호
- 부모 프로세스와 자식 프로세스
  - 모든 프로세스는 부모 프로세스를 가지고 있음
  - 부모 프로세스를 kill 하면 자식 프로세스도 자동으로 kill 됨

프로세스 관련 명령

- ```ps```: 현재 프로세스의 상태확인 ex) ```ps -ef | grep <process name>```
- ```kill```: 프로세스 강제 종료 ex) ```kill -9 <process number>```
- ```pstree```: 부모 프로세스와 자식 프로세스의 관계를 트리로 나타냄

[실습 15] 프로세스 연습

``` bash
ps  # 별 의미가 없음
ps -ef  # 현재 모든 프로세스를 보여주기
ps -ef | grep bash  # bash에 관련된 프로세스만 보기
kill -9 2677  # bash(2677) 프로세스 죽이기
pstree  # 프로세스 구조 보기
# gdm xwindow와 관련된 것들
# systemd 를 kill하면 컴퓨터를 끄는 것
```

``` bash
yes  # y가 계속나오는 명령어
yes > /dev/null  # y를 계속 /dev/null에 넣음, 블랙홀 작성
# 다른 배쉬창에서
ps -ef | grep yes  # yes에 관련된 프로세스 찾기
kill -9 4492  # yes(4492) 프로세스 죽이기
# 다시 같은창으로 돌아와서
# Ctrl + z -> 백그라운드로 돌리기(stopped)
bg  # background에서 돌고 있는 것
fg 1  # 백그라운드 1번을 foreground로 올리기
# Ctrl + c -> 종료
gedit &  # gedit을 백그라운드로 실행해라
# 큰 파일 압축하기, 묶기는 백그라운드로 진행하면 좋음
```

### 서비스와 소켓

서비스(=데몬과 비슷)

- 시스템과 독자적으로 구동되어 제공하는 프로세스
  - 예) web server(httpd), DB server(mysqld), FTP server(vsftpd)
- 실행 및 종료는 ```systemctl <start|stop|restart> <service_name>```
- 서비스의 실행 스크립트 파일은 대부분 ```/usr/lib/systemd/system/``` 디렉토리에 있고 ```<service_name>.service```의 이름으로 확인 할 수 있음
  - 예) Cron 서비스(자동 백업)는 ```crond.service``` 라는 이름으로 존재

소켓

- 서비스는 항상 가동되지만, 소켓은 외부에서 특정 서비스를 요청할 경우에 systemd가 구동함, 요청이 끝나면 소켓도 종료
  - 예) 텔넷 서버
- 소켓 스크립트 파일은 ```/usr/lib/systemd/system/``` 디렉토리에 있고 ```<socket_name>.socket``` 이라는 이름으로 존재
