## 📍 Location & Pathname  
Window.location 은 현재 URL 정보를 가진 Location 객체를 반환한다.

**location object**

>예시 주소 : http://www.example.com:8080/products?id=1234&page=1#top

- location.href   
전체 URL이 포함된 문자열을 반환한다.   
`http://www.example.com:8080/products?id=1234&page=1#top`   

- location.protocol   
프로토콜을 반환한다.   
`http:`   

- location.host   
호스트 이름과 포트 번호를 반환한다.   
`www.example.com:8080`

- location.hostname   
호스트 이름을 반환한다.   
`www.example.com`

- location.pathname   
경로를 반환한다.   
`/products`

- location.search   
쿼리 문자열을 반환한다.   
`?id=1234&page=1`

- location.hash   
해시 문자열을 반환한다.   
`#top`

**Location Instance Method**   

- assign(url)   
매개변수로 받은 url을 새로운 문서에 로드한다.   

- reload()   
현재 문서를 다시 로드한다.   

- replace(url)   
매개변수로 받은 url을 새로운 문서에 로드한다. 이전 문서는 history에 남지 않는다.   

- toString()   
전체 URL이 포함된 문자열을 반환한다.

---

## ✏️ 정리
- 공부한 내용   
    * [x] location 객체의 속성과 메서드
