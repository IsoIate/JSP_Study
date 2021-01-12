## Assertion
- 작성한 코드가 생각대로 작동하고 있는지 검증하기 위해 사용하는 예약어

#### Assertion과 Exception의 차이점
- 예외는 특정 부분에서 예외가 발생하여 비 정상적인 프로그램 종료를 막고 예외 처리로 인해 프로그램의 신뢰성을 높임
- Assertion은 특정 결과를 위해 코드나 값이 예상하는 값이어야 하는 것을 검증하기 위함

#### 기본 문법
````
// 1번째
assert [boolean 식];

// 2번째
assert [boolean 식 : 조건식이 false 일 때 나타날 문장]; 
````

#### 메소드
- assertEquals(x,y) 
  - x와 y가 일치함을 확인함. 예상 값(x) 과 실제 값 (y) 이 같으면 테스트 통과
- assertArrayEquals(a, b);
  - 배열 A와 B가 일치함을 확인합니다.
- assertFalse(x)
  - x가 false 인지 확인합니다.
- assertTrue(x)
  - x가 true 인지 확인합니다.
- assertTrue(message, condition)
  - condition이  true이면 message표시
- assertNull(o)
  - 객체o가 null인지 확인합니다.
- assertNotNull(o)
  - 객체o가 null이 아닌지 확인합니다.
- assertSame(ox, oy)
  - 객체 ox와 oy가 같은 객체임을 확인합니다.
  - ox와 oy가 같은 객체를 참조하고 있으면 테스트 통과
  - assertEquals()메서드는 두 객체의 값이 같은지 확인하고, assertSame()메서드는 두 객체의 레퍼런스가 동일한가를 확인합니다. (== 연산자)
- assertNotSame(ox, oy)
  - ox와 oy가 같은 객체를 참조하고 있지 않으면 통과
- assertfail()
  - 테스트를 바로 실패처리
