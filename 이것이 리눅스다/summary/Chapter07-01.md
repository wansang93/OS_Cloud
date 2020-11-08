## 07-01 셸스크립트-셸 스크립트 개요, 작성법, 실행법, 변수

### CentOS의 bash 셸

기본 셸은 bash(Bourne Again SHell)

BASH 셸의 특징
- Alias(명령어 단축 기능)
- History(위/아래 화살표키)
- 연산
- Job Control
- 자동 이름 완성
- 프롬프트 제어
- 명령 편집

예전에는 여러가지 셸이 있었는데 요즘은 배쉬를 씀

### 환경 변수

환경변수 보기: `echo $환경변수이름`
환경변수 수정: `export 환경변수=값`

주요 환경변수

![07-01환경변수](assets/07-01환경변수.png)

### 셸 스크립트 프로그래밍

C언어와 유사, 변수, 반복문, 제어문 사용, vi나 gedit으로 작성 가능, 리눅스의 많은 부분이 셸로 작성되어있음

셸 스크립트의 확장자는 `*.sh` 로 하는게 좋음

셸 파일 만들기

1. vi 로 작성
   파일 생성 후 다음과 같이 작성
   ```shell
   #!/bin/sh
   echo "사용자 이름" $USER
   echo "홈 폴더" $HOME
   exit 0
   ```

2. 실행 방법
   1. `sh <스크립트 파일>` 로 실행
   2. `chmod +x <스크립트 파일>` 명령으로 실행 가능 하게 하고 `./<스크립트 파일>`로 실행

### 변수의 기본

- 변수를 대입할 때 `=` 좌우에는 공백이 없어야 함
- 모든 변수는 문자열로 취급
- 변수 이름은 대소문자를 구분

### 변수의 입력과 출력

```shell
#!/bin/sh
myvar="Hi Woo"  # 변수 myvar 선언
echo $myvar  # myvar 출력
echo "$myvar"  # myvar 출력
echo '$myvar'  # $myvar 그대로 출력
echo \$myvar  # $myvar 그대로 출력
echo 값 입력:
read myvar  # 입력한 값을 myvar 변수에 저장
echo '$myvar' = $myvar  # 다음과 같이 출력
exit 0
```

### 숫자 계산

- 연산을 하려면 `expr`을 반드시 입력
  ```shell
  num1=100
  num3='expr\($num1 + 200\) \* 2'
  ```
- 괄호(`(`, `)`)나 곱하기(`*`)는 `\`를 반드시 붙여줘야 함

### 파라미터(Parameter) 변수

- 파라미터 변수는 `$0`, `$1`, `$2` ... 형태를 가짐
- 전체 파라미터는 `$*` 로 표현

paravar.sh 파일 만들기
```shell
#!/bin/sh
echo "실행파일은 이름은 <$0>이다"
echo "첫번째 파라미터는 <$1>이고, 두번째 파라미터는 <$2>다"
echo "전체 파라미터는 <$3>다"
exit 0
```

```bash
sh paravar.sh 값1 값2 값3
```