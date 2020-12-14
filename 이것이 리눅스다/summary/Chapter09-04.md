## 09-04 네임 서버-라운드로빈 네임서버

### 라운드 로빈(Round Robin)방식의 네임 서버

- 여러 대의 웹 서버를 운영, 웹 클라이언트가 서비스를 요청할 경우 교대로 서비스를 실시하도록 하는 방식

![09-04 라운드 로빈 개념](./assets/09-04라운드로빈개념.png)

### [실습4] 라운드 로빈 방식의 네임서버 구현

실습목표
- 외부 사이트 3개를 이용해 라운드 로빈 방식으로 www.john.com 을 구현

1. 서버 터미널에서 수정

    ```bash
    $ nslookup
    > www.danawa.com  # 119.205.194.11
    > www.nate.com  # 120.50.132.112
    > www.hanbit.com  # 218.38.58.195

    $ vi /var/named/john.com.db
    www             IN      CNAME   webserver.john.com.  # 이렇게 수정
    # 아래 추가(라운드 로빈 방식으로 웹을 불러옴)
    webserver 100   IN      A       119.205.194.11
            200   IN      A       120.50.132.112
            300   IN      A       218.38.58.195

    :wq

    systemctl restart named
    systemctl status named
    ```

2. 클라이언트에서 www.john.com 을 여러번 들어가서 바뀌는지 확인
