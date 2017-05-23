# Todo List
> 해당 과제는 웹상에서 할 일을 관리(추가, 삭제, 완료처리)하는 ToDoList 서비스를 구현하는 것이다. 이 과제에서 사용하는 Todo List는 [TodoMVC App Template](https://github.com/tastejs/todomvc-app-template)을 기반으로 설명되어 있다.

## TASK
1. **할 일 등록하기**
	- 할 일을 등록하는 input box가 있고, 커서를 두고 입력한 후 엔터 key를 치면 글이 등록된다.
	- 빈 문자이면 등록되지 않는다.
	- 새로 고침을 해도 같아야 한다.
2. **할 일 리스트**
	- 등록된 할 일 리스트를 보여준다.
	- 최신 할 일이 앞에 보여준다.
3. **할 일 완료하기**
	- 버튼을 클릭 시 이 일은 완료한 일로 상태가 변경되며, 리스트에서 위 그림과 같이 취소선이 그어진다.
	- css의 `completed` 클래스를 활용한다.
	- 새로 고침을 해도 같아야 한다.
5. **할 일 삭제하기**
	- 리스트에서 텍스트에 마우스 오버하면 위 그림과 같이 삭제하기 버튼이 보인다. 
	- 이 버튼을 클릭 시 이 글을 삭제되어 리스트에서 아예 보이지 않는다.
	- 새로 고침을 해도 같아야 한다.
6. **할 일 전체 갯수 표시**
	- 아직 완료하지 못한 할 일의 갯수를 보여준다.
7. **할 일 리스트를 필터링**
	- 기본은 ALL로 모든 할 일이 보인다.
	- Active클릭 시 아직 완료하지 못한 일이 보인다
	- Completed를 클릭 시 완료한 일이 보인다.
	- hash가 url에 표현되면 안된다.
8. **완료한 일 삭제**
	- 클릭 시 이미 완료한 일을 리스트에서 삭제한다.
	- 새로 고침을 해도 같아야 한다.

## 과제 제출
- 해당 저장소를 fork한다.
- 과제를 수행한 후 Pull request로 제출한다.


## 조건
### FE
- 라이브러리는 jQuery만 사용한다.
- 파일은 uglify하지 않는다.

### Server
- UI는 정적파일인 HTML과 JavaScript에만 맡긴다. 즉 JSP와 같은 서버사이드 렌더링을 사용하지 않는다.
- Java의 일반적인 코딩 컨벤션을 따른다.
	- 클래스명은 UpperCamelCase, 멤버 변수명,메서드명은 lowerCamelCase로 선언한다.
	- 상수 이름은 대문자로 쓰고 "_"로 구분한다.
	- 중괄호의 시작 위치, 들여쓰기 문자는 `TodoApplication.java`를 참조하여 맞춘다.
- `src/main/java` 아래에 있는 코드에는 `System.out.println()`이 남아있지 않아야한다.
- 과제의 기본틀에서 제공하는데로 Spring MVC + Spring Boot를 이용해서 구현한다.
- DB와 스키마는 어플리케이션이 실행되는 시점에 자동생성된다.
	- server 디렉토리에서 `./mvnw exec:java` 명령을 내리면 DB에 접속할 수 있다. DB접속 정보는 `server/src/main/resources/application.properties`를 참조한다.
- `TodoController`, `TodoService`, `TodoDao` 3개의 계층으로 어플리케이션을 구성한다.
	- 계층 간의 의존성은 생성자를 통해 주입한다.
- 1개 이상의 테스트 메서드를 담은 테스트 클래스 1개를 필수로 작성한다.

#### `TodoController`
- 패키지는 `kr.or.connect.todo.api`으로 선언한다.
- `/api/todos`의 경로에 REST 스타일로 API를 정의한다.
- `@RestController`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping` 애너테이션을 활용한다.

#### `TodoService`
- 패키지는 `kr.or.connect.todo.service`으로 선언한다.

#### `TodoDao`
- 패키지는 `kr.or.connect.todo.persistence`로 선언한다.
- Spring JDBC의 `SimpleJdbcInsert`, `NamedParameterJdbcTemplate`을 이용해서 구현한다.
- CRUD 동작을 실행하는 역할에만 충실하도록 구현한다.
- SQL구문은 `TodoSqls` 클래스에 상수로 선언한다.

## 참고
과제를 수행하는데 필요한 지식은 [사전 교육](http://www.edwith.org/boostcamp_web)을 통해 학습할 수 있다.

### 개발환경
- 서버 실행
	- 저장소를 clone 후 server 디렉토리를 IDE에서 import한다. TodoApplication의 main메서드를 실행한다.
		- Eclipse로 import하는 방법은 [사전 교육](http://www.edwith.org/boostcamp_web)의 `실습S01: Spring Boot 프로젝트 만들기`중 `5. IDE로 import` 절을 참조한다.
	- IDE에 의존하지 않고 서버를 실행하려면 server 디렉토리에서 `./mvnw spring-boot:run`을 입력한다.
- FE 개발
	- Eclipse 외의 편집기를 써도 무방한다.
	- Eclipse로 FE 코드를 import하려면 [사전 교육](http://www.edwith.org/boostcamp_web)의 '실습S02: 정적 파일 디렉토리 설정' 중 `2. index.html 추가` 부분을 참조한다.


### github
- [fork하여 PR을 보내는 방법](https://www.youtube.com/watch?v=ZSZoaG0PqLg)
- [PR보내고 다시 PR보낼때 확인](https://www.youtube.com/watch?v=CbLNbCUsh5c)
- [confilct날 때 해결하는 방법](https://www.youtube.com/watch?v=U3RmwYc5eGQ)

