## 07-02 셸스크립트-다양한 프로그래밍 연습

### 기본 if 문

```shell
if [조건]
then
  참일경우 실행
else
  거짓일 경우 실행
fi
```

### 비교 연산자

비교 연산

![07-02비교연산](assets/07-02비교연산.png)

파일 조건 연산

![07-02파일조건연산](./assets/07-02파일조건연산.png)

파일 조건 연산 응용 셸 파일

```shell
#!/bin/sh
fname = /lib/systemd/system/sshd.service
if [-f$fname]
then
  head -5 $fname
else
  echo "sshd 서버가 설치되지 않았습니다."
fi
exit 0
```

### case~esac문

c언어의 case문과 비슷

```shell
#!/bin/sh
case "$1"in
  start)
    echo"시작~~";;
  stop)
    echo"중지~~";;
  restart)
    echo"다시 시작~~";;
  *)
    echo"뭔지 모름~~";;
esac
exit 0
```

```shell
#!/bin/sh
read answer
case "$answer"in
  yes|y|Y|Yes|YES)
    echo"YES 입니다.";;
  [nN]*)
    echo"No 입니다";;
  *)
    echo"YES / NO 중 하나를 입력하세요";;
    exit 1;;
 esac
exit 0
```

### AND, OR 관계 연산자

- and: `-a` or `&&`
- or: `-o` or `||`

### 반복문 -for문, -while문

for문

```shell
for 변수 in 값1 값2 값3
do
  반복할 문장
done
```

```shell
for fname in $(ls *.sh)
do
  실행
done
exit 0
```

while문

while `[1]` 또는 `[:]` 이 오면 무한루프 생성

```shell
while [1]
do
  실행할 문장
done
exit 0
```

1에서 10까지 합계를 출력

```shell
#!/bin/sh
hap=0
i=1
while [$i -le 10]
do
  hap='expr $hap + $i'
  i='expr $i + 1'
done
echo "1부터 10까지의 합: "$hap
```

패스워드가 참일 때 까지 입력을 받기

```shell
#!/bin/sh
echo "비밀번호를 입력하세요."
read mypass
while [$mypass != "1234"]
do
  echo "wrong, retry"
  read mypass
done
echo "pass"
exit 0
```

### until문

while문과 동일하지만 조건이 참일 때까지 계속 반복

### break, continue, exit, return 문

```shell
break;;
continue;;
exit 1;;
```

### 사용자 정의 함수

```shell
함수이름 () {
  함수 내용
}
함수이름  # 함수 호출
```

### eval

문자열을 명령문으로 인식하고 실행

```shell
#!/bin/sh
str="ls-l eval.sh"
echo $str
eval $str
exit 0
```

### export

외부 변수를 선언, 선언한 변수를 다른 프로그램에서도 사용할 수 있도록 도와줌

### printf

C언어의 printf() 함수와 비슷하게 형식 지정 출력

### set과 $(명령어)

리눅스 명령어를 결과로 사용하기 위해서 `$(명령어)` 형식을 사용

결과를 파라미터로 사용하고자 할 때 set과 함께 사용

```shell
#!/bin/sh
echo "오늘 날짜는 $(date)입니다."
set $(date)
echo "오늘은 $4 요일 입니다."
exit 0
```

### shift

파라미터 변수를 왼쪽으로 한 단계씩 아래로 쉬프트 시킴

```shell
#!/bin/sh
myfunc() {
  str=""
  while ["$1"=""]; do
    str="$str $1"
    shift
  done
  echo $str
}
```
