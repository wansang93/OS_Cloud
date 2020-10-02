## 04-07 필수개념과 명령어-프로그램 설치를 위한 RPM

### 프로그램 설치를 위한 RPM(Redhat Package Manager)

레드햇사에서 처음으로 시작한 패키지 관리자로

리눅스도 윈도우 처럼 setup.exe 파일처럼 편리하게 설치하자

확장명은 *.rpm 이며 이를 패키지(package)라고 불림

gzip은 압축하는 파일인데 이걸 살펴봄 ```ls -l gzip*```

**패키지이름** **버전** **릴리즈번호** **CentOS버전** **아키텍처** 순으로 적혀있음

- 자주 사용하는 RPM 명령어 옵션
  1. 설치: ```rpm -Uvh <package_file_name>.rpm```
     - U는 Upgrade의 뜻, I(install)로 해도 가능하나 이미 설치되어 있으면 오류 발생
     - v는 설치과정 확인
     - h 설치진행과정을 # 마크로 화면에 출력
  2. 삭제: ```rpm -e <package_name>```
     - windows의 프로그램 추가/제거 처럼 설치할때는 .rpm 파일(windows의 setup파일)이 있어야 하고 제거할때는 없어도 됨
  3. 이미 설치된 패키지 질의
     - 패키지가 설치되어있는지 확인: ```rpm -qa <package_name>```
     - 파일이 어느 패키지에 포함됬는지 확인: ```rpm -qf <file_abs_path>```

RPM 단점은 의존성 문제, 이를 해결하기 위해 DNF, YUM 등장

[실습10] rpm 패키지 설치 연습

``` bash
cd /run/media/root/CentOS-8-BaseOS-x86_64/AppStream/Packages/  # 설치할 파일 보기
pwd
ls -l mc-*  # 패키지 파일 확인
rpm -qip mc-4.8.19-9.el8.x86_64.rpm  # 도움말
rpm -Uvh mc-4.8.19-9.el8.x86_64.rpm  # 설치
rpm -qi mc  # 설치 확인
rpm -ql mc  # 설치 파일들 확인
mc  # 프로그램 실행(파일을 관리할 수 있음)
```

의존성 있는 패키지 설치, 강제설치가 가능하지만 추천x  
그래서 dnf 명령어를 더 많이 씀 다음시간에 배워보자

``` bash
ls -l mysql-errmsg*  # 의존성 패키지 파일 확인
rpm -Uvh mysql-errmsg-8.0.13-1.module_el8.0.0+41+ca30bab6.x86_64.rpm  # 설치오류
```

실습결과

![실습결과04-07](./assets/04-07실습결과1.png)