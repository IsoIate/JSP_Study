## Arrays.asList
- java.util.Arrays 사용(보통 사용하는 java.util.ArrayList와 다름)
- 해당 패키지는 remove(), add() 메소드를 제공하지 않음
- 대신 set(), get(), contains()를 제공함
- Arrays.asList()로 만든 List에 새로운 원소를 추가하거나 삭제는 할 수 없다. (배열 사이즈 변경 불가능)
- Array를 List처럼 사용할 수 있도록 하는 클래스
- asList()를 사용해서 객체를 만들 때 새로운 배열 객체를 만드는 것이 아니라, 원본배열의 주소값을 참조한다.
- asList()를 사용해서 내용을 수정하면 원본 배열도 함께 바뀌게 됨


```
public class AsList {
    public static void main(String[] args) {
        String[] str = {"aaa", "bbb", "ccc"};
        System.out.println(Arrays.toString(str));

        // List<> list = new ArrayList<>(); 대신 사용가능
        List<String> lst = Arrays.asList(str);  // 배열을 리스트로 변경, 새로운 배열객체를 생성 X, 원본 배열의 주소를 가져옴
        System.out.println(lst);

        // lst.add("ddd"); asList로 변경된 리스트에는 새로운 값을 추가할 수 없음

        // 두가지 방법 모두 값 변경 가능
        str[0] += "88";
        lst.set(2, lst.get(2) + "99");
        System.out.println(Arrays.toString(str));
        System.out.println(lst);
    }
}
```
