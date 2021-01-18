# Studying Design Patterns with [Head First Design Patterns]

## 객체지향 원칙
- 바뀌는 부분은 캡슐화한다.
- 상속보다는 구성을 활용한다.
- 구현이 아닌 인터페이스에 맞춰서 프로그래밍한다.
- 서로 상호작용을 하는 객체 사이에서는 가능하면 느슨하게 결합하는 디자인을 사용해야 한다.

## 스트래티지 패턴(strategy pattern)
- 알고리즘군을 정의하고 각각을 캡슐화하여 교환해서 사용할 수 있도록 만든다.
- 스트래티지를 활용하면 알고리즘을 사용하는 클라이언트와는 독립적으로 알고리즘을 변경할 수 있다.
- ex) com.exam.strategy.simuduck.model.Duck은 자신의 행동알고리즘을 교환해서 사용할 수 있도록
  알고리즘군인 behavior 인터페이스를 사용한다.(composition)

## 옵저버 패턴(observer pattern)
- 한 객체의 상태가 바뀌면 그 객체에 의존하는 다른 객체들한테 연락이 가고 자동으로 내용이 갱신되는 방식으로
일대다(one-to-many) 의존성을 정의합니다.
  
## 데코레이터 패턴(decorator pattern)
- 객체에 추가 요소를 동적으로 더할 수 있다. 데코레이터를 사용하면 서브클래스를 만드는 경우에 비해 훨씬 유언하게 기능을 확장할 수 있다.

#### 핵심정리
- 상속을 통해 확장을 할 수도 있지만, 디자인의 유연성 면에서 별로 좋지 않습니다.
- 기존 코드를 수정하지 않고도 행동을 확장하는 방법이 필요합니다.
- 구성과 위임을 통해서 실행중에 새로운 행동을 추가할 수 있습니다.
- 상속 대신 데코레이터 패턴을 통해서 행동을 확장할 수 있습니다.
- 데코레이터 패턴에서는 구상 구성요소를 감싸주는 데코레이터들을 사용합니다.
- 데코레이터 클래스의 형식은 그 클래스가 감싸고 있는 클래스의 형식을 반영합니다.(상속 또는 인터페이스 구현을 통해서 자신이 감쌀 클래스와 같은 형식을 가지게 됩니다)
- 데코레이터에서는 자기가 감싸고 있는 구성요소의 메소드를 호출한 결과에 새로운 기능을 더함으로써 행동을 확장합니다.
- 구성요소를 감싸는 데코레이터의 개수에는 제한이 없습니다.
- 구성요소의 클라이언트 입장에서는 데코레이터의 존재를 알 수 없습니다.
  - 클라이언트에서 구성요소의 구체적인 형식에 의존하게 되는 경우에는 적합하지 않다.  
- 데코레이터 패턴을 사용하면 자잘한 객체들이 매우 많이 추가될 수 있고, 데코레이터를 너무 많이 사용하면 코드가 필요 이상으로 복잡해질 수도 있습니다.

## 팩토리 패턴(Factory Pattern)
- 모든 팩토리 패턴에서는 객체 생성을 캡슐화합니다.
- 팩토리 메소드 패턴에서는 서브클래스에서 어떤 클래스를 만들지를 결정하게 함으로써 객체 생성을 캡슐화합니다.
- 추상 팩토리 패턴에서는 인터페이스를 이용하여 서로 연관된, 또는 의존하는 객체를 구상 클래스를 지정하지 않고도 생성할 수 있습니다. 클라이언트에서
추상 인터페이스를 통해서 일련의 제품들을 공급받을 수 있습니다.
```
팩토리 메소드 vs 추상 팩토리
1 . 팩토리 메소드
  - 서브 클래스를 통해서 객체생성.
  - 클라이언트 코드와 인스턴스를 만들어야 할 구상 클래스를 분리시켜야 할 때 사용.
  - 어떤 구상 클래스를 필요로 하게 될지 미리 알 수 없는 경우에도 매우 유용. 

2. 추상 팩토리
  - 객체 구성(composition)을 사용. '제품군'을 만들기 위한 추상 형식을 제공. 제품 생산 방법은 서브 클래스에서 정의.
    객체 생성이 팩토리 인터페이스에서 선언한 메소드들에서 구현됨.
  - 클라이언트에서 서로 연관된 일련의 제품들을 만들어야 할 때, 즉 제품군을 만들어야 할 때 활용.

공통점 
- 클라이언트와 클라이언트에서 사용하는 실제 구상 제품을 분리시켜 줌. => 객체 생성을 캡슐화해서 애플리케이션의 결합을 느슨하게 만들고,
  특정 구현에 덜 의존하도록 만듦.
``` 

