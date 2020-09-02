# Inversion of control

+ 일반적인 의존성에 대한 의존권
+ OwnerRepository가 있어야 OnwerController를 쓸 수 있다?
+ OnwerController는 OwnerRepository가 필요하다?
+ -> OwnerRepository 객체가 생성되지 않으면 OnwerController객체도 생성될 수 없음


```
class OnwerController {
  private OwnerRepository repository = new OwnerRepository();
}

```
+ IoC 컨테이너
  + Bean을 만들고 엮어주며 제공해준다.
  
 + Bean (클래스?)
  + 어노테이션이 붙으면 빈으로 등록됨 (컴포넌트 스캔?)
  + IoC컨테이너에서 관리
  + 등록하는 방법
    - Component Scanning
      - @Component
        - @Repository
        - @Service
        - @Controller
    - 또는 일일히 xml에 작성하거나 자바 설정 파일에 추가
    -> @SpringBootApplication 어노테이션을 설정한 Bean 내에 @Bean 추가
    
  + 꺼내쓰는 방법
    - Autowired 또는 @inject
