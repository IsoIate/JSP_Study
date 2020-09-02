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


## 제네릭

- 클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법
```
class Person<T> {
  public T info;
}

...

Person<String> p1 = new Person<String>();
person<StringBuilder> p2 = new Person<StringBuilder>();

```

- 왜 제네릭을 쓰는가?
  - 코드의 중복을 제거함
  - 타입 안정성? (Type Safety) 을 위함

- 제네릭 타입에는 래퍼런스 타입만 올 수 있다 (기본 데이터 타입은 불가능 (int, float 등))
- 기본 데이터 타입을 쓰려면 Wrapper 클래스를 사용해야 함

- Wrapper 클래스 사용법
```
Integer int = new Inetger(1);

```

- 제네릭의 생략
```
package javastudy;

class EmployeeInfo {
    public int rank;
    EmployeeInfo(int rank) { this.rank = rank; }
}

class Person<T, S> {
    public T info;
    public S id;
    Person(T info, S id) {
        this.info = info;
        this.id = id;
    }
    // info의 데이터 타입을 지정하고 싶지 않을 때
    public <U> void printInfo(U info) {
        System.out.printf("info");
    }
}

public class GenericDemo {
    public static void main(String[] args) {
        EmployeeInfo e = new EmployeeInfo(1);
        Integer i = new Integer(10);
        
        // Person<EmployeeInfo, Integer> p1 = new Person<EmployeeInfo, Integer>(e, i);
        // 위와 같은 코드
        Person p1 = new Person(e, i);

        // p1.<EmployeeInfo>printInfo(e);
        // 위와 같은 코드
        p1.printInfo(e);
    }
}
```

- 제네릭의 제한
  - 제네릭 타입에 무분별한 데이터가 들어오는것을 방지하기 위함
  - 사용방법 : 추상클래스, 인터페이스
  
```

package javastudy;

// 추상클래스도 가능
interface Info {
    int getLevel();
}

class EmployeeInfo implements Info {
    public int rank;
    EmployeeInfo(int rank) { this.rank = rank; }
    @Override
    public int getLevel() {
        return this.rank;
    }
}

// 인터페이스이지만 extends를 사용한다 (상속 개념과는 조금 다름)
class Person<T extends Info> {
    public T info;
    Person(T info) {
        this.info = info;
        info.getLevel();
    }
}

public class GenericDemo1 {
    public static void main(String[] args) {
        Person<EmployeeInfo> p1 = new Person<EmployeeInfo>(new EmployeeInfo(1));
    }
}


```

