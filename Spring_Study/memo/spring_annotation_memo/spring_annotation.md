# 어노테이션(Annotation)

----------------------------------------------------

## 1. 어노테이션 ?
- 사전적으로 "주석" 이라는 의미를 가지고 있다. 
- 자바 코드에서 @를 이용해 주석처럼 달면, 특수한 의미,
기능을 부여해준다.
- 프로그램 코드의 일부가 아닌 프로그램에 관한 데이터를 제공,
코드에 정보를 추가하는 정형화된 방법이다.

## 2. DI, IOC 에 관한 어노테이션

---------------------------------------------------------------------------

### 1. @Configuration

   - 설정파일을 만들기 위한 어노테이션
   - Bean 을 등록하기 위한 어노테이션


### 2. @Bean

   - 스프링 IOC 컨테이너가 관리하는 자바 객체
   - 일반적으로는 컴포넌트 스캔을 사용해 자동으로 빈을 등록하지만, 수동으로 빈을 등록해야 하는 경우 사용한다


### 3. @Component

  - 개발자가 직접 작성한 Class를 Bean 으로 등록하기 위한 어노테이션
  - @ComponentScan 선언에 의해 특정 패키지 안의 클래스 들을 자동 스캔하여 그 범위 안에 있는 클래스들에 빈 인스턴스를 생성한다.
  - Controller, Service, DAO 세가지 이외의 클래스에만 사용을 권장

### 4. @Service

  - 비지니스 로직이 들어가는 Service로 사용되는 클래스 임을 명시하는 어노테이션

### 5. @Repository

  - DB연동 작업을 하는 클래스인 DAO에 특화된 어노테이션
  - 해당 클래스에서 발생하는 DB 관련 예외를 spring의 DAOException으로 전환할 수 있는 장점이 있다.

### 6. @Controller

  - Spring MVC의 Controller로 사용되는 클래스 선언을 단순화 시켜주는 어노테이션

### 7. @ControllerAdvice

  - 예외처리, 바인딩 설정, 모델 객체를 모든 컨트롤러 전반에 걸쳐 적용하고 싶은 경우에 사용한다.
  - 예외를 처리하는 @ExceptionHandler와 함께 사용하면 전반에 걸친 예외처리가 가능
  - 바인딩 또는 검증을 설정할 수 있는 @initBinder와 함께 사용하면 전반에 걸친 바인딩 설정 가능
  - 모델 정보를 초기에 초기화 할 수 있는 @ModelAttribute와 함께 사용하면 전반에 거린 모델 정보 설정이 가능

### 8. @RestController

  - REST API를 제공하는 컨트롤러를 위한 어노테이션, 해당 클래스에서 URL 매핑된 메서드들은 리턴 값으로 String 을 반환한다.
  - @Controller에 @ResponseBody가 추가된것(Controller에 @ResponseBody를 붙인것과 완벽히 동일하다)
  - Json 형태로 객체 데이터를 반환한다

### 9. @RestControllerAdvice

  - @ControllerAdvice 와 @ResponseBody 를 합쳐놓은 어노테이션
  - @ControllerAdvice 와 동일한 역할을 수행하고, @ResponseBody 를 통해 객체를 리턴 할 수 있다.
  - 단순히 예외를 처리하고싶다면 @ControllerAdvice, 응답으로 객체를 리턴해야한다면 @RestControllerAdvice를 적용하면 된다.

### 10. @Aspect

  - 스프링의 포인트컷과 어드바이스로 구성된 어드바이저의 생성을 편리하게 해주는 기능을 가진 어노테이션

### 11. @Autowired

  - 필요한 의존 객체의 "타입"에 해당하는 빈을 찾아 주입한다.
    - 적용위치 :

          - 변수
          - 생성자
          - setter
          - 일반 메서드

### 12. @ComponentScan

  - 클래스들을 순회하며 빈으로 등록될 객체들을 탐색후, 자동으로 등록한다
    - 범위

          - @Configuration
          - @Component
          - @Service
          - @Repository
          - @Controller
          - @RestController
          - @ControllerAdvice
          - @RestControllerAdvice
          - @Aspect ...

## 3. Lombok 에 관한 어노테이션

---------------------------------------------------------------------------

### 1. 생성자 관련

### 1-1. @AllArgsConstructor

- 모든 필드를 파라미터로 가지는 생성자를 생성한다

### 1-2. @NoArgsConstructor

- 파라미터가 없는 기본 생성자를 생성

