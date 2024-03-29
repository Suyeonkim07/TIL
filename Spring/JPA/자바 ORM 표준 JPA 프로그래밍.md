# 자바 ORM 표준 JPA 프로그래밍
## JPA 소개  
- 자바 진영의 ORM 기술 표준
- 표준 명세 : 인터페이스 의 모음

<br>

### ORM :object-relational mapping
객체와 관계형 데이터베이스의 다리 역할을 해줌

<br>

### jpa를 사용해야하는 이유?
- 패러다임의 불일치 해결
- 생산성 (CRUD가 다 만들어져있음)
- 유지보수 

### jpa의 성능 최적화 기능
- 1차 캐시와 동일성 보장
    - 같은 트랜잭션 안에서는 같은 엔티티 반환
- 트랜잭션을 지원하는 쓰기지연 
    - 트랜잭션을 커밋할 때까지 insert 모았다가 한번에 전송
- 지연로딩
    - 연관된 것을 실제 사용할 때만 로딩 <br> 
    <-> 즉시로딩 : 연관된 객체까지 미리 조회

## Hello JPA - 애플리케이션 개발
### 강의 요약
1. jpa는 entityManagerFactory를 만들어야한다.
2. db요청이 필요하면 entityManager 이용해서 해야한다
3. 모든 변경은 트랜잭션에서 해야한다.
<br>
### JPQL
- 엔티티 객체 대상으로 하는 객제지향 쿼리
 <->
 - SQL : 데이터 베이스 테이블을 대상으로 쿼리

<br>

## 영속성 컨텍스트
- 엔티티를 영구 저장하는 환경
- db에 저장하는게 아니라 엔티티를 영속성 컨텍스트에 저장하는 것

생명주기 
- 비영속 : 객체를 생성 
- 영속 : 객체를 저장
- 준영속 : 영속성 컨텍스트에서 분리
    - jpa가 관리하지 않는 상태 
    - 영속성 컨텍스트의 제공 기능을 사용할 수 없음
- 삭제 : 객체를 삭제


이점
- 1차 캐시
- 동일성 보장
- 트랜잭션을 지원하는 쓰기지연
- 변경감지
- 지연로딩

### 1차캐시
- 값을 조회할 때 영속성 컨텍스트의 1차캐시에서 찾음
- 없을 때는 DB에서 조회
(한 트랙잭션안에서만 효과가 있음)

### 동일성 보장
- 1차 캐시가 있어서 가능하다
- 같은 트랜잭션안에서 비교시 true보장

### 트랜잭션을 지원하는 쓰기지연
- 트랜잭션을 커밋하는 순간 데이터베이스에  insert query

** jpa batch : db에 한번에 넣을 수 있는 기능 **

### 변경 감지
<매커니즘>
- 영속성 컨텍스트로 들어온 최초의 값을 스냅샷 찍는다
-  커밋하는 순간 엔티티와 비교 후 update
<br>

** flush : 영속성 컨텍스트의 변경내용을 데이터 베이스에 동기화

### 지연 로딩
- 실제로 사용할 때 조회한다.
<br>

## 엔티티 매핑

- @Entity : Jpa가 관리하는 객체(데이터베이스 테이블과 매핑 되어있음)
    - 기본 생성자 필수



