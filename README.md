# spring_study
## 2023/05/29
### Log
- 스프링 주요 어노테이션 정리


## 2023/05/30
### Log
- JPA 주요 어노테이션 정리 추가

@Entity : 클래스를 엔티티로 선언

@Id : 테이블의 기본키에 사용할 속성을 지정

@Table(name="테이블명") : 엔티티와 매핑할 테이블을 지정

@GenerateValue : 키 값을 생성하는 전략 명시

@Lob : BLOB, CLOB 타입 매핑

@Enumerated(EnumType.STRING) -> 기본값은 (EnumType.ODINAL) 이지만, 보안상 문제로 쓰지않는다

@Transient : 엔티티 내부에서만 사용되는 항목 - 테이블 필드로 반영되지 않는다

@Temporal : 날짜와 시간 (과거에 사용했던 어노테이션)

@CreateDate : 엔티티가 생성되어 저장될 때 시간 자동 저장

@LastModifiedDate : 조회한 엔티티의 값을 변경할 때 시간 자동 저장

@CreationTimestamp : INSERT 쿼리시 자동으로 현재 날짜와 시간이 추가된다

@UpdateTimestamp : UPDATE 쿼리시 자동으로 현재 날짜와 시간이 수정

@Column

속성
@column(nullable=true|false) - notnull 제약조건 부여
@columnDefinition)
@Column(name="db의 필드명") - 엔티티의 필드명과 실 db의 테이블 필드명이 다를 때
@Column(unique="ture|false") - unique 제약조건 부여
@Column(length= ) - 기본값 = 255, 컬럼의 길이 설정
@Column(insertable=true|false) - 추가 불가
@Column(updatable=true|false) - 수정 불가
@MappedSuperclass : 공통적으로 사용하는 항목들(테이블을 직접 만들지 않는 항목) BaseEntity추상클래스를 만들어서 사용한다
