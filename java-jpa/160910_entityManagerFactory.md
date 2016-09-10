### 엔티티 매니저 팩토리와 엔티티 매니저

#### 엔티티 매니저 팩토리

엔티티 매니저를 만드는 공장, 공장을 만드는 비용은 크다 따라서 한 개만 만들어서 애플리케이션 전체에서 공유하도록 설계되어 있다. 그 반면에 공장에서 엔티티 매니저를 생성하는 비용은 거의 들지 않는다.  그리고 엔티티 매니저 팩토리는 여러 스레드가 동시에 접근해도 안전하므로 서로 다른 스레드 간에 공유해도 되지만, 엔티티 매니저는 여러 스레드가 동시에 접근하면 동시성 문제가 발생하므로 스레드 간에 절대 공유되어서는 안된다.


```java
//엔티티 매니저 팩토리 생성
EntityManagerFactory emf = Persistence.createEntityManagerFactory("jpademo");
//엔티티 매니저 생성
EntityManager em = emf.createEntityManager();
//트랜잭션 기능 획득
EntityTransaction tx = em.getTransaction();

//트랜젝션 시작
tx.begin();

~~~~~~~~~~~~~~~~~~~~~~~~~~~
비즈니스 로직 처리
~~~~~~~~~~~~~~~~~~~~~~~~~~~

//트랜젝션 커밋
tx.commit();

//엔티티 매니저 종료
em.close();

//엔티티 매니저 팩토리 종료
emf.close();
```
