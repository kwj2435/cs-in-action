#### Spring 이란?
Spring은 Java 언어 기반의 프레임 워크이다.  
Spring은 객체 지향 언어가 가진 강력한 특징을 살려내어, 좋은 객체 지향 애플리케이션을 개발할 수 있도록 도와준다.  

#### Spring이 좋은 객체 지향 애플리 케이션 개발을 도와주는 방법
객체 지향의 5원칙중 OCP(Open/Close Principle, 개방 폐쇄 원칙)과 DIP(Dependency Inversion Principle, 의존관계 역전 원칙)  
위 두가지 원칙은 객체지향의 다형성만을 가지고 해결되지 않는 부분이다.  
Spring은 위 두가지 원칙은 DI/IOC를 이용하여 해결하고 있다.

#### 프레임워크란?
개발자에게 개발에 필요한 설계와 라이브러리를 통해 전체 개발 결과물의 뼈대를 제공하는 역할

#### 라이브러리란?
특정 기능을 제공하기 위해 미리 만들어진 코드들의 집합

#### Spring MVC와 Spring Boot의 차이
Spring Boot는 Spring MVC가 가지고 있던 불편함을 해소하기 위해 나온 스프링 모듈이다.   
Spring MVC를 사용할 때 불편함은 다음과 같다.
1. 서버를 띄우기 위해 별도의 Tomcat이 필요하다.  
2. 디펜던시 간의 호환성 문제로 잦은 문제가 발생한다.  
3. XML 기반의 bean 관련 코드는 가독성을 떨어지게 한다.  
4. 주입된 디펜던시별 설정 작업이 번거롭다.

위와 같은 불편함을 해결하고자 Spring Boot는 다음과 같은 기능을 제공한다.
1. Boot 자체에 내장 Tomcat을 탑재하여 별도의 Tomcat 없이도 서버를 띄울 수 있다.
2. starter pack 을 제공하여 호환성에 맞는 디펜던시를 묶어서 제공한다.
3. yml, properties 기반의 디펜던시 설정과 Auto Configuration을 제공한다.

#### Servlet이란?
서블릿이란 동적 웹 페이지를 만들 때 사용 되는 자바 기반의 프로그래밍 기술이다.  (웹 서버 프로그래밍을 위한 사양을 갖춘 자바 규격)
서블릿은 웹 요청과 응답의 흐름을 간단한 메서드 호출만으로 체계적으로 다룰 수 있도록 제공해준다.
서블릿은 interface로 명시되어 있는데, 스프링에서는 DispatcherServlet이 해당 인터페이스를 구현하여 사용하고 있다.  
  
클라이언트가 웹 서버에 요청을 하면 웹 서버는 was에 위임한다. was는 각 요청에 해당하는 서블릿을 실행한후 수행하여 반환한다.

1. 클라이언트 요청
2. HttpRequest를 Servlet Container로 보냄
3. Servlet Container는 HttpServletRequest, HttpServletResponse 객체 생성
4. Web.xml이 어느 서블릿에 대해 요청한 것인지 탐색 (Spring의 경우 DispatcherServlet)
5. 해당하는 서블릿에서 service() 메소드 호출
6. doGet() 또는 doPost() 호출
7. 동적 페이지 생성 후 ServletResponse 객체에 응답 전송
8. HttpServletRequest, HttpServletResponse 객체 소멸

#### Servlet Container
- 서블릿을 관리하기 위해서는 서블릿 컨테이너가 필요하며, 서블릿 컨테이너는 서블릿 객체를 생성하고, 초기화하며 호출하고 종료하는 일련의 생명주기를 관리한다.  
이렇게 생성된 서블릿은 웹서버와의 통신을 위해 소켓을 생성하고, 특정 포트에 리스닝하고 스트림을 생성하는 등의 복잡한 일들을 처리한다.
또한 멀티스레드에 대한 지원과 관리를 담당한다.  

- 우리가 많이 사용하는 톰캣이 바로 Servlet Container 역할을 수행한다.  
Servlet Container는 들어온 요청에 대해 처리가 가능한 Servlet을 찾고 해당 요청을 서블릿과 매핑시켜주는데,  
Servlet Container가 여러 매핑 정보를 가진 여러 Servlet을 생성하고 관리할 수도 있지만,  
스프링의 경우 Servlet Container에 Dispatcher Servlet을 등록하여 둔후 요청들을 DispatcherServlet으로 보내어 해당 부분에서 처리하도록 하고있다.
[DispatcherServlet은 Servlet이다.]

#### Spring은 멀티스레드 환경이니 스레드별로 DispatcherServlet이 생성되는건가?  
DispatcherServlet은 하나의 인스턴스가 생성되고, 애플리케이션 라이프 사이클동안 유지된다.  
이렇게 생성된 DispatcherServlet은 멀티 스레드환경에서 공유 자원으로 사용된다.  

