#### Bean이란?
Spring에 의해 생성되고 Spring Container에 의해 관리되는 객체  
이렇게 생성된 Bean은 필요로 하는곳에 주입된다.  

#### Spring Container, IOC Container 란
Spring Container와 IOC Container는 동일한 의미이다.  
Spring은 객체지향적인 개발을 위해 IOC와 DI 개념을 사용하고 있는데, Spring에 의해 생성된 Bean 객체를 담아두고 관리하는 곳을 가르켜  
Spring Container 혹은 IOC Container라 부른다.  

#### Bean Factory와 Application Context
Spring Container에는 두 가지 구현체가 있다.  
Bean Factory는 스프링 컨테이너의 가장 기본적인 형태로 빈 객체의 생성, 초기화, 관리, 소멸등의 기능을 제공한다.  
Application Context는 BeanFactory를 상속하여 확장한 것으로 Bean Factory에서 제공하는 기능외 부가적인 기능을 제공한다.  
Application Context는 메시지 처리, 이벤트 발행, AOP 지원, 국제화와 로컬화, 환경 설정 관리등의 기능을 추가로 제공한다.

#### Spring Bean의 싱글톤과 Java 싱글톤의 차이점
스프링 빈은 기본적으로 싱글톤으로 생성되어 관리된다.  
다만 스프링에서 빈을 생성할때 사용되는 싱글톤은 일반적인 싱글톤과 차이가 있다.  

#### Spring Bean 기본 Scope와 다른 Scope

#### 하나의 Spring 애플리케이션이 여러 개의 Application Context를 가질 수 있을까?

#### Spring Bean의 생명 주기

#### Spring Bean은 스레드 세이프 한가? 그 이유는?