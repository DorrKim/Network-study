## HTTP/0.9 - 초기버젼

HTTP의 초기버젼으로 원래는 버젼번호가 없으나 구별하기위해 0.9로 불림
요청은 한줄로 표시되며 GET메서드가 유일

> GET /index.html

## HTTP/1.0 - 프로토콜의 기능을 확장

제한적이었던 HTTP/0.9를 확장하여 클라이언트 서버 모두 융통적인 통신이 가능하도록 함

- 버전 전보를 요청 구문 사이에 기록
- 상채라인을 응답 메세지의 시작부분에 부착하여 클라이언트가 요청의 대한 서버의 수행결과 상태를 알게하고 그애 대한 추후 동작을 가능하게 함
- HTTP헤더 개념을 응답, 요청에 도입하여 프로토콜의 유연성과 확장을 가능하게 함
- Content-Type과 같은 새로운 헤더로 HTML파일 만이 아닌 다른 문서도 전송 가능해짐

```
GET /mypage.html HTTP/1.0
User-Agent: NCSA_Mosaic/2.0 (Windows 3.1)

200 OK
Date: Tue, 15 Nov 1994 08:12:31 GMT
Server: CERN/3.0 libwww/2.17
Content-Type: text/html
<HTML>
A page with an image
  <IMG SRC="/myimage.gif">
</HTML>
```

## HTTP/1.1 - 표준적인 프로토콜

모호함을 명확하게 하고 많은 개선사항 도입

- 커넥션을 재사용 및 지속 연결 초기에 하나의 요청/응답시 마다 연결을 해제하는 방식에서 벗어나 TCP연결을 지속
- 파이프 라인화: 첫번떄 요청에대한 응답이 오기전에 두번쨰 요청이 가능하게 하여 요청에 대한 응답을 일일히 기다린후 다음 요청을 보내지 않아도 됨, 따라서 지연시간이 줄어듬
- 추가적인 캐시제어 매커니즘이 도입
- Host 헤더의 추가로 동일 IP에 다른 도메인을 호스팅 하는 기능을 가능하게 함

```
GET /en-US/docs/Glossary/Simple_header HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/en-US/docs/Glossary/Simple_header

200 OK
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Wed, 20 Jul 2016 10:55:30 GMT
Etag: "547fa7e369ef56031dd3bff2ace9fc0832eb251a"
Keep-Alive: timeout=5, max=1000
Last-Modified: Tue, 19 Jul 2016 00:59:33 GMT
Server: Apache
Transfer-Encoding: chunked
Vary: Cookie, Accept-Encoding

(content)


GET /static/img/header-background.png HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/en-US/docs/Glossary/Simple_header

200 OK
Age: 9578461
Cache-Control: public, max-age=315360000
Connection: keep-alive
Content-Length: 3077
Content-Type: image/png
Date: Thu, 31 Mar 2016 13:34:46 GMT
Last-Modified: Wed, 21 Oct 2015 18:27:50 GMT
Server: Apache

(image content of 3077 bytes)
```

## HTTP/2.0

- 텍스트 프로토콜에서 이진 프로토콜로의 변환
- 순서가 제거된 다중화 프로토콜
- 전송됭 데이터들간의 중복제거, 유사한 내용의 헤더를 압축
