# My Coding Convention 

> 나만의 코딩 컨벤션 스타일을 구축하고자 만든 문서 

## 파일 공통 요건

1. 파일 인코딩은 UTF-8 (`[encoding-utf8]`)
  * 모든 소스, 텍스트 문서 파일의 인코딩은 UTF-8 로 통일한다.

## 네이밍 

1. 식별자에는 영문, 숫자, 언더스코어(`_`) 만 허용 (`[identifier-char-scope]`)
  * 변수명, 클래스명, 메서드명 등에는 영어와 숫자만을 사용한다. 상수에는 단어 사이의 구분을 위하여 언더스코어(`_`)를 사용한다. 정규표현식 `[^A-Za-z0-9_]`에 부합해야 한다.

2. 한국어 발음대로 표기 금지 (`[avoid-korean-pronounce]`)
  * 식별자의 이름을 한글 발음을 영어로 옮겨서 표기하지 않는다. 한국어 고유명사는 예외이다.
    - 나쁜 예 : moohyungJasan (무형자산)
    - 좋은 예 : intangibleAssets (무형자산)
    
3. 클래스 중괄호 시작과 끝은 빈 줄 포함 
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
  
## References

> https://naver.github.io/hackday-conventions-java/#space-after-bracket
