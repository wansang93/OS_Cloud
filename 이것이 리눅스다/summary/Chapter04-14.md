## 04-14 필수 개념과 명령어-응급 복구, GRUB 부트로더

### 응급 복구

[실습16] root 비밀번호 분실 시

1. GRUB(처음 부팅시 나오는) 화면이 나오면 5초 안에 키보드 누르기
2. press ```e```
3. linux 끝에 ```rhgb quiet``` 을 지우고 끝에 ```init=/bin/sh``` 써주기(응급복구 모드로 들어가기) -> ```Ctrl``` + ```x``` (확인)
4. ```passwd``` 비밀번호 바꾸기 -> 에러발생
5. 에러 발생 이유 찾기 ->  ```mount``` 입력 /(루트) 파티션이 ro(read only)여서 쓰기가 불가능
6. ```mount -o remount, rw  /``` -> read    wirte로 변경
7. 다시 ```passwd```로 비밀번호 변경 후 재시작

### GRUB 부트로더

GRUB 부트로더의 특징
- 부트 정보를 사용자가 임의로 변경해 부팅 가능
- 즉 부트 정보가 올바르지 않더라도 수정하여 부팅 가능
- 다른 여러 가지 운영체제와 멀티 부팅 가능

GRUB2의 장점
- 셀 스크립트를 지원, 조건식과 함수를 사용 가능
- 동정 모듈을 로드
- 그래픽 부트 메뉴를 지원하며 부트 스플래시 성능이 개선
- ISO 이미지를 이용해서 바로 부팅 가능
- 설정 파일의 형식이 변경되었지만 더 향상된 내용을 포함할 수 있음

GRUB2 설정 방법
- ```/boot/grub2/grub.cfg``` 설정파일을 직접 변경하면 안됨
- ```/etc/default/grub``` 파일과 ```/etc/grub.d/``` 디렉토리 파일을 수정 후에 ```grub2-mkconfig```명령어를 실행해 설정함

[실습17] GURB 부트로더 변경

``` bash
vi  /etc/default/grub
grup2-mkconfig -o /boot/grub2/grub.cfg

cd /etc/grub.d/
vi 00_header
# 제일 아래 추가
    cat << E0F
    set  superuser="thisislinux"
    password thisislinux 4321
    E0F
grup2-mkconfig -o /boot/grub2/grub.cfg
reboot
```