### 1-3. @RequiredArgsConstructor

- final, @NonNull 인 필드값만 파라미터로 받는 생성자로 생성

### 2. 메서드 관련

### 2-1. @Getter

- Getter를 자동으로 생성

### 2-2. @Setter

- Setter를 자동으로 생성

### 2-3. @ToString

- toString 메서드를 자동으로 생성

### 2-4. @EqualsAndHashCode

- equals() 메서드와 hashCode() 메서드 자동으로 생성

### 3. 통합기능 관련 어노테이션

---------------------------------------------------------------------------

### 3-1. @Data

- @toString, @getter, @setter, @RequiredArgsConstructor 등을 모두 사용한 것과 같은 기능

### 3-2. @Value

- @Data 의 변형된 기능
- 모든 필드를 private final 로 설정, 클래스를 final로 설정, Setter를 생성하지 않는다.

### 4. 빌더 패턴

### 4-1. @Builder

- 메서드 체이닝을 이용하는 static 메서드 builder()를 생성한다.

### 4-2. @Builder.Default

- 명시적으로 기본값 설정
- 필드에 값을 설정하지 않은 경우 0/null/false 로 기본값이 설정된다, 이때 기본값을 지정하기 위해 사용

## 4. 요청, 응답에 관한 어노테이션

---------------------------------------------------------------------------

### 1. @ResponseBody

- @Controller 로 지정된 클래스 내에서 어떤 비즈니스 로직을 처리하는 메서드는 클라이언트에게 뷰가 아닌 데이터(JSON)를 전송하고 싶을때 사용한다

### 2. @RequestBody

- Http 요청 파라미터 형식이 아닌 HTTP BODY 형식의 데이터를 클라이언트에게서 받아서 처리해야 할 때 사용한다

### 3. @RequestMapping

- 어노테이션의 이름과 같이 요청(URL)을 컨트롤러의 메서드와 매핑할 때 사용한다(디폴트가 GET 방식)
- 메서드뿐만 아니라 클래스 레벨에서도 사용이 가능하다

### 4. @GetMapping, @PostMapping

- @RequestMapping 과 동일하나, HTTP 메서드를 따로 지정해줘야 했던 @RequestMapping과 다르게 원하는 메서드를 직접 사용할 수 있다
- get 메서드로 매핑, post 메서드로 매핑

### 5. @CookieValue

- 쿠키 값 또는 파라미터를 설정한다

### 6. @RequestParam

- HTTP 요청 파라미터를 쉽게 받을수 있는 어노테이션

### 7. @ModelAttribute

- 요청 파라미터의 값들을 통해 객체를 만들때 하나하나 파라미터 값을 불러오지 않아도 객체 생성을 자동화 할 수 있다


## 5. JPA에 관한 어노테이션

---------------------------------------------------------------------------

### 1. @Entity 

- 클래스를 엔티티로 선언


### 2. @Id 
- 테이블의 기본키에 사용할 속성을 지정


### 3. @Table(name="테이블명") 
- 엔티티와 매핑할 테이블을 지정


### 4. @GenerateValue 
- 키 값을 생성하는 전략 명시


### 5. @Lob 
- BLOB, CLOB 타입 매핑


### 6. @Enumerated
- @Enumerated(EnumType.STRING) -> 기본값은 (EnumType.ODINAL) 이지만, 보안상 문제로 쓰지않는다


### 7. @Transient 
- 엔티티 내부에서만 사용되는 항목 - 테이블 필드로 반영되지 않는다


### 8. @Temporal 
- 날짜와 시간 (과거에 사용했던 어노테이션)

### 9. @CreateDate 
- 엔티티가 생성되어 저장될 때 시간 자동 저장

### 10. @LastModifiedDate 
- 조회한 엔티티의 값을 변경할 때 시간 자동 저장

### 11. @CreationTimestamp 
- INSERT 쿼리시 자동으로 현재 날짜와 시간이 추가된다


### 12. @UpdateTimestamp 
- UPDATE 쿼리시 자동으로 현재 날짜와 시간이 수정

### 13. @Column

  - 속성

        - @column(nullable=true|false) - notnull 제약조건 부여

        - @column(Definition)
    
        - @Column(name="db의 필드명") - 엔티티의 필드명과 실 db의 테이블 필드명이 다를 때
    
        - @Column(unique="ture|false") - unique 제약조건 부여
    
        - @Column(length= ) - 기본값 = 255, 컬럼의 길이 설정
    
        - @Column(insertable=true|false) - 추가 불가
    
        - @Column(updatable=true|false) - 수정 불가
    
        - @MappedSuperclass : 공통적으로 사용하는 항목들(테이블을 직접 만들지 않는 항목) BaseEntity추상클래스를 만들어서 사용한다

