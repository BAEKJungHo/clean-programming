# DIP : 의존성 역전 원칙

- 프로그래머는 `추상화에 의존해야지 구체화에 의존하면 안된다.`
  - 즉, 구현체에 의존하지 말고 인터페이스에 의존하라는 의미
  - 앞서 말한, `역할에 의존하게 해야한다는 것`과 같다.
  - 역할과 구현을 철저하게 분리 해야 한다.

```java
public class UserService {
  
  // private UserRepository userRepository = new UserJoinRepository();
  private UserRepository userRepository = new UserFindRepository();
  
}
```

UserService 는 인터페이스에 의존하지만 구현 클래스에도 동시에 의존한다. `클라이언트가 구현체를 직접 선택 : DIP 위반`

> 다형성 만으로는 OCP, DIP 를 지킬 수 없다.
