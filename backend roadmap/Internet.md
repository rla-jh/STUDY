# 인터넷

---

## 1️⃣ 인터넷이란?

**컴퓨터들이 서로 통신 가능한 거대한 네트워크**

두 대의 컴퓨터가 통신할 때 서로 물리적으로 또는 무선으로 연결되어야 한다. 하지만 두 대의 컴퓨터만이 아닌 원하는 만큼의 컴퓨터를 연결하려면 매우 복잡해진다. 

![Untitled](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-1.png)

예를 들어 10대의 컴퓨터를 연결하는 경우 컴퓨터 당 9개의 플러그가 달린 45개의 케이블이 필요하다.

![Untitled](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-2.png)

이 문제를 해결하기 위해 네트워크의 각 컴퓨터는 **라우터**라고하는 특수한 소형 컴퓨터에 연결된다. 이 라우터에는 컴퓨터에서 보낸 메시지가 올바른 대상 컴퓨터에 도착하는지 확인한다.

이 라우터를 시스템에 추가하면 각 컴퓨터마다 단일 플러그와 10개의 플러그가 있는 하나의 라우터만 필요한 것이다.

![Untitled](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-3.png)

컴퓨터를 라우터에 연결하고, 라우터를 또 다른 라우터에 연결하면 무한히 확장할 수 있다.

![Untitled](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-5.png)

하지만 이러한 방식도 라우터끼리 연결되어 있는 네트워크외에 다른 네트워크에는 케이블을 연결할 수 없다.

전력 및 전화와 같이 이미 집에 연결된 케이블이 있다. 전화기 기반 시설은 이미 세계 어느 곳과도 연결되어 있으므로 완벽한 배선이다. 따라서 네트워크를 전화 시설과 연결하기 위해서는 **모뎀**이라는 특수 장비가 필요하다. 

모뎀은 네트워크 정보를 전화 시설에서 처리할 수 있는 정보로 바꾸며, 그 반대의 정보도 마찬가지이다.

![Untitled](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-6.png)

그래서 네트워크는 전화 시설에 연결되고, 우리의 네트워크에서 도달하려는 대상 네트워크로 메시지를 보내는 것인데, 그렇게 하기 위해서는 우리의 네트워크를 **인터넷 서비스 제공 업체(Internet Service Provider, ISP)**에 연결한다. ISP는 모두 연결되는 몇몇 라우터를 관리하고 다른 ISP의 라우터에도 액세스 할 수 있는 회사이다.

![Untitled](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-7.png)

따라서 우리의 네트워크 메시지는 ISP 네트워크의 네트워크를 통해 대상 네트워크로 전달된다.

인터넷은 이러한 전체 네트워크 인프라로 구성된다.

## 2️⃣ HTTP란?

**HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜, 웹에서 이루어지는 모든 데이터 교환의 기초이며, 클라이언트-서버 프로토콜이기도 하다.**

클라이언트와 서버들은 개별적인 메시지 교환에 의해 통신한다.

브라우저인 클라이언트에 의해 전송되는 메시지를 **요청(requests)**이라고 부르고, 이에 대해 서버에서 응답으로 전송되는 메시지를 **응답(responses)**이라고 부른다.

### ✔️ HTTP 흐름

1. TCP 연결 - TCP 연결은 요청을 보내거나 응답을 받는데 사용된다. 
2. HTTP 메시지 전송 

```
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```

1. 서버에 의해 전송된 응답 받기

```
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html... (here comes the 29769 bytes of the requested web page)
```

1. 연결을 닫거나 다른 요청들을 위해 재사용한다.

### ✔️ HTTP 요청

- HTTP 메서드 (GET, POST 등)
- 가져오려는 리소스의 경로
- HTTP 프로토콜 버전
- 서버에 대한 추가 정보를 전달하는 선택적 헤더들

![Untitled](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview/http_request.png)

### ✔️ HTTP 응답

- HTTP 프로토콜 버전
- 요청의 성공 여부와 상태 코드
- 상태메시지
- 요청 헤더와 비슷한 HTTP 헤더

![Untitled](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview/http_response.png)

## 3️⃣ 브라우저 개념과 동작 방식

**웹에서 페이지를 찾아서 보여주고 사용자가 하이퍼링크를 통해 다른 페이지로 이동할 수 있도록 하는 프로그램**

### 기능

사용자가 선택한 자원을 서버에 요청하고 브라우저에 표시한다.

HTML과 CSS 명세에 따라 HTML 파일을 해석해서 표시한다.

### 기본 구조

- 사용자 인터페이스 : 주소 표시줄, 이전/다음 버튼, 북마크 메뉴 등 요청한 페이지를 보여주는 창 외에 모든 부분
- 브라우저 엔진 : 사용자 인터페이스와 렌더링 엔진 사이의 동작 제어
- 렌더링 엔진 : 요청한 콘텐츠 표시 (HTML을 요청하면 HTML과 CSS를 파싱하여 화면에 표시)
- 통신 : HTTP 요청과 같은 네트워크 호출에 사용된다.
- UI 백엔드 : 콤보 박스와 창 같은 기본적인 장치를 그린다. OS 사용자 인터페이스 체계를 사용한다.
- 자바스크립트 해석기 : 자바스크립트 코드를 해석하고 실행한다.
- 자료 저장소 : 쿠키를 저장하는 것과 같이 모든 종류의 자원을 저장한다.

