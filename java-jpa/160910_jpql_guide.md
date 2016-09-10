## JPQL languge reference

JPQL은 엔티티 객체를 대상으로 쿼리를 제공해 준다. 쉽게 말하면 클래스와 필드를 대상으로 쿼리를 한다는 의미다.

참고문서 : http://docs.oracle.com/html/E13946_05/ejb3_langref.html

아래는 기본적인 JPQL를 사용 할 수 있는 자바코드 입니다. 샘플은 작성해 올려 링크 할 예정이다.
```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpa_persistence_xml");
EntityManager em = emf.createEntityManager(); //엔티티 매니저 생성
EntityTransaction tx = em.getTransaction(); //트랜잭션 기능 획득

try {
    //트랜잭션 시작
    tx.begin();

    //비즈니스 로직
    List<T> tTableObjects = em.createQuery("select m from Member m", T.class).getResultList();
    System.out.println("tTableObjects.size=" + tTableObjects.size());

    //트랜젝션 커밋
    tx.commit();
} catch (Exception e) {
    e.printStackTrace();
    tx.rollback(); //트랜잭션 롤백
} finally {
    em.close(); //엔티티 매니저 종료
}

//엔티티 매니저 팩토리 종료
emf.close();
```

그럼 JPQL을 이용한 몇가지 쿼리 예제를 보도록 하자.

#### JPQL Identification Variables

테이블 Magazine 과 테이블 aricles 과 테이블 author 가 있을때 작가의 퍼스트 이름 'John'인 Magazine 을 구할 때 예제.

```sql
SELECT DISTINCT mag FROM Magazine mag JOIN mag.articles art JOIN art.author auth WHERE auth.firstName = 'John'
```

#### JPQL Range Declarations

특정 범위의 데이터를 조회 할 때

테이블 Magazine 중 publisher (발행자)가 'Adventure' 인경우의 가격보다 큰 Magaine을 구할 때 예제.

```sql
SELECT DISTINCT mag1 FROM Magazine mag1, Magazine mag2
WHERE mag1.price > mag2.price AND mag2.publisher.name = 'Adventure'
```

### JPQL Named Parameters

Named Parameters를 이용해 총수익(revenue)이 파라메터값보다 큰 발행자(Publisher)를 구 할때 예제.

```sql
SELECT pub FROM Publisher pub WHERE pub.revenue > :rev
```

```java
//비즈니스 로직
List<Publisher> pubs = em.createQuery("SELECT pub FROM Publisher pub WHERE pub.revenue > :rev", T.class).setParameter("rev",.getResultList();
System.out.println("pubs.size=" + pubs.size());
```

### JPQL Aggregate Functions

JPQL 집합함수 사용 할 때 예제

```sql
SELECT AVG(mag.price) FROM Magazine mag
SELECT SUM(mag.price) FROM Publisher pub JOIN pub.magazines mag pub.firstName = 'Larry'
SELECT COUNT(mag) FROM Magazine mag
```

### JPQL ORDER BY Clause

```sql
SELECT pub FROM Publisher pub JOIN pub.magazines mag ORDER BY o.revenue, o.name
```

### JPQL Bulk Update

```sql
DELETE FROM Publisher pub WHERE pub.revenue > 1000000.0
DELETE FROM Publisher pub WHERE pub.revenue = 0 AND pub.magazines IS EMPTY
UPDATE Publisher pub SET pub.status = 'outstanding'
    WHERE pub.revenue < 1000000 AND 20 > (SELECT COUNT(mag) FROM pub.magazines mag)
```

### JPQL Subqueries

서브쿼리 사용 예제.

```sql
SELECT DISTINCT auth FROM Author auth
    WHERE EXISTS (SELECT spouseAuth FROM Author spouseAuth WHERE spouseAuth = auth.spouse)

SELECT mag FROM Magazine mag
    WHERE (SELECT COUNT(art) FROM mag.articles art) > 10

SELECT goodPublisher FROM Publisher goodPublisher
    WHERE goodPublisher.revenue < ( SELECT AVG(p.revenue) FROM Publisher p )
```

### JPQL Empty Collection Comparison Expressions

```sql
SELECT mag FROM Magazine mag WHERE mag.articles IS EMPTY
```

### JPQL In Expressions

```sql
SELECT o FROM Order o where o.country IN ('UK', 'US', 'France')
SELECT o FROM Order o where (o.country = 'UK') OR (o.country = 'US') OR (o.country = ' France')
SELECT o FROM Order o where o.country NOT IN ('UK', 'US', 'France')
SELECT o FROM Order o where NOT ((o.country = 'UK') OR (o.country = 'US') OR (o.country = 'France'))
```
