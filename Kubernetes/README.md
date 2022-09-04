# 쿠버네티스(Kubernates)

docs link -> [https://kubernetes.io/docs/home/](https://kubernetes.io/docs/home/)

## 면접 질문 리스트

> [출저: unhochoi 블로그](https://wooono.tistory.com/109#:~:text=%EC%BF%A0%EB%B2%84%EB%84%A4%ED%8B%B0%EC%8A%A4%EB%8A%94%20'%EB%8F%84%EC%BB%A4,%ED%88%B4'%EC%9D%B4%EB%9D%BC%EA%B3%A0%20%EC%83%9D%EA%B0%81%ED%95%98%EB%A9%B4%20%EB%90%9C%EB%8B%A4.&text=%EC%A6%89%2C%20%EB%8F%84%EC%BB%A4%EB%8A%94%20'%ED%95%9C%20%EA%B0%9C%EC%9D%98,%ED%95%98%EB%8A%94%20%EB%8D%B0%20%EC%B5%9C%EC%A0%81%ED%99%94%EB%90%98%EC%96%B4%EC%9E%88%EB%8B%A4.)

### 도커와 쿠버네티스의 차이

- 도커와 쿠버네티스 비교 예시
  - 컨테이너 하나 띄워서 사용해야지 => 도커
  - 0월 0시에 100개의 컨테이너를 자동으로 생성해야지 => 쿠버네티스
- 간단 설명
  - 도커는 **기술적인 개념이자 도구**
  - 이미지를 컨테이너에 띄우고 실행하는 기술이 도커
  - 즉, 도커는 **한 개의 컨테이너**를 관리하는 데 최적
  - 쿠버네티스는 **도커를 관리하는 툴**
  - 이런 도커를 기반으로 컨테이너를 관리하는 서비스가 쿠버네티스
  - 즉, 쿠버네티스는 **여러 개의 컨테이너**를 서비스 단위로 관리하는 데 최적