![Untitled](https://d2.naver.com/content/images/2015/06/helloworld-59361-1.png)

### 렌더링 엔진

**요청 받은 내용을 브라우저 화면에 표시하는 일**

- 파이어폭스의 렌더링 엔진 → 게코(Gecko)
- 사파리, 크롬의 렌더링 엔진 → 웹킷(Webkit)

**렌더링 엔진의 동작 과정**

![Untitled](https://d2.naver.com/content/images/2015/06/helloworld-59361-2.png)

HTML 문서를 파싱하고 “콘텐츠 트리” 내부에서 태그를 DOM 노드로 변환한다. 그 다음 CSS 파일도 파싱한다.

스타일 정보와 HTML 표시 규칙은 “렌더 트리"라고 부르는 또 다른 트리를 생성한다.

렌더트리는 정해진 순서대로 화면에 표시한다.

렌더 트리 생성이 끝나면 배치가 시작된다.

렌더링 엔진은 모든 HTML을 파싱할 때 까지 기다리지 않고 배치와 그리기 과정을 시작한다. 네트워크로부터 나머지 내용이 전송되기를 기다리는 동시에 받은 내용의 일부를 먼저 화면에 표시한다.

## 4️⃣ DNS 개념과 동작 방식

**DNS(Domain Name System) - 사람이 읽을 수 있는 도메인 이름(www.amazon.com)을 기계가 읽을 수 있는 IP주소로 변환한다.**

인터넷 상의 모든 컴퓨터는 숫자를 사용하여 서로를 찾고 통신한다. 이러한 숫자를 IP 주소라고 한다.

웹 브라우저를 열고 웹 사이트로 이동할 때 긴 IP주소를 기억하기는 불편하기 때문에 example.com 과 같은 도메인 이름을 입력해도 동일한 웹 사이트로 갈 수 있다.

### 동작 방식

1. 브라우저의 위치 표시줄에 example.com와 같은 도메인 이름을 입력한다.
2. 브라우저는 이 도메인의 이름(로컬 DNS 캐시 사용)으로 식별된 IP 주소를 이미 인식하고 있는지 컴퓨터에 묻는다. 인식하고 있다면 도메인 이름이 IP주소로 변환되고 브라우저는 웹서버와 내용을 협상한다.
3. 컴퓨터가 도메인의 이름에 해당하는 IP를 모를 경우 DNS 서버에 계속 요청한다. (DNS 서버의 작업은 정확히 어떤 IP 주소가 등록된 각 도메인 이름과 일치하는지 컴퓨터에 알려주는 것이다)
4. 컴퓨터가 요청된 IP주소를 알고 있으므로 브라우저는 웹 서버와 콘텐츠를 협상할 수 있다.

![Untitled](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_domain_name/2014-10-dns-request2.png)

## 5️⃣ 도메인 이름이란?

**IP 주소가 사람이 이해하고 기억하기 어렵기 때문에 각 IP에 이름을 부여하는 것이 도메인이라고 한다.**

> **IP란?**
**인터넷에 연결되어 있는 장치들이 각각의 장치를 식별할 수 있는 주소**
> 

### 구성 요소

도메인 = 컴퓨터 이름 + 최상위 도메인

ex) daum.co.kr

- daum : 컴퓨터 이름
- co : 국가 형태의 최상위 도메인
- kr : 대한민국의 NIC에서 관리하는 도메인

### 호스트

네트워크에 연결되어 있는 컴퓨터들

### 호스트 설정

도메인을 호스트의 IP에 연결하는 것

- **하나의 도메인으로 여러개의 호스트에 연결하기**

![Untitled](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/121/784.png)

## 6️⃣ 호스팅이란?

**서버의 전체 혹은 일부를 이용할 수 있도록 임대해주는 서비스**

- **웹 호스팅** : 여러 고객이 하나의 서버를 함께 사용하는 형태, 하나의 서버를 나누어 쓰기 때문에 저렴하게 이용할 수 있고, 호스팅 업체의 통합 관리를 받기에 편리하다. 그러나 사용할 수 있는 하드웨어가 제한적이다.
- **서버 호스팅** : 고객이 단독으로 서버를 사용하는 형태, 넓은 하드웨어 공간을 사용할 수 있고, 서버 운영/관리에 대한 직접적인 권한을 가질 수 있다. 하지만 단독으로 서버를 이용하기에 비용이 높은 편이다.
- **클라우드 서버** : 서버 호스팅을 가상화한 것으로 가상 서버를 단독으로 사용할 수 있는 형태, 고객이 필요할 때마다 서버 자원을 늘리거나 축소하여 유연하게 서버를 이용할 수 있다. 하지만 하나의 가상 서버에 문제가 생기면 연결된 다른 가상 서버에도 문제가 생길 수 있다.

---

**참고 자료**


[인터넷은 어떻게 동작하는가? - Web 개발 학습하기 | MDN](https://developer.mozilla.org/ko/docs/Learn/Common_questions/How_does_the_Internet_work)

[HTTP 개요 - HTTP | MDN](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview)

[브라우저 - 용어 사전 | MDN](https://developer.mozilla.org/ko/docs/Glossary/Browser)

[웹페이지를 표시한다는 것: 브라우저는 어떻게 동작하는가 - Web Performance | MDN](https://developer.mozilla.org/ko/docs/Web/Performance/How_browsers_work)

[NAVER D2](https://d2.naver.com/helloworld/59361)

[DNS란 무엇입니까? - DNS 소개 - AWS](https://aws.amazon.com/ko/route53/what-is-dns/?nc1=h_ls)

[What is a domain name? - Web 개발 학습하기 | MDN](https://developer.mozilla.org/ko/docs/Learn/Common_questions/What_is_a_domain_name)

[도메인이란? - 생활코딩](https://opentutorials.org/course/228/1450)

[다들 호스팅, 호스팅 하는데, '호스팅 뜻'은? - wishket](https://blog.wishket.com/%ED%98%B8%EC%8A%A4%ED%8C%85%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C-%EA%B7%B8%EB%A6%B0%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8/)

[호스트 설정 - 생활코딩](https://opentutorials.org/course/228/1453)
