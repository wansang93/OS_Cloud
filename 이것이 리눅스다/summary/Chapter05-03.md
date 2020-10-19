## 05-03 X 윈도 사용-기타 응용 프로그램, Foxit, LibreOffice, 소프트웨어 센터

### 응용 프로그램

- 인터넷 응용 프로그램 - 에볼루션(Evolution)
  - 예전에는 e-mail 클라이언트를 많이 사용했음
  - 뒷부분에 이메일 서버 구축 때 사용함
  - `시작`(`현재 활동`) -> `에볼루션`
  - 명령어: `evolution`
- 메신저 - 피진(Pidgin)
  - Bonjour, Google Talk, ICQ 등
  - 우리나라에서는 지원을 안하고 많이 안쓰는 분위기
  - `시작` -> `프로그램 표시` -> `Pidgin`
  - 명령어: `pidgin`
- FTP 클라이언트 - gftp
  - CentOS 에서는 지원을 안해서 Fedora 29 사이트에서 다운받아야 함
  - 다운로드 링크 -> [gftp-2.0.19-19.fc29.x86_64.rpm](https://archives.fedoraproject.org/pub/archive/fedora/linux/releases/29/Everything/x86_64/os/Packages/g/gftp-2.0.19-19.fc29.x86_64.rpm)
  - `시작` -> `프로그램 표시` -> `gFTP`
  - 명령어: `gftp`
- 사운드 설정 및 음량 조절
  - 메뉴 -> 우측상단 -> 설정
  - 명령어: `gnome-control-center` -> `소리 아이콘 클릭`
- 멀티미디어 - 음악 재생과 인터넷 라디오 재생
  - `시작` -> `리듬 박스`
  - 명령어: `rhythmbox`
- 멀티미디어 - DVD 재생 및 동영상 플레이어
  - `시작` -> `프로그램 표시` -> `모두` -> `동영상`
  - 명령어: `totem`
- 문서 편집기/뷰어 - gedit
  - `시작` -> `프로그램 표시` -> `텍스트 편집기`
  - 명령어: `gedit`
- 문서 편집기/뷰어 - evince
  - PDF, XPS, TIFF 등의 다중 문서 뷰어
  - `시작` -> `프로그램 표시` -> `유틸리티` -> ``문서 보기``
  - 명령어: `evince`

[실습4] Foxit Reader 설치

1. Foxit 설치 링크 ->  [https://www.foxitsoftware.com/downloads/](https://www.foxitsoftware.com/downloads/)
2. Foxit Reader 다운로드
3. Terminal 에서
   ``` bash
   cd 다운로드/
   tar xfz Foxit~
   ./Foxit~
   ```
4. 기본으로 설치
5. `프로그램 표시` -> `Foxit Reader`

- CD/DVD 레코딩 - 브라세로
  - CD/DVD를 레코딩 하는 툴
  - `시작` -> `프로그램 표시` -> `브라세로`
  - 명령어: `brasero`
- 그래픽 편집 - GIMP
  - Windows의 포토샵과 비슷한 기능
  - `su -c 'dnf -y install gimp'` 로 설치
  - `시작` -> `프로그램 표시` -> `GNU Image Manipulation Program`
  - 명령어: gimp
- 그림 보기 - ego
  - windows의 사진 앱과 비슷함
  - `시작` -> `프로그램 표시` -> `유틸리티` -> `이미지 보기`
  - 명령어: `ego`
- 스크린샷
  - 화면을 캡처할 때 사용
  - `시작` ->  `프로그램 표시` -> `유틸리티` -> `스크린샷`
LibreOffice
  - Microsoft Office와 비슷하고 **무료** 

[실습5] 리브레오피스(Libreoffice) 최신 버전 설치

  1. 다운로드 링크 -> [https://www.libreoffice.org/download/download/](https://www.libreoffice.org/download/download/)
  2. 압축 풀기
     ``` bash
     cd 다운로드/
     tar xfz LibreOff~
     cd LibreOff~
     cd RPMS/
     su -c 'dnf -y install *.rpm'
     libreoff~  # 실행
     libreoff~ --calc  # excel 실행
     ```

- 워드프로세스 - Writer
  - MS Word 파일 포맷인 `*.doc`, `*.docx`를 지원
  - PDF 파일로 저장 지원
  - `시작` -> `프로그램 표시` -> `LibreOffice Writer`
  - 명령어: `libreoff~ --writer`
- 스프레드시트 - Calc
  - MS Excel 파일 포맷인 `*.xls`, `*.xlsx`를 지원
  - PDF 파일로 저장 지원
  - `시작` -> `프로그램 표시` -> `LibreOffice Calc`
  - 명령어: `libreoff~ --calc`
- 프레젠테이션 툴 - Impress
  - MS Powerpoint 파일 포맷인 `*.ppt`, `*.pptx`를 지원
  - PDF 파일로 저장 지원
  - `시작` -> `프로그램 표시` -> `LibreOffice Impress`
  - 명령어: `libreoff~ --impress`
- 소프트웨어 센터
  - 응용 프로그램 스토어로 검색을 통해 원하는 소프트웨어를 클릭만으로 설치
  - `시작` -> `소프트웨어`
  - 소프트웨어 센터에서 검색되는 패키지는 `dnf` 로 설치 가능 