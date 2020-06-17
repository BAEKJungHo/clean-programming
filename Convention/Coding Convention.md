# My Coding Convention 

> 나만의 코딩 컨벤션 스타일을 구축하고자 만든 문서 

## 파일 공통 요건 (Common Files Setting)

### 1. 파일 인코딩은 UTF-8 (`[encoding-utf8]`)
  * 모든 소스, 텍스트 문서 파일의 인코딩은 UTF-8 로 통일한다.

## 네이밍 (Naming)

### 1. 식별자에는 영문, 숫자, 언더스코어(`_`) 만 허용 (`[identifier-char-scope]`)
  * 변수명, 클래스명, 메서드명 등에는 영어와 숫자만을 사용한다. 상수에는 단어 사이의 구분을 위하여 언더스코어(`_`)를 사용한다. 정규표현식 `[^A-Za-z0-9_]`에 부합해야 한다.

### 2. 한국어 발음대로 표기 금지 (`[avoid-korean-pronounce]`)
  * 식별자의 이름을 한글 발음을 영어로 옮겨서 표기하지 않는다. 한국어 고유명사는 예외이다.
    - 나쁜 예 : moohyungJasan (무형자산)
    - 좋은 예 : intangibleAssets (무형자산)
    
### 3. 패키지 이름은 소문자로 구성 (`[package-lowercase]`)
  * 패키지 이름은 소문자를 사용하여 작성한다. 단어별 구문을 위해 언더스코어(`_`)나 대문자를 섞지 않는다.
    - 나쁜 예
      ```
      package com.navercorp.apiGateway
      package com.navercorp.api_gateway
      ```
    - 좋은 예
      ```java
      package com.navercorp.apigateway
      ```
      
### 4. 클래스/인터페이스 이름에 대문자 카멜표기법 적용 (`[class-interface-lower-camelcase]`)
  * 클래스 이름은 단어의 첫 글자를 대문자로 시작하는 대문자 카멜표기법(Upper camel case)을 사용한다. 파스칼표기법(Pascal case)으로도 불린다.
    - 나쁜 예
      ```java
      public class reservation
      public class Accesstoken
      ```
    - 좋은 예
      ```java
      public class Reservation
      public class AccessToken
      ```
      
### 5. 클래스 이름에 명사 사용 (`[class-noun]`)
  * 클래스 이름은 명사나 명사절로 짓는다.
  
### 6. 인터페이스 이름에 명사/형용사 사용 (`[interface-noun-adj]`)
  * 인터페이스(interface)의 이름은 클래스 이름은 명사/명사절로 혹은 형용사/형용사절로 짓는다.
    - 좋은 예
      ```java
      public interface RowMapper {}
      public interface AutoClosable {}
      ```
### 7. 테스트 클래스는 'Test’로 끝남 (`[test-class-suffix]`)
  * JUnit 등으로 작성한 테스트 코드를 담은 클래스는 'Test’을 마지막에 붙인다.
    - 좋은 예
      ```java
      public class WatcherTest {}
      ```
      
### 8. 메서드 이름에 소문자 카멜표기법 적용 (`[method-lower-camelcase]`)
  * 메서드의 이름에는 첫 번째 단어를 소문자로 작성하고, 이어지는 단어의 첫 글자를 대문자로 작성하는 소문자 카멜표기법(Lower camel case)를 사용한다. 테스트 클래스의 메서드 이름에서는 언더스코어를 허용한다.

### 9. 메서드 이름은 동사/전치사로 시작 (`[method-verb-preposition]`)
  * 메서드명은 기본적으로는 동사로 시작한다. 다른 타입으로 전환하는 메서드나 빌더 패턴을 구현한 클래스의 메서드에는 전치사를 쓸 수 있다.
    - 좋은 예
      + 동사사용 : renderHtml()
      + 전환메서드의 전치사 : toString()
      + Builder 패턴 적용한 클래스의 메서드의 전치사 : withUserId(String id)
      
### 10. 신조어 알아 맞히기 금지 (`[do-not-guess-right-variable]`)
  * 변수명(클래스와 메서드명을 포함)은 신조어 알아 맞히기가 되어서는 안된다.
    - 나쁜 예
      ```java
      private String s;
      private String idx;
      ```
    - 좋은 예
      ```java
      private String sequence;
      private String index;
      ```

