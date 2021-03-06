
[//]: # (todo 각 챕터별 적절한 code example 추가)

## chapter 8. 단일 책임 원칙 (SRP: Single Responsibility Principle)

> 한 클래스는 단 한 가지의 변경 이유만을 가져야 한다.

한 클래스가 하나 이상의 책임을 맡는다면, 그 책임들은 결합된다.
한 책임에 대한 변경은 다른 책임을 충족시키는 클래스의 능력을 떨어뜨리거나 저하시킬 수도 있다.
이런 종류의 결합은 변경을 했을 때 예상치 못한 방식으로 잘못 동작하는 취약한 설계를 유발한다.

#### 책임이란?

```java
interface Modem {
    public void dial(Stringpno);
    public void hangup();
    public void send(char c);
    public char recv();
}
```

위 Modem 이라는 인터페이스는 타당해 보인다.
하지만 Data channel 이라는 책임과 Connection 이라는 두가지 책임이 보인다.
`dial()`, `hangup()`는  Connection,
`send()`, `recv()`는  Data channel.
그렇다면 두 책임이 분리되어야 할까?

이는 어플리케이션이 어떻게 바뀌는가에 달려있다.
어플리케이션이 Data channel 의 함수 시그니처에 영향을 주는 방식으로 바뀐다면,
`send()`, `recv()`는 좀 더 자주 재컴파일, 재배포되어야 한다.
이는 C++ 의 경우엔 링킹 시간, 컴파일 시간, 메모리 영역소비 등의 문제를 야기한다.
결과적으로 [경직성 문제]()를 야기하므로 분리하는 것이 맞다.

반면에 어플리케이션이 두 가지 책임의 변경을 유발하는 방식으로 바뀌지 않는다면, 이들을 분리할 필요없다.
이런 경우 이들을 분리하면, 오히려 [불필요한 복잡성 문제]()를 야기한다.



## chapter 9. 개방 폐쇄 원칙 (OCP: Open-Closed Principle)

> 소프트웨어 개체 (class, module, function etc...) 는 확장에 대해 열려 있어야 하고, 수정에 대해서는 닫혀있어야 한다.

모듈의 행위는 확장될 수 있다. 즉 모듈이 하는 일을 변경할 수 있다. 하지만 수정에 대해서는 닫혀있다. 즉 행위를 확장하는 것이 그 모듈의 소스코드나 바이너리 코드의 변경을 초래하지 않는다.

바이너리 파일을 변경한다는 것은 DLL, 공유 라이브러리, 또는 다른 종류의 바이너리 컴포넌트가 재배포 되어야함을 의미한다.  

### 추상화

개방 폐쇄 원칙을 지키기 위한 방법으로는 추상화가 있다.

## chapter 10. 리스코프 치환 원칙 (LSP : Liskov Substitution Principle)

> 서브타입은 그것의 기반타입으로 치환 가능해야 한다.

리스코프 치환 원칙은 바람직한 상속 계층구조에 대해 다룬다.


## chapter 11. 의존 관계 역전 원칙 (DIP : Dependency Inversion Principle)

> a. 상위 수준의 모듈은 하위수준의 모듈에 의존해서는 안 된다. 둘 모두 추상화에 의존해야 한다.
> 
> b. 추상화는 구체적인 사항에 의존해서는 안된다. 구체적인 사항은 추상화에 의존해야 한다.


## chapter 12. 인터페이스 분리 원칙 (ISP : Interface Segregation Principle)

> 클라이언트가 자신이 사용하지 않는 메소드에 의존하도록 강제되어서는 안 된다