## 싱클턴 패턴(Singleton Pattern)
- 해당 클래스의 인스턴스가 하나만 만들어지고, 어디서든지 그 인스턴스에 접근할 수 있도록 하기 위한 패턴이다.
- 객체 중에는 사실 하나만 있으면 되는 것들이 많다. ex) 스레드 풀, 캐시, 레지스트리 설정, 로그, 프린터 등의 디바이스를 위한 드라이버...
- 전역변수와 다른점?
  - 전역 변수에 객체를 대입하면 애플리케이션이 시작될 때 객체가 생성될 것이다.(*플랫폼에 따라 다를 수 있음) 하지만 애플리케이션이 끝날 때까지 그 객체를 한 번도 쓰지 않는다면?
  - 싱글턴 패턴을 쓰면 필요할 때만 객체를 만들 수 있다.
  - 전역 변수를 사용하다 보면 간단한 객체에 대한 전역 레퍼런스를 자꾸 만들게 되면서 네임스페이스가 지저분해지는 경향이 있다.
- 클래스 로더가 여러개인 경우 싱슬턴의 인스턴스도 여러개 만들어지는 문제가 발생할 수 있다.

## 커맨드 패턴(Command Pattern)
- 커맨드 패턴을 이용하면 요구 사항을 객체로 캡슐화할 수 있으며, 매개변수를 써서 여러 가지 다른 요구 사항을 집어넣을 수도 있습니다.
- 또한 요청 내역을 큐에 저장하거나 로그로 기록할 수도 있으며, 작업 취소 기능도 지원 가능합니다.
- 프로그래밍을 하다 보면 요청 자체를 리시버한테 넘기지 않고 지가기 처리하는 "스마트" 커맨드 객체를 사용하는 경우도 종종 있습니다.
- 커맨드 패턴을 활용하여 로그 및 트랜잭션 시스템을 구현하는 것도 가능합니다.

## 어댑터 패턴(Adapter Pattern)
- 한 클래스의 인터페이스를 클라이언트에서 사용하고자 하는 다른 인터페이스로 변환합니다. 어댑터를 이용하면 인터페이스 호환성 문제 때문에 같이 쓸 수 없는 클래스들을 연결해서 쓸 수 있습니다.
- 클라이언트에서 어댑터를 사용하는 방법
  1. 클라이언트에서 타겟 인터페이스를 사용하여 메소드를 호출함으로써 어댑터에 요청합니다.
  2. 어댑터(adapter)에서는 어댑티(adaptee) 인터페이스를 사용하여 그 요청을 어댑티(adaptee)에 대한 (하나 이상의) 메소드 호출로 변환합니다.
  3. 클라이언트에서는 호출 결과를 받긴 하지만 중간에 어댑터가 껴 있는지는 전혀 알지 못합니다.
  
```
Q: 어댑터에서 얼마나 적응을 시켜줘야 하나요? 대형 타겟 인터페이스를 구현해야 되는 경우에는 할 일이 정말 많아질 수 있을 것 같은데요?
A: 예, 그럴 수도 있습니다. 하지만 다른 대안이 있는지 한번 생각해보세요. 그냥 모든 변경 사항을 캡슐화시킨 클래스 한 개만 제공하는 방법이 베스트일지도?

Q: 한 어댑터에서 한 클래스만 감싸야 하나요?
A: 한 어댑터에서 타겟 인터페이스를 구현하기 위해 두 개 이상의 어댑티를 감싸야 하는 상황도 생길 수 있습니다. -> 사실 이런 내용은 퍼사드 패턴이라는 또 다른 패턴하고 연관되어 있습니다.
```
- 클래스 어댑터
  - 클래스 어탭터 패턴을 쓰려면 다중 상속이 필요합니다.
  - 어댑티를 적응시키는 데 있어서 구성을 사용하는 대신, 어댑터를 어댑티와 타겟 클래스 모두의 서브 클래스로 만듭니다.
  
## 퍼사드 패턴(Facade Pattern)
- 퍼사드는 인터페이스를 단순화시킬 뿐 아니라 클라이언트와 구성요소들로 이루어진 서브시스템을 분리시키는 역할도 합니다.
- 어떤 서브시스템에 대한 간단한 인터페이스를 제공하기 위한 용도로 쓰입니다.
- 퍼사드 패턴을 사용하려면 어떤 서브시스템에 속한 일련의 복잡한 클래스들을 단순화하고 통합한 클래스를 만들어야 합니다.
- 다른 패턴과 달리 상당히 단순한 편입니다.(복잡한 추상화 같은 게 필요 없죠.)
- 퍼사드 패턴을 이용하면 클라이언트와 서브시스템이 서로 긴밀하게 연결되지 않아도 됩니다.