### 11. 상수는 대문자와 언더스코어로 구성 (`[constant_uppercase]`)
  * 상태를 가지지 않는 자료형이면서 static final 로 선언되어 있는 필드일 때를 상수로 간주한다. 상수 이름은 대문자로 작성하며, 복합어는 언더스코어(`_`)를 사용하여 단어를 구분한다.
    - 좋은 예
      ```java
      public final int UNLIMITED = -1;
      public final String POSTAL_CODE_EXPRESSION = “POST”;
      ```
      
### 12. 변수에 소문자 카멜표기법 적용 (`[var-lower-camelcase]`)
  * 상수가 아닌 클래스의 멤버변수/지역변수/메서드 파라미터에는 소문자 카멜표기법(Lower camel case)을 사용한다.
    - 나쁜 예
      ```java
      private boolean Authorized;
      private int AccessToken;
      ```
    - 좋은 예
      ```java
      private boolean authorized;
      private int accessToken;
      ```
      
## 선언 (Declarations)

### 1. static import 에만 와일드 카드 허용 (`[avoid-star-import]`)
  * 클래스를 import 할 때는 와일드카드(`*`) 없이 모든 클래스명을 다 쓴다. static import 에서는 와일드카드를 허용한다.
    - 나쁜 예
    ```java
    import java.util.*;
    ```
    - 좋은 예
    ```java
    import java.util.List;
    import java.util.ArrayList;
    ```

### 2. 제한자 선언의 순서 (`[modifier-order]`)
  * 클래스/메서드/멤버변수의 제한자는 Java Language Specification 에서 명시한 아래의 순서로 쓴다
    - public protected private abstract static final transient volatile synchronized native strictfp
      + [Java Language Specification - Chapter 18. Syntax](https://docs.oracle.com/javase/specs/jls/se7/html/jls-18.html) 참조
      
### 3. 어노테이션 선언 후 새줄 사용 (`[newline-after-annotation]`)
  * 클래스, 인터페이스, 메서드, 생성자에 붙는 애너테이션은 선언 후 새줄을 사용한다. 이 위치에서도 파라미터가 없는 애너테이션 1개는 같은 줄에 선언할 수 있다.
    - 좋은 예
    ```java
    @RequestMapping("/guests")
    public void findGuests() {}
    
    @Override public void destroy() {}
    ```
    
### 4. 한 줄에 한 문장 (`[1-state-per-line]`)
  * 문장이 끝나는 ; 뒤에는 새줄을 삽입한다. 한 줄에 여러 문장을 쓰지 않는다.
    - 나쁜 예
    ```java
    int base = 0; int weight = 2;
    ```
    - 좋은 예
    ```java
    int base = 0;
    int weight = 2;
    ```
    
### 5. 클래스 중괄호 시작과 끝은 빈 줄 포함 (`[class-start-end-include-blank-lines]`)
  * 클래스 중괄호의 시작과 끝 부분은 빈 줄을 포함해야 한다.
    - 나쁜 예 
      ```java
      public class Event {
        private String name;
        public String getName() {
          return name;
        }
      }
      ```
    - 좋은 예
      ```java
      public class Event {
     
        private String name;
        
        public String getName() {
          return name;
        }
        
      }
      ```   

### 6. 수직과 수평 스크롤을 고려 (`[consider-scrolling]`)
  * 수직과 수평 스크롤을 고려하여 줄바 꿈을 해야 한다.
    - 파라미터가 3 개 이상인 경우에만 매개변수 줄바꿈을 실시한다.
      + 좋은예
        ```java
        public String argumentScrolling(
          String name,
          String age,
          String phone
        ) {}
        ```
    - 메서드의 길이는 최대 15 줄 이내로 작성하도록 노력한다.
      + 메서드의 길이가 길수록 코드 분석이 어려워지고 메서드가 많은 책임을 가지고 있을 수 있다.
      + 수직 스크롤이 늘어난다는 것은 가독성이 떨어진다는 것이다.
      
### 7. 매개변수가 3개 이상이면 매개변수를 줄일 수 있는지 고려 (`[consider-arguements-count]`)
  * 매개변수가 3개 이상이면 매개변수를 줄일 수 있는지 고려해야 한다.
    - 많은 매개변수는 가독성을 떨어뜨린다.
    
## References

> https://naver.github.io/hackday-conventions-java/#space-after-bracket
