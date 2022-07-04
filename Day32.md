**Day32**

- 2022-05-26
- Server: Day01

---

# 주제

- 서버 구축 초기 단계 방법부터 발전된 방법까지 차례차례 경험하며 **서버를 구축**한다.

- **사용 환경**:
  - IDE: Eclipse
  - lang: Java
  - framework: Spring
  - library: External JREs or Maven


<br>

---

# 개요



<br>

---

# 서버구축

- 3개의 레이어로 서버를 구성하려고 한다.

<br>

## 서버구성: 3개의 Java 클래스

- **Java Controller**
  - 브라우저에서 요청을 하면 새로운 html 화면을 만들어서 보내주는 역할.

  - From AJAX: 브라우저에 데이터 요청을 받아서 JSON의 형태로 데이터를 보내준다.
    - 지도
    - 그래프

  - From DAO: DAO로 부터 결과를 받아서 html 화면을 만들고 그 화면을 브라우저에 보내준다.

- **Service**
  - JC에서 register(data insertion) 요청을 받고 DAO에게 보내주는 역할. (즉, 두 클래스의 징검다리 또는 사이의 필터.)
  - Service의 존재 이유
    - Service가 없으면 두 개의 자바 클래스 JC와 DAO가 붙어있게 되고 둘 중 하나라도 잘못되면 둘 다에 문제가 생길 수 있다.
  - 하지만 이러면 안된다 왜냐면 DAO는 DB랑 밀접한 관계를 가지고 있기 때문에 DAO에 문제가 생기면 DB도 문제가 생기기 때문.
  - 메인터넌스를 할 때도 DB에는 영향을 주지 않기 위해 Service를 넣어서 완충효과를 본다.
  
- **DAO (Data Access Object)** : 요청을 받으면 CRUD가 일어나고 그 결과를 Java Controller로 보낸다.
  - JDBC Connection 관리
    - JDBC Connection 중 발생할 수 있는 에러 관리

  - **VO** : 데이터를 담아서 왔다갔다하면서 전달해주는 역할.




- 장점:
  - 분리되어 있어서 서로에게 영향을 끼치지 않고 각각의 수정이 쉽다.

- 단점 : 
  - 클래스가 많아진다.
  - 모든 클래스가 다 엮여진다. 하나 문제가 생기면 다 연쇄적으로 문제가 일어난다 -> 객체지향의 단점
    - 이것을 완화시키기 위해서 **Spring**이 나왔다. -> 이제 이 클래스들은 레고블럭처럼 동작을 한다. How?
    - ==> 각각의 클래스들은 container에 붙여서 쓴다. => Spring Container
    - 브라우저에서 Spring에게 요청을 한다. 그럼 Spring Container통해 Spring이 알아서 해당 클래스를 사용하게 한다. - 기존 자바의 방식과 거꾸로
    - => ex) JC가 Service가 필요할 때 그냥 너 쓸게 하고 썼는데
    - 이제는 Spring Container가 그래? 하고 Service를 만들어서 JC에게 준다.
    - 그래서 각각의 클래스들을 Contrainer에서 꼈다 뺐다하면서 쓰이는 것. -> 독립적
    - 여기 관련 서비스 사례: 전자 정부 서비스 ->10여년동안 대대적으로 모든 시스템들을 Spring으로 바꾼 것.

---

---



- 오늘 배우는 것:
- JC에서 텍스트를 이용해서 VO 생성
- Service로 VO를 보냄
- DAO로 VO를 보냄
- DAO가 VO의 데이터를 DB에 넣음



- 각각의 클래스를 코딩하는 것은 쉽지만

- 이러한 환경을 구축하는 게 제일 어렵다.
  - --> Spring Boot - 환경 세팅을 버튼으로 띡띡띡하면 환경이 만들어진다. 거기서 html과 클래스만 만들면 되는 것.
  - 요즘: Spring Boot 쉬움 -> 커리어 쌓음 -> Spring으로 넘어가서 더 복잡한 환경에서 시작.



- 코스: 자바 클래스들만 -> Spring container 붙이기 -> Spring 서버 붙이기 -> DB 연결하기 -> 웹 클라이언트 붙이기

----

## 준비하기

- 네이버 카페에서 다운  받아놓기

  - Spring lab & library

  - Spring Maven
- Eclipse

  - spring workspace 만들기
  - file > switch workspace > 새로만들기 (spring)
  - 폰트 키우기
  - Create Java Project - day01
    - JRE 1.8 버전으로 설정
- StarUML - day32
  - day32-2
    - interface를 통해서 시스템관의 관계를 융통성 있게 만들어줄 거임 (점선 관계)
    - interface의 format display를 texture로 바꾸기
    - dependency로 Controller -> service -> Dao 연결
    - realization으로 userServie, UserDao를 각각의 인터 페이스와 연결




- uml- day32-2에 맞게 eclipse에서 클래스 생성
- 대규모 프로그램을 만들 때 인터페이스를 사용할 때
  - 단점: 아직까지도 클래스와의 관계가 타이트하게 묶여있는 것은 어쩔 수 없다.
  - -> 자바만 가지고는 클래스와 클래스의 관계를 루즈 커플링으로 만든다는 것은 어렵다.
  - => Spring

---



## Spring

