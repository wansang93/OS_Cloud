## 13-01 FTP 서버-vsftpd, pure-ftpd 설치

### FTP 개요

- FTP(File Transfer Protocol)는 파일을 전송하기 위한 서비스
- 웹에서 FTP의 고유 기능인 파일 전송을 편리하게 할 수 있게 되어 예전보다 인기가 많이 떨어짐
- 파일 전송 자체를 위해서는 성능이 뛰어남
- vsftpd는 CentOS에서 제공
  - vsftpd(Very Secure FTPD)는 CentOS에서 기본적으로 제공
  - 유닉스, 리눅스 환경에서 보안성, 성능 우수한 FTP 서버로 인정
  - pure-ftpd도 많이 사용됨

### [실습1] vsftpd 설치 및 운영

실습목표
- vsFTPD(Very Secure FTPD)를 설치/운영
- 익명(anonymous)사용자도 업로드 되도록 설정
- vsftpd.conf 파일의 설정법을 익힘

서버 터미널에서

```bash
$ dnf -y install vsftpd  # vsftpd 설치
$ cd /var/ftp/
$ pwd
$ ls
$ cd pub  # 이 파일에 보통 파일 업로드, 다운로드를 함
$ ls
$ cp /boot/vmlinuz-4* file1
$ systemctl restart vsftpd
$ systemctl enable vsftpd
$ systemctl stop firewalld  # 방화벽 끄기
$ gedit /etc/vsftpd/vsftpd.conf
> 12행(anonymous): NO -> YES  # 익명 사용자 접속 허용
$ systemctl restart vsftpd
```

윈도우 클라이언트에서

FileZila FTP 클라이언트(3.33.0) 32bit 다운로드 링크 -> [http://download.hanbit.co.kr/fedora/28/FileZilla_3.33.0_win32-setup_bundled.exe](http://download.hanbit.co.kr/fedora/28/FileZilla_3.33.0_win32-setup_bundled.exe)

기본 값으로 설치 후 FileZilla 프로그램에서

호스트: `192.168.111.100` 사용자명: `anonymous` 비밀번호 `아무거나` -> 빠른 연결

윈도우에서 업로드 하면 실패, 보안상 업로드는 실패

서버로 돌아가서 설정 변경

```bash
$ vi /etc/vsftpd/vsftpd.conf
> :set nu
> 19행(wirte_enable): YES
> 29행(anon_upload): 주석 지우기
> 33행(anon_mkdir_write_enable): 주석 지우기
> :wq
$ cd ..
$ ls -l
$ chown ftp.ftp pub/
$ systemctl restart vsftpd
```

윈도우 클라이언트에서 업로드를 다시 해보면 잘 되는지 확인

서버B 에서 해보기

```bash
# ncftp 다운로드
$ wget http://dw.hanbit.co.kr/centos/8/ncftp-3.2.5-17.fc30.x86_64.rpm
$ ls
$ dnf -y install ncftp*.rpm  # Fedora 파일이지만 사용 가능
$ ncftp 192.168.111.100
> ls
> cd pub
> ls
> ls -l
> get file1  # file1 다운로드
> bye  # 종료
```

### vsftpd.conf 옵션

- anonymous_enable: 익명 사용자의 접속 허가 여부 설정
- local_enable: 로컬 사용자의 접속 허가 여부 설정
- write_enable: 로컬 사용자가 저장, 삭제, 디렉터리 생성 등의 명령 실행 여부 설정
- anon_upload_enable: 익명 사용자의 파일 업로드 허가 여부 설정
- dirlist_enable: 접속한 디렉터리의 파일 리스트를 보여줄지 설정
- download_enable: 다운로드의 허가 여부를 설정
- listen_port: FTP 서비스의 포트 번호를 설정(기본:21번)

### [실습2] Pure_FTPd 설치 및 운영

실습목표
- Pure_FTPd를 설치/운영

서버 A 터미널에서

```bash
dnf -y remove vsftpd
wget http://dw.hanbit.co.kr/centos/8/pure-ftpd-1.0.49-2.epel8.playground.x86_64.rpm
ls
dnf -y install pur*.rpm
vi /etc/pure-ftpd/pure-ftpd.conf
:set nu
77행(NoAnonymous) -> no
279행(AnonymousCantUpload) -> no
:wq
systemctl restart pure-ftpd
cd /var/ftp/
ls
rm -rf *
mkdir upload download
chmod 333 upload/
chown ftp.ftp upload download
ls -l
cp /boot/vmlinuz-4* download/file2
```

윈도우 클라이언트에 FileZilla에서 재접속 후

호스트: `192.168.111.100` 사용자명: `anonymous` 비밀번호 `아무거나` -> 빠른 연결

업로드 다운로드 해보기
