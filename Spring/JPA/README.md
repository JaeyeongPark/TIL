# JPA

## JPA란?
* 자바 진영의 ORM 기술 표준으로 , 인터페이스의 모음이다.
* JPA 실제구현체로 Hibernate, EclipseLink, DataNuclues가 있다.
* Hibernate가 사실상 표준이다.

## ORM 
* 데이터베이스 객체를 자바 객체로 매핑하여 객체 간의 관계를 바탕을 SQL을 자동으로 생성

## JPA를 사용해야하는 이유
* JPA를 사용하면 interface 선언만으로도 쿼리 구현이 가능해져서 생산성이 올라간다.
* 칼럼 추가/삭제 시 직접 관련된 CRUD 쿼리를 모두 수정하는 대신 JPA가 관리하는 모델(Entity)을  수정하면 된다.
* 데이터베이스 벤더마다 미묘하게 다른 데이터 타입이나 SQL을 JPA를 이용하면 손쉽게 해결할 수 있다.
* JPA는 객체와 관계형 데이터베이스 사이의 패러다임의 불일치로 발생하는 문제를 해결한다.

## Entiy 클래스 annotation 
* @Entity
  * 테이블과 링크될 클래스임을 나타낸다.
  * 기본값으로 클래스의 카멜케이스를 바탕으로 테이블 이름을 매핑한다.
  * ex) SalesManager.java -> sales_manager table
* @GeneratedValue
  * PK생성 규칙
  * 스프링 부트 2.0에서는 GenerationType.IDENTITY옵션을 추가해야 auto_increment가 된다.
* @Id
  * 해당 테이블의 PK필드를 나타낸다.
* @Column
  * 테이블의 컬럼을 나타내며 굳이 선언하지 않더라도 해당 클래스의 필드는 모두 컬럼이 된다.
  * 사용하는 이유는 기본값 외에 추가로 변경이 필요한 옵션 있으면 사용한다.
* @Builder
  * 해당 클래스의 빌더 패턴 클래스를 생성
  * 생성자 상단에 선언 시 생성자에 포함된 필드만 빌더에 포함



## CrudRepository 인터페이스
```java
public interface CrudRepository<T, ID> extends Repository<T, ID> {

  <S extends T> S save(S entity);       // 1   

  Optional<T> findById(ID primaryKey);  // 2

  Iterable<T> findAll();                // 3         

  long count();                         // 4                     

  void delete(T entity);                // 5      

  boolean existsById(ID primaryKey);    // 6      

  // … more functionality omitted.
}
```
1. 주어진 엔티티를 저장
2. 지정된 ID로 식변되는 엔티티를 반환
3. 모든 엔티티를 반환
4. 엔티티 수를 반환
5. 지정된 엔티티를 삭제
6. 주어진 ID를 가진 엔티티가 있는지 여부를 나타냅니다.


## 쿼리 방법
1. 인터페이스에서 쿼리 메서드를 선언한다.
```java
interface PersonRepository extends Repository<Person, Long> {
  List<Person> findByLastname(String lastname);
}
```
2. JavaConfig 또는 XML구성을 사용하여 해당 인터페이스에 대한 프록시 인스턴스를 생성
* Java설정은 다음과 유사한 클래스를 생성한다.
```java
interface PersonRepository extends Repository<Person, Long> {
  List<Person> findByLastname(String lastname);
}
```
* XML설정은 다음과 유사한 Bean을 정의한다.
```java
interface PersonRepository extends Repository<Person, Long> {
  List<Person> findByLastname(String lastname);
}
```
3. 다음 예와 같이 레포지토리 인스턴스를 주입하고 사용한다.
```java
class SomeClient {

  private final PersonRepository repository;

  SomeClient(PersonRepository repository) {
    this.repository = repository;
  }

  void doSomething() {
    List<Person> persons = repository.findByLastname("Matthews");
  }
}
```


