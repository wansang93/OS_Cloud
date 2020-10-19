## 05-04 X 윈도 사용-리눅스에서 Windows응용 프로그램 실행

[실습6] CentOS 안에 Windows 설치

1. RAM -> 4GB
2. CPU -> 4개로 설정, 가상화 기술 클릭
3. 해상도 설정
4. Windows IOS 파일 다운로드 하기, 링크 -> [https://www.microsoft.com/ko-kr/evalcenter/evaluate-windows-10-enterprise](https://www.microsoft.com/ko-kr/evalcenter/evaluate-windows-10-enterprise)
5. Terminal에서
   ``` bash
   dnf -y install make perl patch kernel-devel kernel-devel-4.18.0-80.el8.x86_64 elfutils-libelf-devel
   ```
6. VirtualBox 다운로드 하기, 링크 -> [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
7. Terminal에서
   ``` bash
   dnf -y install Vir*  # Virtual Box(vbox) 설치
   usermod -a -G vboxusers centos  # centos를 vbox로 추가
   /usr/lib/vertualbox/vboxdrv.sh setup  # vbox 드라이버 설치
   /sbin/vboxconfig  # 설정하기
   ```
8. Virtual Box 를 3장과 동일하게 설정