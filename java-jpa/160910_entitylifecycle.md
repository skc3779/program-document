### 엔티티 생명주기

엔티티 생명주기에는 4가지가 존재

* 비영속(new/transient) : 영속성 컨텍스트와 전혀 관계가 없는 상태
* 영속(managed) : 영속성 컨텍스트에 저장된 상태
* 준영속(detached) : 영속성 컨텍스트에 저장되었다가 분리된 상태
* 삭제(removed) : 삭제된 상태


#### 비영속(new/tranient)

엔티티 객체를 생성, 지금은 순수한 객체 상태이며 아직 저장하지않았다.
따라서 영속성 컨텍스트나 데이터베이스와는 전혀 관련이 없다. 이것을 비영속상태라 한다.

```java
Memeber member = new Member();
member.setUsername("멤버1");
```

#### 영속(managed)

엔티티 매니저를 엔티티를 연속성 컨텍스트에 저장했다. 이렇게 연속성 컨텍스트가 관리하는 상태를 연속상태라 한다.
em.find(), JPQL를 사용해서 조회한 엔티티도 영속성 컨텍스트가 관리하는 연속상태가 된다.

```java
//엔티티 매니저 팩토리 생성
EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpademo");
//엔티티 매니저 생성
EntityManager em = emf.createEntityManager();

//멤버객체
Memeber member = new Member();
member.setUsername("멤버1");
생략...

//연속상태
em.persist(member);

생략...
```

#### 준영속(detached)

연속성 컨텍스트가 관리하던 영속 상태의 엔티티를 엲속성 컨텍스트가 관리하지 않게되면 이를 준영속 상태가 된다. 이는
em.detach(), em.close(), em.clear(), 를 호출해서 영속성 컨텍스트를 분리, 종료, 초기화하면 연속성 컨텍스트가 관리하던 연속 상태의 엔티티는 준영속 상태가 된다.


### 삭제(removed)

엔티티를 연속성 컨텍스트와 데이터베이스에서 삭제.

```java
em.removed(member);
```

###  연속성 컨텍스트의 특징

1. 연속성 컨텍스트는 엔티티를 식별자 값(@Id)로 구분한다. 따라서 영속 상태는 식별자 값이 반듯이 있어야 한다.
2. 연속성 컨텍스트에 엔티티를 저장하면 이 엔티티는 데이터베이스에 저장 되는데 JPA는 보통 트랜잭션을 커밋하는 순간 영속성 컨텍스트에 새로 저장된 엔티티를 데이터베이스에 반영 한다 이것을 플러시(flush)라 한다.
3. 연속성 컨텍스트에 엔티티를 관리 시 장점.
    * 1차 캐시
    * 동일성 보장
    * 트랜잭션을 지원하는 쓰기 지원
    * 변경 감지
    * 지원 로딩


#### 1차 캐시

1차 캐시에 대한 설명은 ```160910_영속성컨텍스트_구조.pptx``` 참고

#### 동일성 보장

```java
Member a = em.find(Member.class, "member1");
Member b = em.find(Member.class, "member2");

if( a == b ) {
	System.out.println("동일성을 보장");
}

```

#### 트랜잭션을 지원하는 쓰기 지원

```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpademo");
EntityManager em = emf.createEntityManager();
EntityTransaction tr =  em.getTransaction();

// 트랜젝션 시작
tr.begin();

// 여기까지 내부적으로는 Insert sql을 데이터베이스에 보내즈는 않는다.
em.persist(memberA);
em.persist(memberB);
em.persist(memberC);

//커밋하는 순간 데이터베이스에 Insert sql을 보낸다.
tr.commit();

```

#### 변경 감지

```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpademo");
EntityManager em = emf.createEntityManager();
EntityTransaction tr =  em.getTransaction();

// 트랜젝션 시작
tr.begin();

// 영속 엔티티 조회
Member memberA = em.find(Memeber.class, "memberA");

// 영속 엔티티 데이터 수정
memberA.setUsername("Hong KilDong");
memberA.setAge(10);

// 커밋하는 순간 데이터베이스에 Insert sql을 보낸다.
tr.commit();

```

1. 트랜잭션을 커밋하면 엔티티 매니저 내부에서 먼저 플러시(flush)가 호출된다.
2. 엔티티와 스냅샷을 비교해서 변경된 엔티티를 찾는다.
3. 변경된 엔티티가 있으면 수정 쿼리를 생성해서 쓰기 지연 SQL 저장소에 보낸다.
4. 쓰기지연 저장소와 SQL을 데이터베이스에 보낸다.
5. 데이터베이스 트랜잭션을 커밋한다.

