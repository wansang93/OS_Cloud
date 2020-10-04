## 04-09 필수 개념과 명령어-파일 압축과 묶기, 파일 위치 검색

### 파일 압축과 묶기

1. 파일 압축, 압축 풀기
   - 압축파일 확장명은 ```xz```, ```bz2```, ```gz```, ```zip```, ```Z``` 등
   - ```xz```와 ```bz2```가 압축률이 좋음
   - 명령어(```xz```, ```bz2```, ```gz```, ```zip```, ```Z```)
     - ```xz <file_name>``` 압축
     - ```xz -d <file_name>.xz``` 압축풀기
     - ```bz2 <file_name>```
     - ```bz2 -d <file_name>.bz2```
   - 압축을 하면 windows와 달리 파일이 없어지고 압축이 됨
   - 따라서 cp 명령어로 복사해서 압축하면 좋음
   - 예외로 zip 명령어 등을 쓰면 windows 처럼 파일이 남고 압축이 됨

2. 파일 묶기, 풀기
   - 리눅스에서는 파일 압축과 파일 묶기가 별개임
   - 명령어(```tar```)
     - 옵션들: ```c```(묶기), ```x```(풀기), ```t```(경로 확인), ```f```(파일), ```v```(과정보기)
     - ```J```(tar+gzip), ```z```(tar+gzip), ```j```(tar+bzip2)
     - ```tar cvf my.tar /etc/sysconfig/```
     - ```tar cvfj file.tar.bz file1 file2 file3 file4```: file.tar.bz 이름으로 file4개를 묶어 압축

### 파일 위치 검색

파일 위치 검색

1. find
   - 명령어: ```find {경로} {옵션} {조건} {action}```
     - {옵션}: ```-name```, ```user {user_name}```, ```newer {전유저, 다음유저}```, ```-perm {허가권}```, ```-size {사이즈 크기}```
     - {action}: ```print```(기본), ```-exec 명령어 {} \;```(외부 명령 실행)
2. ```which {file_name}```: PATH에 설정된 디렉터리만 검색
3. ```whereis {file_name}```: 실행 파일, 소스, man페이지 파일 검색
4. ```locate {file_name}```: 파일 목록 데이터베이스에서 검색
