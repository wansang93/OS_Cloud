## 05-01 X 윈도 사용-바탕화면, 테마, GRUB 배경 설정

### 그놈(GNOME) 데스그탑 환경 설정

[실습1] X 윈도의 바탕 화면과 테마 설정

- 배경화면 다운로드 링크 [gnome-look.org](https://www.gnome-look.org/browse/cat/300/order/latest/)
- 태마 설정하기
  ``` bash
  su -c 'dnf -y install gnome-tweak-tool'
  gnome-tweaks
  ```
- 부트 창 배경화면 바꾸기
  ``` bash
  su -c 'mv /home/centos/다운로드/wall.png /boot/grub2'  # 사진 옮기기
  su -c 'ls -l /boot/grub2'  # 옮긴 사진 확인하기
  su -c 'gedit /etc/default/grub'  # 설정 값 바꾸기
    GRUB_TERMINAL_OUTPUT="console"  # 주석 처리하기
    GRUB_BACKGROUND="/boot/grub2/wall.png"  # 아랫줄에 추가하기
  su -c 'grub2-mkconfig -o /boot/grub2/grub.cfg'  # 설정 변경 확인
  reboot  # 재시작 후 결과 보기
  ```