## String 클래스

- byte[] 배열을 문자열로 변환하는 생성자
```
// 배열 전체를 String 객체 생성
String str = new String(byte[] bytes);

// 지정한 문자셋으로 디코딩
String str = new Tring(byte[] bytes, String charsetName);

// 배열의 offset 인덱스 위치부터 length개 만큼 String 객체 생성
String str = new String(byte[] bytes, int offset, int length);

// 지정한 문자셋으로 디코딩
String str = new String(byte[] bytes, int offset, int length, String charsetName);
```