#### Spring과 Tomcat의 관계
Tomcat은 WAS의 대표적인 미들웨어 서비스이다.  
[미들웨어는 서로 다른 애플리케이션이 서로 통신 하는데 사용되는 소프트웨어]  
톰캣은 일반적으로 아파치 톰캣으로 불리며 웹서버의 기능과 웹 애플리케이션 서버 기능 모두를 포함하고 있다.  
톰캣의 웹서버에서는 HTML,CSS,JS와 같은 정적 웹페이지 처리를 하고 동적 웹 처리는 Servlet Container로 전달하고 있다.  
톰캣의 웹서버는 사용자의 Http 요청 일련의 과정을 진행하며, 통신을 위해 소켓 연결등 네트워크 처리를 함께 진행한다.  
톰캣은 단일 프로세스로 동작하여 요청 처리를 스레드로 할당한다. 내부에는 스레드풀을 가지고 있다.

정리하자면, 클라이언트의 요청을 웹서버가 처음 마주하고 필요에따라 was로 해당 요청을 전달한다.
요청을 받은 Servlet Container는 요청을 처리하기 위해 적절한 Servlet을 찾는데 이때 DispatcherServlet으로 요청을 전달한다.
Servlet을 전달받은 DispatcherServlet은 어떤 컨트롤러를 호출할지 결정및 결과 반환을 진행한다.  

DispatcherServlet은 서블릿 컨테이너에서 동작하는 Spring Framework의 일부로서, 클라이언트의 요청을 서블릿을 통해 처리한다.
[Tomcat은 WAS이며 동적 웹 애플리케이션을 관리하는 역할을 한다. Spring은 WAS 위에서 동작하는 웹 애플리케이션 서버이다.]

#### Tomcat에 대한 심화 이해
Tomcat은 4.x 버전 부터 Catalina(Servlet Container), Coyote(HTTP 커넥터) 및 Jasper(JSP)엔진과 함께 출시되었다.  
아파치 톰캣이 웹서버와 was의 기능을 한다고 표현할때, was는 곧 servlet container를 의미한다.  
Servlet Container는 말그대로 Servlet을 담아두는 컨테이너 역할을 하며, 들어온 요청에 따라 정의된 서블릿과 매핑시켜준다.  
Servlet Container는 들어온 Http 요청에 대해 HttpRequest, HttpResponse 객체를 만들게 되는데,
HttpServletRequest는 Http 요청 정보를 편리하게 사용할 수 있도록 도와주는 객체로, 클라이언트가 보내는 HTTP 요청 메시지를 parsing하여, 그 내용물을 담고 있다.    
HttpServletResponse는 Http 요청에 대한 응답 메시지를 정의하며 응답메시지를 정의하는게 있어 필요한 편의기능을 제공한다.  
이렇게 생성된 두 객체는 Servlet Container가 Servlet을 호출할때 파라미터로 전달하여 사용되게 된다.  

ServletContainer로 사용할 수 있는 건 Tomcat외에도 Jetty, Undertow, Netty가 있다.

#### DispatcherServlet
DispatcherServlet은 Java EE의 Servlet을 래핑한 클래스이다.  (Spring에서 사용하는 서블릿 구현체)
Servlet Container로 부터 전달받은 Request를 올바른 Controller에 매핑하는 것부터, View, Model 처리등을 지원해준다.  
DispatcherServlet이 등장하기전에는 web.xml을 통해 모든 서블릿을 URL 매핑을 위해 web.xml에 등록해두어야 했지만,  
dispatcherServlet이 해당 애플리케이션으로 들어오는 모든 요청을 핸들링하는 편한 방식으로 바뀌게 되었다.  

DispatcherServlet의 역할  
1. ViewResolver를 통한 View 전달
2. 클라이언트로 부터 들어온 요청을 적절한 핸들러(컨트롤러)로 분배
3. 요청을 처리하기전 필터 처리
4. Spring Security와 통합하여 보안 및 인증 처리
5. 다국어및 국제화 관련 작업 지원 

#### DispatcherServlet과 FrontController의 관계
DispatcherServlet은 Spring MVC에서 FrontController 패턴의 구현체이다.  
Front Controller 패턴은 웹 애플리케이션의 모든 클라이언트 요청을 중앙 집중적으로 처리하는 디자인 패턴이다.  
Dispatcher Servlet은 클라이언트의 모든 HTTP 요청을 전달 받으며 요청을 분석하고 적절한 핸들러에게 요청을 전달한다.  
요청을 전달 받은 핸들러는 요청을 처리하고 결과를 Dispatcher Servlet에 반환한다.  
결과적으로 Dispatcher Servlet은 Front Controller 패턴을 구현하여 애플리케이션의 중앙 집중적인 요청을 담당하고,  
개발자는 컨트롤러와 뷰로직에 집중하여 웹 애플리케이션을 개발할 수 있게 된다.  
이것이 Dispatcher Servlet과 Front Controller 패턴의 관계이다.  

#### 클라이언트의 요청부터 Spring Controller에 도달하기 까지의 과정
1. Client -> Web Server(톰캣)로 Request 보냄
2. Apache(웹서버)은 (Tomcat)was로 요청 전달
3. Servlet Container(was)는 Request에 대한 HttpServletReuqest,HttpServletResponse 두 객체를 생성한다.
4. 요청한 URL에 해당하는 Servlet을 찾고, 없을 경우 Servlet을 생성한다.(DispatcherServlet은 옵션에 따라 미리 생성할수도, 나중에 생성할수도 있다.)  
5. DispatcherServlet에서 HandlerMapping 과정을 통해 해당하는 Controller로 요청을 전달한다.

#### 톰캣의 스레드풀


