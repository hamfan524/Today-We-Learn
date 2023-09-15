# REST

# 💯 REST의 정의

```
"REpresentational State Transfer" 의 약자로,

자원을 이름(자원의 표현)으로 구분해 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미합니다.

어떤 자원에 대해 CRUD(Create, Read, Update, Delete) 연산을 수행하기 위해 URI(Resource)로

GET, POST 등의 방식(Method)을 사용하여 요청을 보내며, 요청을 위한 자원은 특정한 형태
(Representation of Resource)로 표현됩니다.
```

<br>

즉, **자원(resource)**의 **표현(representation)**에 의한 **상태 전달**을 뜻합니다.

- **자원** **:** 해당 소프트웨어가 관리하는 모든 것 ( 문서, 그림, 데이터, 해당 소프트웨어 자체 등 )
- **표현 :** 그 자원을 표현하기 위한 이름 ( DB의 학생 정보가 자원이면, 'students'를 자원의 표현으로 정함 )
- **상태 전달 :** 데이터가 요청되는 시점에 자원의 상태를 전달한다. ( JSON 혹은 XML을 통해 데이터를 주고 받는 것이 일반적 )

- 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍쳐 스타일
- 네트워크 상에서 **Client 와 Server 사이의 통신 방식** 중 하나

<br><br>

# REST의 개념

- HTTP URI 를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT DELETE) 를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미
  - 즉 REST는 자원 기반의 구조(ROA, Resource Oriented Architecture) 설계의 중심에 Resource가 있고 HTTP Method를 통해 Resource를 처리하도록 설계된 아키텍쳐를 의미
  - 웹 사이트의 이미지, 텍스트, DB 내용 등의 모든 자원에 고유한 ID인 HTTP URI를 부여한다.
  - CRUD Operation
    - Create: 생성(POST)
    - Read: 조회(GET)
    - Update: 수정(PUT)
    - Delete: 삭제(DELETE)
    - HEAD: header 정보 조회(HEAD)

| GET    | Read : 정보 요청, URI가 가진 정보를 검색하기 위해 서버에 요청한다.                  |
| ------ | ----------------------------------------------------------------------------------- |
| POST   | Create : 정보 입력, 클라이언트에서 서버로 전달하려는 정보를 보낸다.                 |
| PUT    | Update : 정보 업데이트, 주로 내용을 갱신하기 위해 사용한다. (데이터 전체를 바꿀 때) |
| PATCH  | Update : 정보 업데이트, 주로 내용을 갱신하기 위해 사용한다. (데이터 일부만 바꿀 때) |
| DELETE | Delete : 정보 삭제, (안전성 문제로 대부분 서버에서 비활성화한다.)                   |

---

<br><br>

# REST의 특징

**1. Server-Client (서버-클라이언트 구조)**

- 자원이 있는 쪽이 Server, 자원을 요청하는 쪽이 Client가 됩니다.
  - REST Server는 API를 제공하고 비즈니스 로직 처리 및 저장을 책임지고,
  - Client는 사용자 인증이나 context( 세션, 로그인 정보 ) 등을 직접 관리하고 책임집니다.
  - 역할을 확실히 구분시킴으로써 서로 간의 의존성을 줄입니다.

**2. Stateless (무상태)**

- HTTP 프로토콜은 Stateless Protocol이므로 REST 역시 무상태성을 갖습니다.
- Client의 context를 Server에 저장하지 않습니다.
  - 즉, 세션과 쿠키와 같은 context 정보를 신경쓰지 않아도 되므로 구현이 단순해집니다.
- Server는 각각의 요청을 완전히 별개의 것으로 인식하고 처리합니다.
  - 각 API 서버는 Client의 요청만을 단순 처리합니다.
  - 즉, 이전 요청이 다음 요청의 처리에 연관되어서는 안됩니다. ( DB에 의해 바뀌는 것은 허용 )
  - Server의 처리 방식에 일관성을 부여하기 때문에 서비스의 자유도가 높아집니다.

**3. Cacheable (캐시 처리 기능)**

- 웹 표준 HTTP 프로토콜을 그대로 사용하므로 웹에서 사용하는 기존의 인프라를 그대로 활용할 수 있습니다.
  - 즉, HTTP가 가진 가장 강력한 특징 중 하나인 캐싱 기능을 적용할 수 있습니다.
  - HTTP 프로토콜 표준에서 사용하는 Last-Modified Tag 또는 E-Tag를 이용해 캐싱을 구현합니다.
- 대량의 요청을 효율적으로 처리할 수 있습니다.

**4. Layered System (계층 구조)**

- Client는 REST API Server만 호출합니다.
- REST Server는 다중 계층으로 구성될 수 있습니다.
  - 보안, 로드 밸런싱, 암호화 등을 위한 계층을 추가하여 구조를 변경할 수 있습니다.
  - Proxy, Gateway와 같은 네트워크 기반의 중간매체를 사용할 수 있습니다.
  - 하지만 Client는 Server와 직접 통신하는지, 중간 서버와 통신하는지는 알 수 없습니다.

**5. Uniform Interface (인터페이스 일관성)**

- URI로 지정한 Resource에 대한 요청을 통일되고, 한정적으로 수행하는 아키텍처 스타일을 의미합니다.
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하며, Loosely Coupling(느슨한 결함) 형태를 갖습니다.
  - 즉, 특정 언어나 기술에 종속되지 않음

**6. Self-Descriptiveness (자체 표현)**

- 요청 메시지만 보고도 쉽게 이해할 수 있는 자체 표현 구조로 되어있습니다.

---

<br><br>

# REST의 장단점

- 장점
  - HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라를 구축할 필요가 없다.
  - HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있게 해준다.
  - HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
  - REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악할 수 있다.
  - 서버와 클라이언트 역할을 명확하게 분리
- 단점
  - 표준이 존재하지 않음
  - 사용할 수 있는 메소드가 4가지(HTTP Method) 뿐
  - 구형 브라우저에서 아직 제대로 지원해주지 못하는 부분이 존재
    - PUT, DELETE를 사용하지 못하는 점

<br><br>

references

---

[https://dev-coco.tistory.com/97](https://dev-coco.tistory.com/97)

[https://velog.io/@seokkitdo/Network-REST란-REST-API란-RESTful이란](https://velog.io/@seokkitdo/Network-REST%EB%9E%80-REST-API%EB%9E%80-RESTful%EC%9D%B4%EB%9E%80)
