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
      
### 5. 수직과 수평 스크롤을 고려 (`[consider-scrolling]`)
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
      
### 6. 매개변수가 3개 이상이면 매개변수를 줄일 수 있는지 고려 (`[consider-arguements-count]`)
  * 매개변수가 3개 이상이면 매개변수를 줄일 수 있는지 고려해야 한다.
    - 많은 매개변수는 가독성을 떨어뜨린다.
    
### 7. 배열에서 대괄호는 타입 뒤에 선언 (`[array-square-after-type]`)
  * 배열 선언에 오는 대괄호(`[]`)는 타입의 바로 뒤에 붙인다. 변수명 뒤에 붙이지 않는다.
    - 나쁜 예
      ```java
      String names[];
      ```
    - 좋은 예
      ```java
      String[] names;
      ```

### 8. long 형 값의 마지막에 L 붙이기 (`[long-value-suffix]`)
  * long 형의 숫자에는 마지막에 대문자 'L' 을 붙인다. 소문자 'l' 보다 숫자 '1' 과의 차이가 커서 가독성이 높아진다.
    - 나쁜 예
      ```java
      long base = 54423234211l;
      ```
    - 좋은 예
      ```java
      long base = 54423234211L;
      ```
      
### 9. 특수 문자의 전용 선언 방식을 활용 (`[special-escape]`)
  * `\b, \f, \n,\r,\t, \", \\` 와 같이 특별히 정의된 선언 방식이 있는 특수 문자가 있다. 이런 문자들은 숫자를 이용한 `\008` 이나 `\u0008` 과 같은 숫자를 넣은 선언보다 전용 방식을 활용한다.
    - 나쁜 예
      ```java
      System.out.println("---\012---");
      ```
    - 좋은 예
      ```java
      System.out.println("---\n---");
      ```
      
## 들여쓰기 (Indentation)

들여쓰기는 코드의 계층을 구분하기 위해 추가하는 문자이다.

### 1. 하드탭 사용 (`[indentation-tab]`)
  * 탭(tab) 문자를 사용하여 들여쓴다. 탭 대신 스페이스를 사용하지 않는다. 이를 잘 준수하기 위해서 스페이스와 탭을 구별해서 보여주도록 에디터를 설정한다.

### 2. 탭의 크기는 4개의 스페이스 (`[4-spaces-tab]`)
  * 1개의 탭의 크기는 스페이스 4개와 같도록 에디터에서 설정한다.
  
### 3. 블럭 들여쓰기 (`[block-indentation]`)
  * 클래스, 메서드, 제어문 등의 코드 블럭이 생길 때마다 1단계를 더 들여쓴다.
  
## 중괄호 (Braces)

중괄호(`{}`) 는 클래스, 메서드, 제어문의 블럭을 구분한다.

### 1. K&R 스타일로 중괄호 선언 (`[braces-knr-style]`)
  * 클래스 선언, 메서드 선언, 조건/반복문 등의 코드 블럭을 감싸는 중괄호에 적용되는 규칙이다. 중괄호 선언은 K&R 스타일(Kernighan and Ritchie style)을 따른다. 줄의 마지막에서 시작 중괄호`{`를 쓰고 열고 새줄을 삽입한다. 블럭을 마친후에는 새줄 삽입 후 중괄호를 닫는다.
    - 나쁜 예
      ```java
      public class SearchConditionParser
      {
          public boolean isValidExpression(String exp)
          {

              if (exp == null)
              {
                  return false;
              }

              for (char ch : exp.toCharArray())
              {
                   ....
              }

              return true;
          }
      }
      ```
    - 좋은 예
      ```java
      public class SearchConditionParser {
         public boolean isValidExpression(String exp) {

             if (exp == null) {
                 return false;
             }

             for (char ch : exp.toCharArray()) {
                 ....
             }

             return true;
         }
      }
      ```