### 데코레이션 vs 어댑터 vs 퍼사드
- 데코레이터는 객체를 감싸서 새로운 행동을 추가하기 위한 용도
- 어댑터는 객체를 감싸서 인터페이스를 바꾸기 위한 용도
- 퍼사드는 일련의 객체들을 감싸서 단순화시키기 위한 용도

# 디자인 원칙
## OCP(Open-Closed Principle)
- 클래스는 확장에 대해서는 열려 있어야 하지만 코드 변경에 대해서는 닫혀 있어야 한다.
## Dependency Inversion Principle
- 추상화된 것에 의존하도록 만들어라. 구상 클래스에 의존하지 않도록 한다.
- 가이드 라인
  - 어떤 변수에도 구상 클래스에 대한 레퍼런스를 저장하지 않는다.
  - 구상 클래스에서 유도된 클래스를 만들지 않는다.
  - 베이스 클래스에 이미 구현되어 있던 메소드를 오버라이드하지 않는다. => 이미 구현되어 있는 메소드를 오버라이드한다는 것은 애초부터 베이스 클래스가 제대로 추상화된 것이 아니었다고 볼 수 있습니다.
## 최소 지식 원칙(= 데메테르의 법칙(Law of Demeter))
- 객체 사이의 상호작용은 될 수 있으면 아주 가까운 "친구" 사이에서만 허용하는 것이 좋다.
  - 시스템을 디자인 할 때, 어떤 객체든 그 객체와 상호작용을 하는 클래스의 개수에 주의해야 한다.
  - 이 원칙을 잘 따르면 여러 클래스들이 복잡하게 얽혀서 시스템의 한 부분을 변경했을 때 다른 부분까지 줄줄이 고쳐야 되는 상황을 미리 방지할 수 있습니다.
- 가이드라인
  - 어떻게 하면 여러 객체하고 인연을 맺는 것을 피할 수 있을까요? 어떤 메소드에서든지 다음 네 종류의 객체의 메소드만을 호출하면 됩니다.
    - 객체 자체
    - 메소드에 매개변수로 전달된 객체
    - 그 메소드에서 생성하거나 인스턴스를 만든 객체
    - 그 객체에 속하는 구성요소(인스턴스 변수에 의해 참조되는 객체)
- 단점
  - 이 원칙을 잘 따르면 의존성을 줄일 수 있지만, 다른 구성요소에 대한 메소드 호출을 처리하기 위해 래퍼 클래스를 더 만들어야 할 수도 있습니다. ==> 복잡도, 개발시간 증가, 성능 저하
```
Q: 어떤 메소드를 초훌찬 결과로 리턴받은 객체에 있는 메소드를 호출할 때는 어떤 단점이 있을까요?
A: 그렇게 하면 다른 객체의 일부분에 대해서 요청을 하게 되는 것이고, 그러다 보면 직접적으로 알고 지내는 객체의 개수가 늘어나게 됩니다.
   ==> 그런 경우에 최소 지식 원칙을 따르려면 그 객체 쪽에서 대신 요청을 하도록 만들어야 합니다. 그러면 그 객체의 한 구성요소를 알고 지낼 필요도 없어지죠.(친구 수를 줄이는 데도 도움이 되고요)
   
   // 원칙을 따르지 않은 경우
   // station으로부터 Thermometer라는 객체를 받은 다음, 그 객체의 getTemperature() 메소드를 직접 호출합니다.
   public float getTemp() {
     Thermometer thermometer = station.getThermometer();
     return thermometer.getTemperature();
   }
   
   // 원칙을 따르는 경우
   public float getTemp() {
     return station.getTemperature(); // 최소 지식 원칙을 적용하여 Station 클래스에 thermometer에 요청을 해주는 메소드를 추가했습니다. 이렇게 하면 의존해야 하는 클래스의 개수를 줄일 수 있죠.
   }
```
```
  public class Car {
    Engine engine;
    // ... 기타 인스턴스 변수
    
    public Car() {
      // 엔진 초기화 등 인스턴스 변수 초기화 처리
    }
    
    public void start(Key key) {
      Doors doors = new Doors();
      boolean authorized = key.turns(); // 매개변수로 전달된 객체의 메소드 호출 : OK
      
      if (authorized) {
        engine.start(); // 이 객체의 구성요소의 메소드 호출 : OK
        updateDashboardDisplay(); // 객체 내에 있는 메소드 호출 : OK
        doors.lock(); // 직접 생성하거나 인스턴스를 만든 객체의 메소드 : OK
      }
    }
    
    public void updateDashboardDisplay() {
      // 디스플레이 갱신
    }
  }

```
  