## CORS
**Cross-Origin Resource Sharing**

> 교차 출처 리소스 공유

 1. 추가 http 헤더를 통해 웹 페이지에서 최초 서비스된 도메인 밖의 다른 도메인으로부터 리소스를 요청할 수 있도록 허용하는 구조
 2. 자신의 출처(도메인, 포트 등)이 다를 때 실행됨
 3. 개발시 로컬에서 프론트, 백의 포트가 다르므로 보안 목적으로 차단됨
 4. 서버-클라이언트가 분리되어 있다면  Cors미들웨어나 서버측에서 승인해 줄 수 있도록 설계



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