## CORS
**Cross-Origin Resource Sharing**

> 교차 출처 리소스 공유

 1. 추가 http 헤더를 통해 웹 페이지에서 최초 서비스된 도메인 밖의 다른 도메인으로부터 리소스를 요청할 수 있도록 허용하는 구조
 2. 자신의 출처(도메인, 포트 등)이 다를 때 실행됨
 3. 개발시 로컬에서 프론트, 백의 포트가 다르므로 보안 목적으로 차단됨
 4. 서버-클라이언트가 분리되어 있다면  Cors미들웨어나 서버측에서 승인해 줄 수 있도록 설계



## CSRF

> **사이트 간 요청 위조**(또는 **크로스 사이트 요청 위조**, [영어](https://ko.wikipedia.org/wiki/영어): Cross-site request forgery, **CSRF**, **XSRF**)는 [웹사이트](https://ko.wikipedia.org/wiki/웹사이트) [취약점 공격](https://ko.wikipedia.org/wiki/취약점_공격)의 하나로, 사용자가 자신의 의지와는 무관하게 공격자가 의도한 행위(수정, 삭제, 등록 등)를 특정 웹사이트에 요청하게 하는 공격을 말한다.
>
> 유명 경매 사이트인 [옥션](https://ko.wikipedia.org/wiki/옥션_(웹사이트))에서 발생한 개인정보 유출 사건에서 사용된 공격 방식 중 하나다.
>
> [사이트 간 스크립팅](https://ko.wikipedia.org/wiki/사이트_간_스크립팅)(XSS)을 이용한 공격이 사용자가 특정 웹사이트를 신용하는 점을 노린 것이라면, 사이트간 요청 위조는 특정 웹사이트가 사용자의 [웹 브라우저](https://ko.wikipedia.org/wiki/웹_브라우저)를 신용하는 상태를 노린 것이다. 일단 사용자가 웹사이트에 [로그인](https://ko.wikipedia.org/wiki/로그인)한 상태에서 사이트간 요청 위조 공격 코드가 삽입된 페이지를 열면, 공격 대상이 되는 웹사이트는 위조된 공격 명령이 믿을 수 있는 사용자로부터 발송된 것으로 판단하게 되어 공격에 노출된다.
>
> [위키](https://ko.wikipedia.org/wiki/%EC%82%AC%EC%9D%B4%ED%8A%B8_%EA%B0%84_%EC%9A%94%EC%B2%AD_%EC%9C%84%EC%A1%B0)





## 동일 출처 정책
**Same-Origin poicy**

> The  **same-origin policy**  is a critical security mechanism that restricts how a document or script loaded from one  [origin](https://developer.mozilla.org/en-US/docs/Glossary/origin)  can interact with a resource from another origin. It helps isolate potentially malicious documents, reducing possible attack vectors. 

어떤 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 중요한 보안 방식입니다. 동일 출처 정책은 잠재적으로 해로울 수 있는 문서를 분리함으로써 가능한 공격 경로를 줄이는데 도움을 줍니다.([https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy))



## Axios
**Promise 기반의 HTTP 통신 라이브러리**

> Promise based HTTP client for the browser and node.js

참고 - [https://www.npmjs.com/package/axios](https://www.npmjs.com/package/axios)
[https://github.com/axios/axios#example](https://github.com/axios/axios#example)

<script src="https://gist.github.com/insolk/7cc3a3a9b7ed98046b280c6a6595d440.js"></script>

### Server-Side Rendering

- 서버 단에서 html을 그려서 클라이언트로 보내지는 방식
- JSP, Thymeleaf, Django, PHP
- 기존 웹페이지 방식에서 많이 쓰였음
- Synchronous(동기)방식으로 통신
  - request을 보내고 response가 올 때 까지 클라이언트는 wait
- 일부분만 바꿔도 될 때에도 전체를 다시 갱신해야 하기 때문에 계속 대기하기 때문에 속도가 느림



### Client-Side Rendering

- server에서는 data(xml, json, csv등)만 보내주고, 클라이언트에서 html에 작성하는 방식
- REST(REpresentional State Transfer)
  - HTTP URL(Resource) + HTTP Method(GET, POST, PUT, DELETE)
- Postman - Chrome API
  - REST Client

- AJax(Asynchronous Javascript and XML)
- Asynchronous(비동기)방식으로 통신
  - request을 보내고 response가 올 때 까지 클라이언트는 wait하지 않고 다른 일 수행
  - JS의 XmlHttpRequest(XHR)가 비동기 방식으로 통신을 해주는 역할을 담당

url 쿼리 스트링 작성법

- `https://url.com?attr1=1&attr2=2...`
- 개발자 도구에서 **request URL**과 **Form data** 적절히 이용

### webserver

- Apache, Nginx

### Static Web Application

- 기존 웹 방식
- 정적으로 html코드를 작성하여 사용하는 방식

### Dynamic Web Application

- 동적으로 사용자 별로 화면을 다르게 표현
- DB와 연동하여 데이터를 불러오고 저장하는 방식