변경 감지는 영속성 컨텍스트가 관리하는 영속 상태의 엔티티만 적용된다. 비연속, 준연속 처럼 영속성 컨텍스트의 관리를 받지 못하는엔티티는 값을 변경해도 데이터베이스에 반영되지 않는다.


JPA의 기본 전략은 엔티티 변경 시 모든 필드 업데이트를 한다.

* 모든 필드를 사용하면 수정 쿼리가 항상 같다. 따라서 애플리케이션 로딩시 수정 쿼리를 미리 생성해두고 재사용이 가능하다.
* 데이터베이스에 동일한 쿼리를 보내면 데이터베이스는 이전에 한번 파싱된 쿼리를 재상용 할 수 있다.

그러나 상황에 따라 다르지만 컬럼이 대략 30개 이상되면 기본 전략보다는 @DynamicUpdate 를 사용한 동적 쿼리가 빠르다.


```java
@Entity
@org.hibernate.annotations.DynamicUpdate
@Table(name = "Member")
public class Member { ... }
```


### 플러시

플러시(flush())는 연속성 컨텍스트의 변경 내용을 데이터베이스에 반영한다.

영속성 컨텍스트를 플러시 하는 방법

1. em.flush()를 직접 호출
2. 트랜잭션 커밋 시 플러시가 자동 호출
3. JPQL 쿼리 실행 시 플러시가 자동 호출

#### 직접호출

테스트나 다른 플레임워크와 JPA를 함께 사용할 때를 제외하고 거의 사용하지 않음

#### 트랜잭션 커밋 시 플러시가 자동 호출

데이터베이스에 변경 내용을 SQL로 전달하지 않고 트랜잭션만 커밋하면 어떤 데이터도 데이터베이스에 반영되지 않는다. 따라서 트랜잭션을 커밋하기 전에 꼭 플러시를 호출 영속성 컨텍스트의 변경 내용을 데이터베이스에 반영해야 한다. JPA는 이러한 문제를 예방하기 위해 트랜잭션을 커밋할 때 플러시를 자동으로 호출해 준다.

#### JPQL 쿼리 실행 시 플러시가 자동 호출

```java
em.persist(memberA);
em.persist(memberB);

// JPQL 실행
List<Member> members = em.createQuery("select m from Member", Member.class).getResultList();

```
위와 같이 member 엔티티를 영속성에 저장후 JPQL를 통해 데이터를 조회시 memberA,B는 조회가 될까?
JPQL은 SQL로 변환되어 데이터베이스에서 엔티티를 조회한다. 그러나 아직 memberA,B는 데이터베이스에 반영되어 있지 않으므로 조회되지 않을 것이다. 이러한 문제를 예방하기 위해 JPQL을 실행 할때 flush()를 자동으로 호출해 줘서 memberA,B 가 결과에 포함된다.

#### 플러시 모드 옵션

* FlushModeType.AUTO : 커밋이나 쿼리를 실행할 때 플러시(기본값)
* FlushModeType.COMMIT : 커밋할 때만 플러시

### 준영속

```java

// 회원 엔티티를 연속 상태
em.persist(memberA);
em.persist(memberB);

// 회원 엔티티를 준영속 상태
em.detach(memberA);

// 트랜젝션 커밋
tr.commit();
```

영속화된 상태의 memberA 엔티티를 관리하지 말라는 것으로 1차 캐시부터 쓰기지연 SQL 저장소까지 해당 엔티티를 관리하기 위한 모든 정보를 제거한다.


#### 영속성 컨텍스트 초기화 : clear()

em.detach()가 특정 엔티티 하나를 준영속 상태로 만들었다면 em.clear()는 연속성 컨텍스트를 초기화해서 해당 연속성 컨텍스트의 모든 엔티티를 준영속 상태로 만든다.

### 영속성 컨텍스트 종료 : close()

영속성 컨텍스트가 종료되어 더이상 관리되지 않는 상태이다.


#### 준영속 상태의 특징

* 거의 비영속 상태에 가깝다.
* 식별자 값을 가지고 있다.
* 지연 로딩을 할 수 없다.

#### 병합 : merge()

준영속 상태의 엔티티를 다시 영속 상태로 변경하려면 병합을 사용한다.

```java
// 회원 엔티티를 연속 상태
em.persist(memberA);

// 회원 엔티티를 준영속 상태
em.detach(memberA);

// mergeMemberA는 다시 연속상태가 됨
Member mergeMemberA = em.merge(memberA);

```