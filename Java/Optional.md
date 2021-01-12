## Optional

- Java Optional 클래스는 Java 8에서 추가되었으며 자바의 고질적인 문제인 NullPointerException 문제를 해결하기 위해 만들어졌다.

#### NullPointerException이 발생하는 경우
- null 객체의 인스턴스 메서드를 호출합니다.
  - Object obj = null; obj.toString();
- null 객체의 필드 액세스 또는 수정.
  - Person p = null; p.name = "nhj";
- 빈 배열 객체에 길이 속성을 가져올 때
  - int[] arrayInts = null; arrayInts.length;
- 배열 슬롯 중 null 인 액세스하거나 수정합니다.
  - String[] arrayStr = new String[2]; arrayStr[0] = "aa"; arrayStr[1].toString(); 
- Throwable 값인 것처럼 null을 던집니다.
  - throw null;

#### of, ofNullable로 객체 감싸기
- NullPointerException 에러를 해결하기 위한 방법으로 아래와 같이 if문을 이용할 수 있다.
```
if(name != null) { 
        System.out.println(name.length); 
}
```
- 하지만 이 방법은 각 변수마다 null값을 체크해야되기 때문에 프로그래머의 실수를 유발할 수 있고   
  코드가 길어짐에 따라 코드의 가독성이 점점 떨어지게 된다.   
- Optional 방식은 위의 문제를 해결하여 가독성 좋고 강건한 코드를 만드는 데 도움을 준다.

```
@Test
public void ofTest() {
    String name = null;
    Optional<String> opt = Optional.of(name); // NullPointerException
}

@Test
public void ofNullableTest() {
    String name = null;
    Optional<String> opt = Optional.ofNullable(name);
}
```

- ofNullable과 달리 of는 null값이 입력으로 들어오면 NullPointerException을 발생시킨다.

#### orElse, orElseGet으로 Optional 값 가져오기
- if에서 null값이 아닌 경우의 처리를 else 키워드 이하의 코드로 해결하지만 Optional 에서는 orElse로 간단하게 해결할 수 있습니다.



