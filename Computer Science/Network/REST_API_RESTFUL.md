# REST API , REST FUL

# REST API

```
REST의 원리를 따르는 API

최근 OpenAPI(누구나 사용할 수 있도록 공개된 API: 구글 맵, 공공 데이터 등),
마이크로 서비스(하나의 큰 애플리케이션을 여러 개의 작은 애플리케이션으로 쪼개어
 변경과 조합이 가능하도록 만든 아키텍처) 등을 제공하는 업체 대부분은 REST API를 제공한다

```

API(Application Programming Interface)란

- 데이터와 기능의 집합을 제공하여 컴퓨터 프로그램간 상호작용을 촉진하며,
  서로 정보를 교환가능 하도록 하는 것

<br>

## 특징

- 사내 시스템들도 REST 기반으로 시스템을 분산해 확장성과 재사용성을 높여 유지보수 및 운용을 편리하게 할 수 있다.
- REST는 HTTP 표준을 기반으로 구현하므로, HTTP를 지원하는 프로그램 언어로 클라이언트, 서버를 구현할 수 있다.
- 즉, REST API를 제작하면 델파이 클라이언트 뿐 아니라, 자바, C#, 웹 등을 이용해 클라이언트를 제작할 수 있다.

<br><br><br>

# \***\*REST API URI 설계 규칙\*\***

<br><br>

## 1️⃣**URI에 후행 슬래시(/ => 마지막에 붙이는 슬래시) 는 포함되지 않아야 합니다.**

혼란을 줄수 있고 의미가 없는 후행 슬래시를 URI 경로의 마지막에  포함시키지 않는 것은 따라야 할 규칙들 중 가장 중요한 것중 하나 입니다. REST API는 후행 슬래시를 가지지 않아야 하고 client들에게 제공하는 링크에 후행 슬래시는 포함되지 않아야 합니다.

```
많은 웹 component들과 framework들은 아래 두개의 URI를 같게 인식합니다 :

**http://api.canvas.com/shapes/**

**http://api.canvas.com/shapes**

그러나 URI의 모든 글자들은 resource들의 고유한 구별자로 계산됩니다.
```

두개의 다른 URI는 두개의 다른 resource들을 가리킵니다. 만약 URI가 다르다면 resource들도 다른것입니다, 그 반대또한 마찬가지 구요. 그러므로 REST API는 깨끗한 URI를 생성하고 소통해야 하며 resource를 모호하게 식별하려는 client의 시도를 허용하지 않아야 합니다.

더 너그러운 API 들은 후행 슬래시 없이 client들을 URI로 리다이렉트 시킬 것입니다.(301을 반환할수도 있다 -"영원히 이동" 자원들을 재위치 시키기 위해 사용되어지곤 한다.)

<br>

## 2️⃣**슬래시(/)는 계층관계를 나타내는데 사용해야 합니다.**

슬래시(/) 문자는 URI의 경로 부분에서 resource들 간의 계층 관계를 나타내는데 사용됩니다.

```
For example: **[http://api.canvas.com/shapes/polygons/quadrilaterals/squares](http://api.canvas.com/shapes/polygons/quadrilaterals/squares)**
```

<br><br>

## 3️⃣**URI의 가독성을 위해 하이픈(-)을 사용해야 합니다.**

URI를 사람에게 쉽게 인식되고 해석되게 하고, 긴 경로 요소 이름의 가독성을 증가 시키기 위해 하이픈(-)을 사용하세요. 영어로 공백이나 하이픈을 사용할 경우 URI에 하이픈을 사용해야 합니다.

```
For example: **[http://api.example.com/blogs/guy-levin/posts/this-is-my-first-post](http://api.example.com/blogs/guy-levin/posts/this-is-my-first-post)**
```

<br><br>

## 4️⃣**URI에서 언더바(\_)는 사용하지 않아야 합니다.**

텍스트 viewer 어플리케이션들(브라우저, 에디터, 등등)은 종종 URI에 클릭할수 있다는 시각적 힌트를 주기위해 밑줄을 사용합니다.

어플리케이션의 폰트에 따라 언더바(\_) 문자는 밑줄로 인해 부분적으로 보이지 않거나 완전히 가려질 수 있습니다.

이러한 혼란을 피하기 위해 언더바(\_) 대신 하이픈(-)을 사용하세요

<br><br>

## 5️⃣**URI 경로에서는 소문자를 선호합니다.**

대문자가 문제를 일으킬 수 있으므로 URI 경로에서는 소문자를 선호하는 것이 편리합니다.

RFC 3986은 URI를 scheme 혹은 host component를 제외하고 대소문자를 구분하는 것으로 정의하였습니다.

```
For example:

1) **http://api.example.com/my-folder/my-doc**

2) **[HTTP://API.EXAMPLE.COM/my-folder/my-doc](http://api.example.com/my-folder/my-doc)**

위의 uri는 괜찮습니다. RFC 3986에서는 1번 URI와 같은 것으로 인식합니다.

3) **http://api.example.com/My-Folder/my-doc**

이 URI는 1번, 2번과 같지 않습니다. 불필요한 혼란을 가져올 수 있습니다.
```

