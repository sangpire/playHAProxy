# Play HAProxy

 HAProxy 가 어떻게 동작하는지 살펴보자

# STEP

## HAProxy 를 띄워보자

공식 이미지 페이지 설명을 보면서 Docker 파일을 만들어보자

이미지 만들기
```shell
$ docker build -t my-haproxy .
```

설정 파일 검증
```shell
$ docker run -it --rm --name haproxy-syntax-check my-haproxy haproxy -c -f /usr/local/etc/haproxy/haproxy.cfg
```

RUN
```shell
$ docker run -d --name my-running-haproxy -p 8080:80 --sysctl net.ipv4.ip_unprivileged_port_start=0 my-haproxy
```

아래 에러 발생
```
2023-03-21 20:03:36 [ALERT] 079/110336 (1) : [haproxy.main()] No enabled listener found (check for 'bind' directives) ! Exiting.
```

인터넷 검색해서 최소한의 HAProxy 설정을 가져옴.


## Link
- [Docker Image](https://hub.docker.com/_/haproxy)
