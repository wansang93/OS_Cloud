## 04-04 필수개념과 명령어-리눅스 기본 명령어

명령어 목록

파일 및 경로 보기

- ```ls```: 파일 목록 보기
  - ```-a```: 숨긴 파일 보기
  - ```-l```: 자세히(long) 보기 -> 앞글자가 d이면 directory, -면 파일
- ```cd```: change directory
  - ```cd ~<username>```: 사용자 디렉토리로 이동
- ```pwd```: print working directory
- ```clear```: 콘솔 창 깨끗이 하기

디렉토리 및 파일 관리

- ```mkdir <directoryname>```: make directory
- ```rmdir <directoryname>```: 폴더 모두 지우기(빈 폴더만)
- ```rm -rf <directoryname>```: 폴더 모두 지우기(매우 위험)
- ```rm <filename>```: remove
- ```cp <filename> <rename> <destination>```: copy
- ```mv <filename> <destination>```: move
- ```touch <filename>```: 빈 파일로 만들기

텍스트 파일 내용 확인하기

- ```cat <filename>```: 텍스트 파일 화면에 출력
- ```head -5 <filename>```: 텍스트 파일 위에 5줄만 출력
- ```tail -7 <filename>```: 텍스트 파일 아래 7줄만 출력
- ```more <filename>```: 텍스트 파일 페이지 단위로 출력(```space``` 다음 페이지, ```q``` 나오기)
- ```less <filename>```: more 보다 편함

확장자 확인하기 -> 리눅스는 예전에는 확장자를 크게 상관하지 않아서 안보여줌(현재는 아님)

- ```file <filename>```: 어떤 종류의 파일인지 확인(확장자 보는것과 비슷)