### 14. 연관관계 매핑

- *연관관계의 주인
  - 테이블은 외래 키 하나로 두 테이블이 연관관계를 맺는다
  - 객체 양방향 관계는 A->B, B-> A처럼 참조가 2군데
  - 객체 양방향 관계는 참조가 2군데 있다. 둘중 테이블의 외래 키를 관리하는 곳을 지정해야 한다 A를 바꿀때 B도 바꿀지 / B를 바꿀때 A도 같이 바꿀지
  - 연관관계의 주인 : 외래 키를 관리하는 참조
  - 주인의 반대편 : 외래 키에 영향을 주지 않음

#### 14-1 @ManyToOne
- 다대일 (N : 1)
#### 14-2 @OneToMany
- 일대다 (1 : N)
#### 14-3 @OneToOne
- 일대일 (1 : 1)
#### 14-4 ManyToMany
- 다대다 (N : N)

### 15. 생성일자와 수정일자 자동 등록 Permalink
- 객체를 생성하거나 수정할 때 생성자와 Setter 에 LocalDateTime.now() 등 시간을 나타내는 객체를 넣어 생성일자와 수정일자를 관리할 수 있다.
- 하지만 여러 엔터티에서 이러한 코딩을 매번 하는 것은 단순하고 번거로운 작업이다.
- 그래서 인스턴스를 생성하거나 수정하는 변화가 있을 시에 이를 감지하여 자동으로 일시를 저장하도록 할 수 있다.

#### 15-1. @EntityListener

- 이벤트를 관찰하고 있다가, 이벤트가 발생하면 특정 동작을 진행한다.
- Entity리스너 이기 때문에 엔티티가 동작하는 몇가지 방법에 이벤트를 리스닝 하고 있다.

#### 15-2. @EnableJpaAuditing

- Configuration 어노테이션을 통해 JPA 에서 auditing 을 가능하게 한다.

#### 15-3. @CreateDate

- 인스턴스가 생성되는 것을 감지하여 감지된 일자를 저장한다.

#### 15-4. @LastModifiedDate

- 인스턴스가 수정되는 것을 감지하여 감지된 일자를 저장한다.

### 16. @IdClass

- 복합키 매핑을 하기 위해서 사용한다
  - DB를 설계하다 보면 Primary key 가 여러개가 되는 경우가 종종 있는데 ,PK에는 보통 @Id를 붙이는데, 무작정 붙이다 보면 오류가 발생한다.




## 6. 테스트에 관한 어노테이션

---------------------------------------------------------------------------

### * jUnit이란?

- Java에서 독립된 단위테스트(Unit Test)를 지원해주는 프레임워크이다.

### * 단위테스트(Unit Test)란?

- 소스코드의 특정 모듈이 의도된 대로 정확히 작동하는지 검증하는 절차이다.

- 모든 함수와 메소드에 대한 테스트 케이스(Test case)를 작성하는 절차를 말한다.

- jUnit은 보이지 않고 숨겨진 단위 테스트를 끌어내어 정형화시켜 단위테스트를 쉽게 해주는 테스트 지원 프레임워크이다.


### * jUnit 특징

- 단정(assert) 메서드로 테스트 케이스의 수행 결과를 판별한다.(ex: assertEquals(예상값, 실제값))

- jUnit4부터는 테스트를 지원하는 어노테이션을 제공한다.(@Test @Before @After)

- @Test 메서드가 호출할 때 마다 새로운 인스턴스를 생성하여 독립적인 테스트가 이루어지게 한다.

### ** jUnit 테스트에서 주로 사용하는 메서드

### 1. assertEquals(expected, actual)
- 실제 값(actual)이 기대하는 값(expected)과 같은지 검사한다.

### 2. assertNotEquals(unexpected, actual)
- 실제 값(actual)이 특정 값(unexpected)과 같지 않은지 검사한다.

### 3. assertSame (Object expected, Object actual)
- 두 객체가 동일한 객체인지 검사한다.

### 4. assertNotSame(Object unexpected, Object actual)
- 두 객체가 동일하지 않은 객체인지 검사한다.

