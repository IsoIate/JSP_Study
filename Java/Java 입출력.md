## BufferedReader 
- 데이터를 바로 전송하는 Scanner에 비해 버퍼를 이용하여 한번에 전송하므로 효율적임
- Scanner보다 알고리즘 면에서 효율적이지만 사용법이 복잡함
- 입력값이 String값으로 들어오므로 형변환 필수

### 사용 예시
```
try { // 예외처리 때문에 try catch문이나 throws를 사용해야 함
  BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); // BufferedReader 생성
  String input = br.readLine(); // 값 입력 (String값)
  char array[] = input.toCharArray(); // (번외) String 문자열을 하나씩 char형 배열에 삽입

  br.close();
} catch (IOException e) {
  e.printStackTrace();
} 
```


## BufferedWriter
- BufferedReader와 마찬가지로 버퍼를 사용하며 System.out.print();에 비해 알고리즘 면에서 효율적임
- 출력 시 개행이 되지 않으므로 따로 시행해야 함

### 사용 예시
```
BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
String output = "hello";

bw.write(output);
bw.newLine(); // 개행
bw.write(output + "\n");  // 개행 2

bw.flush();
bw.close();
```


## StringTokenizer
- split은 String클래스의 메소드로 추출한 문자를 배열로 저장한다
- StringTokenizer는 메소드가 아니라 java.util에 포함되어 있는 자체 클래스
- 각각 사용방법이 다르고 StringTokenizer클래스는 내부에 꼭 넣어야 하는 메소드가 존재함

### countTokens
- 마지막으로 토큰을 가져오기 전 남은 토큰 수를 출력하는 메소드 (int)

### nextToken
- 토큰을 읽어오는 메소드 (String)

### 사용 예시
```
String input = "안녕하세요.반갑습니다.감사합니다";
StringTokenizer st = new StringTokenizer(input, "."); // 다양한 문자로 구분 가능

int count = st.countTokens(); // 토큰 수 확인

for (int i = 0; i < count; i++) {
  String data = st.nextToken(); // 토큰 
  System.out.print(data + " "); 
}

```














