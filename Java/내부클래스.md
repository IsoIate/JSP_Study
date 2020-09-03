## 내부클래스

  - 클래스 내에 클래스를 작성하는 것
  - 외부 클래스의 속성이나 메서드를 내부 클래스에서 사용 가능
  - 내부 클래스를 static (정적) 선언 시 외부 클래스 값에 접근이 불가능함
  - static 선언 시 객체(인스턴스)를 생성하지 않고도 바로 생성되기 때문에 객체가 생성되지 않은 외부 클래스의 값이 존재하지 않기 때문
  
```

public class StudyJava {

  public int a = 5;

    class InnerTest{
      int b = 7;

      public int add() {
          return a + b;
      }
  }
}
  
  ```

