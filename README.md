# solid
해당 공부는 SOLID 원칙을 공부하기 위해서 생성하였습니다.
참조(https://f-lab.kr/insight/solid-principles-and-object-oriented-design?gad_source=1&gclid=Cj0KCQiAwtu9BhC8ARIsAI9JHalcUXNyORemtSI5G7kwVxPZ9I_xeWMEkZw9vFFIsfeV0CGYPexG1fMaAs6gEALw_wcB)

객체지향 설계의 핵심: SOLID 원칙
객체지향 설계의 핵심을 이루는 SOLID 원칙에 관하여 깊이 있게 다루어 보려고 한다.
SOLID 원칙은 객체지향 프로그래밍 및 설계의 기본이 되는 원칙들로서, 이를 잘 이해하고 적용하는 것은 효율적이고 유지보수가 용이한 소프트웨어 개발로 이끈다.

이번 글에서는 SOLID 원칙의 각 요소에 대해 설명하고, 특히 상속과 추상화의 관계, 그리고 이를 잘못 사용했을 때의 문제점에 대해 심층적으로 다루겠다.
소프트웨어 설계에 있어 필수적인 이 원칙들을 통해 개발자는 더 나은 코드를 작성할 수 있다.

SOLID 원칙이란?
SOLID 원칙은 Robert C. Martin에 의해 소개되었으며, 다음과 같은 다섯 가지 원칙으로 이루어져 있다.

단일 책임 원칙 (SRP, Single Responsibility Principle)
개방-폐쇄 원칙 (OCP, Open-Closed Principle)
리스코프 치환 원칙 (LSP, Liskov Substitution Principle)
인터페이스 분리 원칙 (ISP, Interface Segregation Principle)
의존관계 역전 원칙 (DIP, Dependency Inversion Principle)
이 원칙들을 이해하고 적용함으로써 개발자는 코드의 유연성, 확장성, 유지보수성을 크게 향상시킬 수 있다.
또한, 이 원칙들은 서로 긴밀하게 연관되어 있으며, 이를 통해 객체지향 설계의 모범 사례를 구현할 수 있다.

1. 단일 책임 원칙 (SRP)
**단일 책임 원칙(Single Responsibility Principle)**은 클래스가 오직 하나의 책임만을 가져야 한다는 원칙이다.
여기서 책임이란 변경의 이유를 의미한다. 즉, 클래스가 여러 개의 이유로 변경되어야 한다면, 이는 SRP를 위반한 것이다.

❌ SRP 위반 예제
예를 들어, 사용자 정보를 관리하는 클래스가 다음과 같은 기능을 포함한다고 가정하자.

java
복사
편집
public class UserManager {
    public void getUserInfo() {
        // 사용자 정보 조회
    }

    public void validateLogin() {
        // 로그인 검증
    }
}
위 코드에서 UserManager 클래스는 사용자 정보 조회와 로그인 검증이라는 두 가지 책임을 가진다.
즉, 이 클래스는 두 개의 변경 이유를 가지므로 SRP를 위반한다.

✅ SRP 준수 예제
SRP를 준수하려면, 각 기능을 별도의 클래스로 분리해야 한다.

java
복사
편집
public class UserService {
    public void getUserInfo() {
        // 사용자 정보 조회
    }
}

public class AuthService {
    public void validateLogin() {
        // 로그인 검증
    }
}
이제 UserService는 사용자 정보 조회만 담당하고, AuthService는 로그인 검증만 담당한다.
이렇게 하면 응집도가 높아지고 결합도는 낮아져 유지보수가 쉬워진다.

✅ SRP를 지켜야 하는 이유
변경이 발생할 경우, 특정 기능에만 영향을 미친다.
→ 예를 들어, 로그인 검증 로직이 변경되더라도 사용자 정보 조회 기능에는 영향을 주지 않는다.
응집도가 높아지고 결합도가 낮아진다.
→ 하나의 클래스가 하나의 역할만 수행하기 때문에 유지보수와 확장이 쉬워진다.
소프트웨어의 품질을 향상시킨다.
→ 코드의 가독성이 높아지고, 버그 발생 가능성이 줄어든다.

개방-폐쇄 원칙(OCP)
**개방-폐쇄 원칙(Open/Closed Principle)**은 소프트웨어의 구성 요소(클래스, 모듈, 함수 등)는 확장에는 열려 있어야 하며, 수정에는 닫혀 있어야 한다는 원칙이다.
즉, 기존의 코드를 변경하지 않으면서 기능을 추가할 수 있어야 한다.

예를 들어, 특정 클래스에 새로운 기능을 추가하기 위해 해당 클래스의 코드를 직접 수정하는 것은 OCP 위반이다.
대신, 인터페이스나 추상 클래스를 활용하여 확장성을 갖춘 설계를 도모할 수 있다.

✅ OCP를 준수하는 이유
변경의 영향을 최소화
→ 새로운 기능을 추가하더라도 기존 코드에는 영향을 주지 않는다.
유연한 시스템 구축 가능
→ 확장이 쉬워지고 유지보수가 용이해진다.
소프트웨어의 유지보수성과 재사용성 향상
→ 기존 코드 수정 없이 새로운 요구사항을 반영할 수 있다.
리스코프 치환 원칙(LSP)
**리스코프 치환 원칙(Liskov Substitution Principle)**은
서브타입은 언제나 그것의 베이스 타입으로 교체할 수 있어야 한다는 원칙이다.
즉, 서브클래스는 기반 클래스의 기능을 깨뜨리지 않고 확장할 수 있어야 한다.

❌ LSP 위반 사례
예를 들어, 직사각형(Rectangle) 클래스를 상속받아 정사각형(Square) 클래스를 만든다고 가정하자.

java
복사
편집
class Rectangle {
    protected int width;
    protected int height;

    public void setWidth(int width) { this.width = width; }
    public void setHeight(int height) { this.height = height; }

    public int getArea() { return width * height; }
}
정사각형은 가로와 세로 길이가 항상 같아야 하므로, 아래와 같이 구현할 수 있다.

java
복사
편집
class Square extends Rectangle {
    public void setWidth(int width) {
        super.setWidth(width);
        super.setHeight(width);
    }

    public void setHeight(int height) {
        super.setWidth(height);
        super.setHeight(height);
    }
}
이제 Rectangle을 기대하는 코드에서 Square를 사용하면 예상과 다르게 동작할 가능성이 크다.
즉, setWidth()나 setHeight()를 호출했을 때 의도하지 않은 동작이 발생한다면 LSP를 위반한 것이다.

✅ LSP를 준수하는 이유
코드의 재사용성과 유연성 증가
→ 서브클래스를 기반 클래스처럼 사용할 수 있어야 한다.
예상치 못한 동작 방지
→ 올바른 상속 구조를 유지하면 예측 가능한 동작을 보장할 수 있다.
객체 지향적인 올바른 계층 구조 형성
→ 클래스 간의 관계가 명확해지고 유지보수가 쉬워진다.
