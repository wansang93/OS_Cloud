## 05-02 X 윈도 사용-노틸러스, Firefox 업그레이드

### 파일 브라우저 - 노틸러스

[실습2] 노틸러스 사용

- 노틸러스: ```시작```(```현재 활동```) -> ```파일```
  - 파일이 노틸러스 임, 윈도우즈 파일 탐색기랑 비슷함
- 기본 프로그램: ```바탕화면``` -> ```마우스 오른쪽 클릭``` -> ```설정``` -> ```자세히 보기``` -> ```기본 프로그램```
- 브라세로: ```시작``` -> ```프로그램 표시``` -> ```브라세로```
  - CD/DVD record 해주는 프로그램

### Firefox

[실습3] Firefox 업그래이드

- Firefox 버전 확인
  ``` bash
  rpm -qi firefox
  ```
- 최신버전 다운로드
  - 링크 -> [https://www.mozilla.org/ko/firefox/download/thanks/](https://www.mozilla.org/ko/firefox/download/thanks/)
  - terminal 에서
    ``` bash
    cd 다운로드/
    ls
    tar xjf firefox-81.0.2.tar.bz2 
    su -
    mv firefox /usr/local
    chown -R root.root /usr/local/firefox/  # -R 옵션은 하위 파일, 폴더 모두 소유주 바꾸기
    cd /usr/local/bin/
    ln -s /usr/local/firefox/firefox .  # 현재 폴더에 링크 만들기
    ls -l fire*  # 확인
    # firefox 실행하면 끝
    ```
