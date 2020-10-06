## 04-15 필수 개념과 명령어-커널 컴파일

### 모듈의 개념과 커널 컴파일의 필요성

모듈: 필요할 때마다 호출하여 사용되는 코드

![모듈 개념](./assets/04-15%20모듈개념.png)

커널이 무거워져 모듈이라고 따로 만들어서 사용

커널 컴파일: 커널을 다른 것으로 교체 가능

커널 컴파일 순서

![커널 컴파일 순서](./assets/04-15%20커널.png)

[실습18] 커널 업그레이드

``` bash
# 1. 현재 커널 버전 확인
uname -r  # 현재 커널 보기(4.18.0)
# 커널은 c나 asembly로 짜여있음

# 2. 커널 소스 다운로드
# [linux-5.3.11.tar.xz](https://mirrors.edge.kernel.org/pub/linux/kernel/v5.x/linux-5.3.11.tar.xz)
# 다운로드 후

# 3. 커널 소스 압축 풀기
cd 다운로드/
mv linux-5.3.11.tar.xz /usr/src/
cd /usr/src
ls
tar xfz linux-5.3.11.tar.gz
ls -l
cd linux-5.3.11/
pwd
ls  # 리눅스 파일들 보기, 대부분 c언어로 작성 되어있음

# 4. c언어 컴파일 환경 설정하기
dnf -y install make bison flex elfutils-libelf-devel openssl-devel

# 5. 커널 설정 초기화
make mrproper  # 커널 설정 초기화

# 6. 커널 환경 설정
make xconfig
# 커널 환경 설정 후 저장
ls -a  # .config 디렉토리 찾기
vi .config  # .config 열어서 수정
    /CONFIG_SYSTEM_TRUSTED  # CONFIG_SYSTEM_TRUSTED 찾기
    # 아래 두줄 # 처리하기
    :wq
make clean  # 이전 정보 삭제

# 7. 커널 컴파일 및 설치(시간이 정말 오래 걸리니 설치를 잘하길)
make; make modules_install; make install;

# 8. 설치 완료 후 확인
ls -l /lib/modules
reboot
# 추가된 것을 보고 접속 후 버전확인
```