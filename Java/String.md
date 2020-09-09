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

### String 메소드
- 사용 빈도가 높은 메소드
  - char charAt(int index) : 특정 위치의 문자 리턴 ex) 주민번호로 성별 판별할 때
```
String ssn = "010624-2231231";
    char sex = ssn.charAt(7);
    switch (sex) {
        case '1':
        case '3':
            System.out.println("남자");
            break;

        case '2':
        case '4':
            System.out.println("여자");
            break;
    }  
```
  - boolean equals(Object anObject) : 두 문자열을 비교 (값 비교), == -> 주소 비교
  - byte[] getBytes() : byte[]로 리턴
  - int indexOf() : 문자열 찾기
    - 매개값으로 주어진 문자열이 시작되는 인덱스를 리턴한다.
    - 주어진 문자열이 포함되어 있지 않으면 -1을 리턴한다.
```
String sub = "자바 프로그래밍";
int index = sub.indexOf("프로그래밍"); // 3
```
  - int length() : 문자열 길이
  - replace() : 문자열 대치
    - 첫번째 매개값인 문자열을 찾아 두번째 매개값인 문자열로 대치한 새로운 문자열을 리턴
    - String은 값을 변경할 수 없기 때문에 새로운 객체를 참조하는 방식으로 문자열을 변경한다
```
String oldStr = "자바 프로그래밍";
String newStr = oldStr.replace("자바", "JAVA");
```
  - substring() : 문자열 잘라내기
    - substring(int beginIndex, int endIndex) : 주어진 시작과 끝 인덱스 사이의 문자열을 추출
    - substring(int beginIndex) : 주어진 인덱스 이후부터 끝까지 문자열을 추출
  
  - toLowerCase(). toUpperCase() : 알파벳 소, 대문자 변경
  - trin() : 문자열 앞 뒤 공백 잘라내기 (중간의 공백은 제거되지않음)
  - **valueOf() : 기본 타입의 값을 문자열로 변환, static**
  
  
### StringTokenizer 클래스
  - 문자열 분리 방법
    - String의 split() 메소드 이용
    - java.util.StringTokenizer 이용
  
  - split() : 정규표현식을 구분자로 해서 부분 문자열을 분리한 후 배열에 저장하고 리턴함
```
String text = "홍&이,박,김-최";
String[] names = text.split("&|,|-");
```  
  - StringTokenizer
```
String text = "홍/이/박"
StringTokenizer st = new StringTokenizer(text, "/");

// 남아있는 토큰이 있는지 여부
while(st.hasMoreTokens() {

  // 토큰을 하나씩 꺼내서 token에 저장
  String token = st.nextToken();  
  
  // 토큰 출력
  System.out.println(token);
}

// countTokens() : 꺼내지 않고 남아있는 토큰의 수
```   
  
### StringBuffer, StringBuilder 클래스
  - 문자열 결합 연산자 +
    - String은 내부의 문자열을 수정할 수 없다.
```
String data = "ABC";
data += "DEF";

// 위 결과 data에는 "ABCDEF"가 저장되지만 처음 생성된 data객체에 DEF가 추가되는것이 아닌 
// 새로운 객체를 만들어 참조하는것으로 결국 객체를 두개 생성하는 꼴이 되므로 메모리를 차지하게 됨
```
  
  - StringBuffer, StringBuilder
    - 버퍼(데이터를 임시로 저장하는 메모리)에 문자열을 저장한다.
    - 버퍼 내부에서는 추가, 수정, 삭제 작업이 가능하다.
    - 멀티 스레드 환경에서는 StringBuffer, 단일 스레드 환경에는 StringBuilder 사용
    - 사용 메소드는 둘다 같음
  
  - 메소드
    - append(...) : 문자열 추가
    - insert(int offset, ...) : 인덱스의 위치에 문자열을 추가함
    - delete(int start, int end) : 시작 인덱스부터 끝 인덱스까지의 문자열 삭제
    - deleteCharAt(int index) : 주어진 인덱스의 문자를 삭제
    - replace(int start, int end, String str) : 시작 인덱스부터 끝 인덱스까지의 문자열을 str로 대체
    - StringBuilder reverse()
    - setCharAt(int index, char ch) : 주어진 인덱스의 문자를 ch로 바꿈
  
  
### 정규 표현식과 Pattern 클래스
  - 문자열이 정해져 있는 형식으로 구성되어 있는지 검증할 때 사용
  - 문자 또는 숫자 기호와 반복 기호가 결합된 문자열이다.
  - 기본적으로 알아둬야 할 기호
```
[] : 한 개의 문자
[abc] : a,b,c 중 하나의 문자
[^abc] : a,b,c 이외의 하나의 문자
[a-zA-z] : a-z 중 하나의 문자
\d : 한 개의 숫자, [0-9]와 동일
\s : 공백
\w : 한 개의 알파벳 또는 한 개의 숫자, [a-zA-z_0-9]와 동일
? : 없음 또는 한 개
* : 없음 또는 한 개 이상
+ : 한 개 이상
{n} : 정확히 n개
{n,} : 최소한 n개
(n, m) n개부터 m개까지
() : 그룹핑

// 전화번호
(02|010)-\d{3,4}-\d{4}

// 이메일
// white@naver.com or white@naver.co.kr
\w+@\w+\.\w+{\.\w+}?

```
  
  
  
  
  
  
  
  
  
  
  