- 환경설정

  - 자바 프로젝트 생성 day011

    -  생성 시 configure에서 자바 버전 바꿔주기 -> 새 workspace 때마다
    - configure > Installed JREs > 원래 있던 거 삭제
    - add > 원래 있던 jre edit > Directory를 우리 jre로 바꿈
  - 스프링 라이브러리 add
    - 네이버 카페에서 받은 spring_lib를 압축해제 후 해당 폴더를 c: > spring에다가 넣자.
      - 외부 라이브러리를 이렇게 많이 쓰면 시스템 운영 쉽지 않음
      - --> 그래서 Maven
      - 미국 어디의 한 서버에 모든 라이브러리를 다운해 놓고 필요할 때마다 가져다 씀 - 중앙집중화
      - 우리는 지금은 maven을 쓰지 않겠다.
    - build path > library > add External JARs... 에 spring_lib 폴더 안의 모든 JREs를 선택해 넣자. -> Referenced Library에서 확인가능. (or 프로젝트 생성시)
  - spring.lab > d11 > src > It.xml 복사해서 day011 src에 넣기 -> spring.xml로 이름 바꿔주기
    - spring.xml: 나 지금 spring 환경으로 시작할 거야라는 말.
  - 프로젝트 우클릭 > spring > add spring nature (sts를 설치 했기 때문에 나오는 메뉴)
    - 콘솔 위에 src, namespace, overview,beans 섹션이 뜸
  

---

day011

- Uml - day32-3

- Controller 가 Spring Container에게 STV를 달라고 해서 사용할 것이다.

- spring.xml에서 이 부분 바꾸기

  - ```
    <bean id="lg" class="bean.LTV"/>
    <bean id="ss" class="bean.STV"/>
    ```

- spring_lab > d11 > src > app > App.java

  - Controller로 복붙



교과서: 자바를 이용한 웹개발 기술 - 자바 기반으로 웹 만드는 방법

- 기본: Java, SQL, HTML5
- 초기: Sublet, jsp (or thymleaf, react, vue, spring boot (이후))
-  중기: spring 나오면서 framwork 기반 - 많은 양의 코딩을 framework가 해주고 우리는 조금만 코딩 - 단, 환경설정 개같다
- 현재: spring boot
- 그냥 자바 -> 인터페이스 -> spring

---



- 교과서 p761: Spring Framework

  - model2
    - model1보단 개발이 쉽지만 비효율
    - 스트러쳐는 사라짐.
    - 프레임워크란.- Spring Container
      - 일정한 표준을 기준으로 개발이 이루어짐.
      - Spring 전에는 관세청 개발 첨부터 다 해놓고 또 통계청 개발을 처음부터 다 해야했음. 1만명 동원
      - Spring 이후, (2010년 전후) 적은 개발자가 비교적 쉽게 개발 가능.
      - 프레임워크 중 제일 많이 사용되는 것: Spring
    - 스프링프레임워크
      - 라이브러리 필요
  - p768
    - 자바와 같은 객체지향 언어에서 클래스의 역할
    - **의존성 주입**(di)과 **제어역행**(ioc)
    - 의존성 주입 (dependency injection) 이론을 실제적으로 구현한 게 제어역행(ioc
    - 예전: 클래스 간의 관계를 개발하면서 직접 코딩 (타이트 커플링)
    - 의존성 주입: Container가 연관관계를 직접 규정 -> 코드에서는 직접적인 연관관계 없어도 사용 가능(**루즈 커플링**) -> 좀 더 유연하게 유지 변경 가능해짐
    - 위의 환경을 제공해주는 것이 spring



- p783
  - 팩토리 = Spring Container
  - 더 이상 자바에서 객체를 만들지 않아도 연결가능 - 더 이상 타이트 커플링 ㄴㄴ



- p788
  - day012 프로젝트

---

- UML-day32-4
  - UserOracleDao 클래스 더하기
    - 위의 세팅으로 아무것도 바꿀 것없이 클래스를 넣고 빼고 가능하다. - 아주 편리

---

- day013 생성
  - 생성할 때 라이브러리 안 더해줌
  - spring
  - 프로젝트 우클릭 > confingure > Convert to Maven Project > Finish (maven library) - Gradle이라는 것도 있는데 이건 intellij에서 씀
    - pom.xml 생성됨.
    - 다운해놨던 pom.xml에서 필요부분을 생성된 pom.xml에 복붙
  - Spring.xml 복붙

---

- UserDao 만들기 - id가 String 타입이기 때문에 k는 String
- UserService 만들기
- spring.xml 에 적기
- test하기

---

ws (완료)

- ItemVO를 설계하시오.

- ItemVO 관련 CRUD를 위한

  - ItemService
  - ItemDao

  를 구현하고 각각의 기능을 구현하시오.

- 질문1: SellectAll method의 return type을 List로 쓰는 이유

  - 널널하게 만들기 위해서
  - List는 인터페이스이기 때문에 그냥 쓰진 못함. 하위 애들을 가져다 써야함.

- 질문2: 언제는 = null;이고 언제는 = new?

  - null 일때는 텅 빈 곳에 실체가 있는 애들을 넣을 때
  - new 일 때는 만들어서 하나하나 넣을 때.
  - --> 이미지 적으로 이해하라

---



- 해야할 것

  - 코멘트 정리 (완료)
    - 클래스 파일 default
      - username
    - method 자동완성 코멘트 (자동 부분)
  - uml 글씨 크기 키우기 (완료)
  - spring 폴더 git init (완료)