<br><br>

## 6️⃣**URI에 파일 확장자는 포함되지 않아야 합니다.**

웹상에서 마침표(.) 문자는 URI에서 파일의 이름과 확장자를 구분하는데 흔히 사용됩니다. REST API는 메시지들의 객체 body를 나타내는 위해 URI에 임의의 파일 확장자를 포함하지 않아야 합니다. 대신 body의 내용이 어떻게 흐르는지 결정하는 Content-Type header를 통해 전달되는 media-type에 의존하여야 합니다.

```
**http://api.college.com/students/3248234/courses/2005/fall.json**

**http://api.college.com/students/3248234/courses/2005/fall**
```

파일 확장자는 format 선호를 나타내기위해 사용되면 안됩니다.

REST API client들은 HTTP가 제공하는 형식 선택 메커니즘인 Accpet request 헤더를 사용하도록 해야 합니다.

간단한 link들과 쉬운 디버깅을 가능하게 하기 위해 REST API는 query parameter를 통해 미디어 타입 선택을 지원할수 있습니다.

<br><br>

## 7️⃣**마지막 부분은 단수 또는 복수형이여야 할까요? (복수형을 사용하라)**

간단하게 유지하라는 규칙은 이곳에도 적용됩니다. 비록 각자 내재화된 문법규칙이 single instance나 resource를 나타내기 위해 복수형을 사용하는 것이 틀렸다고 할지라도 프로그래밍적 정답은 URI 형식에서 항상 복수형을 사용하라는 것입니다.

불규칙 복수형(person/people, goose/geese)들은 다루지 않는것이 API 사용자들의 생활을 더 좋고 API 제공자들이 더 쉽게 수행할수 있도록 만들어 줍니다.(대부분의 현대 프레임워크들은 /students와 /students/3248234를 같은 컨트롤러에서 다룹니다.)

그런데 관계들은 어떻게 다루어야 할까요? 관계가 다른 자원 내에서만 존재할 수 있는 경우 RESTful 원칙은 유용한 원칙을 제공합니다.

예시를 한번 살펴볼게요. 한 학생이 복수개의 과목을 가지고 있습니다. 이 과목들은 /studensts의 끝 부분에 위치하게 됩니다.

```
**[http://api.college.com/students/3248234/courses](http://api.college.com/students/3248234/courses)**
id 3248234를 가진 학생이 배운 모든 과목들을 반환합니다.

**[http://api.college.com/students/3248234/courses/physics](http://api.college.com/students/3248234/courses/physics)** 
 id 3248234를 가진 학생이 배운 물리학 과목들을 반환합니다.
```

<br><br>

## ❗[Conclusion](https://dkrnfls.tistory.com/218#Conclusion) ❗

REST API 서비스를 설계할때 URI에 나타내어지는 resource들에 집중을 해야합니다.

서비스 내의 각각의 resource들은 하나 이상의 URI 식별자를 가지게 될것입니다. URI가 이해하기 쉽고 적절히 resource를 나타내는 것이 가장 좋습니다. URI는 예측가능해야 하며 이해력을 높이기 위해 계층구조를 사용해야 하고 사용성은 데이터가 구조 관계를 가지고 있다는 점에서 일관되고 계층적이라는 점에서 예측 가능해야 합니다.

RESTful API들은 사용자를 위해 작성되어져야 합니다. URI의 이름과 구조는 사용자들에게 의미를 전달해야 합니다. 위의 규칙들을 따름으로써 client를 좀 더 행복하게 하는 훨씬 깔끔한 REST API들을 만들수 있을 것입니다. 이것은 규칙이나 제약조건이 나니지만 API를 향상 시킬 것입니다.

---

<br><br>

# RESTful의 개념

### RESTful이란

- RESTful은 일반적으로 REST라는 아키텍쳐를 구현하는 웹 서비스를 나타내기 위해 사용되는 용어이다.
  - REST API를 제공하는 웹 서비스를 RESTful하다고 할 수 있다.
- RESTful은 REST를 REST 답게 쓰기 위한 방법으로, 누군가가 공식적으로 발표한 것이 아니다.
  - 즉, REST 원리를 잘 따르는 시스템은 RESTful 용어로 지칭된다.

### RESTful의 목적

- 이해하기 쉽고 사용하기 쉬운 REST API를 만드는 것
- RESTful한 API를 구현하는 근본적인 목적이 성능 향상에 있는 것이 아니라 일관적인 컨벤션을 통한 API의 이해도 및 호환성을 높이는 것이 주 동기이니, 성능이 중요한 상황에서는 굳이 RESTful한 API를 구현할 필요는 없다.

### RESTful하지 못한 경우

- CRUD 기능을 모두 POST 로만 처리하는 API
- route에 resource, id 외의 정보가 들어가는 경우

<br><br>

---

references

[https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)

[https://dkrnfls.tistory.com/218](https://dkrnfls.tistory.com/218)