### 2. 닫는 중괄호와 같은 줄에 else, catch, finally, while 선언 (`[sub-flow-after-brace]`)
  * 아래의 키워드는 닫는 중괄호(`{}`) 와 같은 줄에 쓴다.
    - 나쁜 예
      ```java
      if (line.startWith(WARNING_PREFIX)) {
          return LogPattern.WARN;
      }
      else if (line.startWith(DANGER_PREFIX)) {
          return LogPattern.DANGER;
      }
      else {
          return LogPattern.NORMAL;
      }
      ```
    - 좋은 예
      ```java
      if (line.startWith(WARNING_PREFIX)) {
          return LogPattern.WARN;
      } else if (line.startWith(DANGER_PREFIX)) {
          return LogPattern.DANGER;
      } else {
          return LogPattern.NORMAL;
      }
      ```

### 3. 빈 블럭에 새줄 없이 중괄호 닫기 허용 (`[permit-concise-empty-block]`)
  * 내용이 없는 블럭을 선언할 때는 같은 줄에서 중괄호를 닫는 것을 허용한다.
    - 좋은 예
      ```java
      public void close() {}
      ```

### 4. 조건/반복문에 중괄호 필수 사용 (`[need-braces]`)
  * 조건, 반복문이 한 줄로 끝더라도 중괄호를 활용한다. 이 문서에 언급된 중괄호의 전후의 공백, 제어문 앞 뒤의 새줄 규칙도 함께 고려한다.
    - 나쁜 예
      ```java
      if (exp == null) return false;
      for (char ch : exp.toCharArray()) if (ch == 0) return false;
      ```
    - 좋은 예
      ```java
      if (exp == null) {
          return false;
      }

      for (char ch : exp.toCharArray()) {
          if (ch == 0) {
              return false;
          }
      }
      ```
      
## 소괄호 (parentheses)    

소괄호 사용 시 주의해야할 점

### 1. 소괄호의 시작은 메서드명과 for 문 등 항상 붙어 있어야 한다.
  * 소괄호의 시작은 메서드명과 for 문 등 항상 붙어 있어야 한다.
    - 좋은 예
      ```java
      public String findValues() {
        for(int i=0; i<10; i++){}
      }
      ```
    
## for 문 (For Loop)

for 문 사용 시 주의해야할 점

### 1. for 문 변수 선언 형식 (`[format-for]`)
  * for 문 변수 선언 형식은 아래와 같이 한다.
    - 나쁜 예
      ```java
      for(int i = 0; i < x.size(); i++) {}
      ```
    - 좋은 예
      ```java
      for(int i=0; i<x.size(); i++) {}
      ```
      
 ### 2. 이중 for 문에 j 사용 금지 (`[do-not-use-j]`)
  * 이중 for 문 사용시 변수 j 사용을 금지한다.
    - 나쁜 예
      ```java
      for(int i=0; i<10; i++) {
       for(int j=0; j<10; j++) {
       }
      }
      ```
    - 좋은 예
      ```java
      for(int i=0; i<10; i++) {
       for(int k=0; k<10; k++) {
       }
      }
      ```
      
## 빈 줄(Blank lines)

빈 줄은 명령문 그룹의 영역을 표시하기 위하여 사용한다.

### 1. package 선언 후 빈 줄 삽입 (`[blankline-after-package]`)
  * package 선언 후 빈 줄 삽입
    - 좋은 예
      ```java
      package com.naver.lucy.util;

      import java.util.Date;
      ```
      
### 2. 클래스 중괄호 시작과 끝은 빈 줄 포함 (`[class-start-end-include-blank-lines]`)
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
### 3. 메서드 중괄호 시작과 끝은 빈 줄 제거 (`[method-start-end-exclude-blank-lines]`)
  * 클래스 중괄호의 시작과 끝 부분은 빈 줄을 포함해야 한다.
    - 나쁜 예 
      ```java
        public String getName() {
        
          call();
          return name;
          
        }
      ```
    - 좋은 예
      ```java
        public String getName() {
          call();
          return name;
        }
      ```   
## References

> https://naver.github.io/hackday-conventions-java/#space-after-bracket
