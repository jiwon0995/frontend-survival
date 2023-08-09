## Express

> Express는 Node.js를 위한 웹 프레임워크이다.   
> Node.js의 HTTP 모듈을 사용하여 HTTP 서버를 만든다.   

**Express는 다음과 같은 기능을 제공한다.**

1. HTTP 통신 요청(Request : GET, POST, PUT, DELETE)에 대한 핸들러를 제공한다.
2. HTTP 통신 응답(Response)을 만들기 위해 view의 렌더링 엔진과 연결한다.
3. 접속을 위한 포트나 응답 렌더링을 위한 템플릿 위치같은 공통 웹 어플리케이션 설정을 제공한다.
4. 핸들링 파이프라인 중 필요한 곳에 미들웨어를 처리 요청을 추가한다.


## URL 구조

URL(Uniform Resource Locator)이란 웹에 게시된 리소스의 위치를 나타낸다.

**URL 분석하기**

 ```https://www.frontendsurvival.com:80/week4/express?name=jiwon&study=frontend```

> **scheme : http or https**   
스키마는 브라우저가 리소스를 요청하는데 사용하는 프로토콜을 나타낸다.   
http는 보안이 안된 프로토콜이고 일반적으로는 보안 인증키를 가지고 있는 https를 사용한다.

> **authority : www.frontendsurvival.com:80**  
Authority는 스키마 뒤에 '://'로 구분된다.   
Authority는 도메인과 포트로 구성되어 있다. 포트는 표준 포트(http:80, https:443)를 사용할 경우 생략할 수 있다.

> **path to resource : /week4/express**   
Path는 리소스의 경로를 나타낸다.   

> **parameters : ?name=jiwon&study=frontend**  
파라미터는 웹 서버에 제공되는 매개변수이다. 쿼리스트링으로 표현되며, ?로 시작한다. key=value 형태로 표현되며, 여러개의 파라미터는 &로 구분한다. 

**HTML에서 URL 사용하기**

> `<a>` 태그를 사용하여 다른 페이지로 이동할 수 있다.   
`<link>` or `<script>` 태그를 사용하여 리소스를 가져올 수 있다.   
`<img>, <video>, <audio>` 태그를 사용하여 미디어 리소스를 가져올 수 있다.  
`<iframe>` 태그를 사용하여 다른 페이지를 가져올 수 있다.

## REST API & HTTP Method(CRUD)

> REST API **HTTP URL로 리소스를 명시**하고, **HTTP Method**를 통해 해당 리소스에 대한 **CRUD Operation**을 적용한다.

> CRUD란 Create, Read, Update, Delete의 약자로 데이터의 생성, 조회, 수정, 삭제를 의미한다.

> REST API에서는 다음 Method를 사용해서 CRUD Operation을 적용한다.   
> **GET** : Read   
> **POST** : Create   
> **PATCH, PUT** : Update   
> **DELETE** : Delete

> GET : 클라이언트는 GET을 아용해 서버의 지정된 URL에 있는 리소스에 요청을 보낸다. 파라미터를 넣어서 데이터를 필터링하거나 정렬할 수 있다.   

> POST : 클라이언트는 POST를 이용해 서버의 지정된 URL에 리소스를 생성한다.

> PUT : 클라이언트는 PUT을 이용해 서버의 지정된 URL에 리소스를 수정한다.

> DELETE : 클라이언트는 DELETE를 이용해 서버의 지정된 URL에 리소스를 삭제한다.