### 5. assertTrue(boolean condition)
- 값이 true인지 검사한다.

### 6. assertFalse(boolean condition)
- 값이 false인지 검사한다.

### 7. assertNull(Object actual)
- 값이 null인지 검사한다.

### 8. assertNotNull(Object actual)
- 값이 null이 아닌지 검사한다.

### 9. fail()
- 테스트를 실패 처리한다.


### *** jUnit에서 테스트를 지원하는 어노테이션

### 1. @Test

- @Test가 선언된 메서드는 테스트를 수행하는 메소드가 된다.
- jUnit은 각각의 테스트가 서로 영향을 주지 않고 독립적으로 실행됨을 원칙으로 @Test마다 객체를 생성한다.

### 2. @Ignore

- @Ignore가 선언된 메서드는 테스트를 실행하지 않는다.

### 3. @Before

- @Before가 선언된 메서드는 @Test 메서드가 실행되기 전에 반드시 실행되어진다.
- @Test메서드에서 공통으로 사용하는 코드를 @Before 메서드에 선언하여 사용하면 된다.

### 4. @After

- @After가 선언된 메서드는 @Test 메소드가 실행된 후 실행된다.

### 5. @BeforeClass

- @BeforeClass 어노테이션은 @Test 메소드보다 먼저 한번만 수행되어야 할 경우에 사용하면 된다.

### 6. @AfterClass

- @AfterClass 어노테이션은 @Test 메소드 보다 나중에 한번만 수행되어야 할 경우에 사용하면 된다.

### 7. @AfterAll
- 현재 테스트 클래스의 모든 테스트 후에 @AfterAll이 달린 메서드가 실행되어야 함을 알리는 데 사용 된다.

### 8. @BeforeAll
- 한 클래스의 모든 테스트가 실행되기 전에 특정 작업을 수행해야 한다면 @BeforeAll 애노테이션을 사용한다.
- @BeforeAll 애노테이션은 정적 메서드에 붙이는데 이 메서드는 클래스의 모든 테스트 메서드를 실행하기 전에 한 번 실행된다.

### 9. @AfterEach
- 테스트를 실행한 후에 정리할 것이 있을 때 사용한다. 
- 테스트에서 사용한 임시 파일을 삭제해야 할 때 @AfterEach 애노테이션을 사용하면 된다.

### 10. @BeforeEach
- 테스트를 실행하는데 필요한 준비 작업을 할 때 사용한다.
- @BeforeEach 애노테이션을 이용해서 테스트에서 사용할 임시 파일을 생성한다거나 테스트 메서드에서 사용할 객체를 생성한다.

### 11. @DisplayName
- 자바는 메서드 이름에 공백이나 특수 문자를 사용할 수 없기 때문에 메서드 이름만으로 테스트 내용을 설명하기가 부족할 수 있기 때문에 @DisplayName 애노테이션을 사용해서 테스트에 이름을 붙일 수 있다.

### 12. @Disabled
- 특정 테스트를 사용하고 싶지 않을때 사용한다
- 아직 테스트 코드가 완성되지 않았거나 잠시 동안 테스트를 실행하지 말아야 할 때 이 애노테이션을 사용한다.

### 13. @Tag
- 테스트에 태그를 달 때 사용한다.
- 태그의 이름은 다음 규칙을 따라야 한다.

        - null이 공백이면 안 된다.
        - 좌우 공백을 제거한 뒤에 공백을 포함하면 안 된다.
        - ISO 제어 문자를 포함하면 안 된다.
        - 다음 글자를 포함하면 안된다. - ()&|!

### 14. @Nested
- 중첩 클래스에 테스트 메서드를 추가할 수 있다.
- 중첩된 클래스는 내부 클래스이므로 외부 클래스의 멤버에 접근할 수 있는데, 이 특징을 활용하면 상황별로 중첩 테스트 클래스를 분리해서 테스트 코드를 구성할 수 있다.

### 15. @TempDir
- 임시 폴더 관련 작업을 테스트 코드에서 쉽게 처리할 수 있다. 
- @TempDir 애노테이션을 필드 또는 라이프사이클 관련 메서드나 테스트 메서드의 파라미터로 사용하면 JUnit은 임시 폴더를 생성하고 @TempDir 애노테이션을 붙인 필드나 파라미터에 임시 폴더 경로를 전달한다.
- @TempDir 애노테이션은 File 타입이나 Path 타입에 적용할 수 있다.