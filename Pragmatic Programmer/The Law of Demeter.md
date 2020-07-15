# 디미터 법칙(The Law of Demeter)

> 모듈간의 결합도를 최소화하라.

`부끄럼 타는(shy)` 코드를 작성해서 디미터 법칙을 만족시켜야 한다.


디미터 법칙은 객체의 모든 메서드는 다음에 해당하는 메서드만을 호출해야 한다고 말한다.

- 자기 자신
- 전달받은 매개 변수
- 자신이 생성한 객체
- 컴포넌트 객체

```java
public class Demeter {
  
  private Department department;
  private UserRepository userRepository;
  
  public Demeter(UserRepository userRepository) {
    this.userRepository = userRepository;
  }
 
  public void doDemeter(User user) {
    Employee employee;
    user = findUser(); // 자기 자신
    user.print(); // 메서드로 넘어온 인자
    department = new Department();
    department.setDepartment("ABC"); // 자신이 생성한 객체
    employee.print(); // 직접 포함하고 있는 객체
  }
  
  private User findUser() {
    return userRepository.findUser();
  }
}
```

- 디미터 법칙을 위반한 사례

```java
public void showBalance(BankAccount accnt) {
  Money money = accnt.getBalance();
  printToScreen(money.printFormat());
}
```

위 예제에서 money.printFormat(); 은 디미터 법칙에 위배된다.

## References.

> https://www2.ccs.neu.edu/research/demeter/
