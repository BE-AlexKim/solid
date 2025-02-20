# SOLID 원칙
# 해당 공부는 SOLID 원칙을 공부하기 위해서 생성하였습니다.

## SOLID 원칙에 대해서 아래에 링크에 잘 정리된 내용을 가져왔습니다.
## [SOLID 원칙과 객체지향 설계](https://f-lab.kr/insight/solid-principles-and-object-oriented-design?gad_source=1&gclid=Cj0KCQiAwtu9BhC8ARIsAI9JHalcUXNyORemtSI5G7kwVxPZ9I_xeWMEkZw9vFFIsfeV0CGYPexG1fMaAs6gEALw_wcB)

# SOLID 원칙

개요

객체지향 설계의 핵심을 이루는 SOLID 원칙에 관하여 깊이 있게 다루어 보려고 한다. SOLID 원칙은 객체지향 프로그래밍 및 설계의 기본이 되는 원칙들로서, 이를 잘 이해하고 적용하는 것은 효율적이고 유지보수가 용이한 소프트웨어 개발로 이끈다.

이번 글에서는 SOLID 원칙의 각 요소에 대해 설명하고, 특히 상속과 추상화의 관계, 그리고 이를 잘못 사용했을 때의 문제점에 대해 심층적으로 다루겠다. 소프트웨어 설계에 있어 필수적인 이 원칙들을 통해 개발자는 더 나은 코드를 작성할 수 있다.

SOLID 원칙은 Robert C. Martin에 의해 소개되었으며, 다음과 같은 다섯 가지 원칙으로 이루어져 있다:

### 단일 책임 원칙(SRP)

### 개방-폐쇄 원칙(OCP)

### 리스코프 치환 원칙(LSP)

### 인터페이스 분리 원칙(ISP)

### 의존관계 역전 원칙(DIP)

이 원칙들을 이해하고 적용함으로써 개발자는 코드의 유연성, 확장성, 유지보수성을 크게 향상시킬 수 있다. 이 원칙들은 서로 긴밀하게 연관되어 있으며, 이를 통해 객체지향 설계의 모범 사례를 구현할 수 있다.

# 1. 단일 책임 원칙(SRP)

**단일 책임 원칙(Single Responsibility Principle)**은 클래스가 오직 하나의 책임만을 가져야 한다는 원칙이다. 여기서 책임이란 변경의 이유를 의미한다. 클래스가 둘 이상의 책임을 갖게 되면, 코드의 수정이 필요할 때 여러 부분에서 변경이 발생할 수 있어 유지보수가 어려워진다.

예를 들어, 사용자 정보를 관리하는 클래스가 사용자의 정보 조회뿐만 아니라 로그인 검증까지 하게 되면 SRP 위반이다. 왜냐하면 사용자 정보 조회와 로그인 검증은 서로 다른 책임이기 때문이다.

또한 SRP를 준수하면, 응집도가 높아지고 결합도는 낮아진다. 이는 소프트웨어의 품질을 향상시키는 핵심 요소이다.

왜냐하면 변경이 발생할 경우, 해당 변경은 특정 기능에 국한되며, 그로 인해 다른 기능에 영향을 미치지 않아 유지보수성이 좋아지기 때문입니다.

SRP는 객체지향 설계의 기본이 되는 원칙으로, 소프트웨어의 복잡성을 관리하는 데 중요한 역할을 한다.

# 2. 개방-폐쇄 원칙(OCP)

**개방-폐쇄 원칙(Open/Closed Principle)**은 소프트웨어의 구성요소(클래스, 모듈, 함수 등)는 확장에는 열려 있어야 하며, 수정에는 닫혀 있어야 한다는 원칙이다. 즉, 기존의 코드를 변경하지 않으면서 기능을 추가할 수 있어야 한다.

예를 들어, 특정 클래스에 새로운 기능을 추가하기 위해 해당 클래스의 코드를 수정하는 것은 OCP 위반이다. 대신, 인터페이스나 추상 클래스를 활용하여 확장성을 갖춘 설계를 도모할 수 있다.

이 원칙을 적용하면, 시스템은 더 유연하고 변경에 대한 영향을 최소화할 수 있다.

왜냐하면 새로운 기능을 추가하거나 요구사항이 변경될 때 기존의 코드를 수정하지 않고도, 확장을 통해 요구사항을 충족시킬 수 있기 때문입니다.

OCP는 소프트웨어의 유지보수성과 재사용성을 크게 향상시키는 중요한 원칙 중 하나이다.

# 3. 리스코프 치환 원칙(LSP)

**리스코프 치환 원칙(Liskov Substitution Principle)**은 서브타입은 언제나 그것의 베이스 타입으로 교체할 수 있어야 한다는 원칙이다. 즉, 서브클래스는 기반 클래스의 기능을 깨뜨리지 않고 확장할 수 있어야 한다.

이 원칙이 위배되는 경우, 상속 구조가 잘못 설계되었음을 의미한다. 예를 들어, 직사각형 클래스를 상속받아 정사각형 클래스를 만든 경우, 직사각형으로 사용될 때와 똑같이 동작하지 않는다면 LSP 위반이다.

LSP를 준수하면, 코드의 재사용성과 유연성이 증가한다.

왜냐하면 서브클래스를 베이스 클래스의 객체로 안전하게 대체할 수 있어 기존 코드를 변경하지 않고도 확장할 수 있기 때문입니다.

LSP는 타입 계층구조에서의 상속 관계를 설계할 때 중요한 지침을 제공한다.

# 4. 인터페이스 분리 원칙(ISP)

**인터페이스 분리 원칙(Interface Segregation Principle)**은 클라이언트는 자신이 사용하지 않는 메서드에 의존하면 안 된다는 원칙이다. 즉, 하나의 큰 인터페이스보다는 구체적인 여러 개의 인터페이스가 낫다는 것이다.

큰 인터페이스 하나에 모든 것을 담기보다는, 필요한 기능만을 갖는 작은 인터페이스 여러 개로 분리하는 것이 바람직하다.

이렇게 하면, 클라이언트는 자신에게 필요하지 않은 의존성으로부터 자유로워질 수 있다.

왜냐하면 클라이언트는 필요한 기능만을 제공하는 인터페이스에만 의존하게 되므로, 불필요한 변경으로부터 보호받을 수 있기 때문입니다.

ISP는 인터페이스를 설계할 때 클라이언트의 필요를 정확히 반영하여 필요한 것만을 제공하는 것이 중요하다는 점을 강조한다.

# 5. 의존관계 역전 원칙(DIP)
🌟 DIP (Dependency Inversion Principle, 의존 역전 원칙)란?
DIP는 SOLID 원칙 중 하나로, "고수준 모듈은 저수준 모듈에 의존해서는 안 된다. 대신, 둘 다 추상화에 의존해야 한다." 는 원칙입니다.

즉, 고수준의 비즈니스 로직이 저수준의 구현에 의존하지 않고, 추상화된 인터페이스나 클래스에 의존해야 한다는 의미입니다.
이 원칙을 통해 유연하고 변경에 강한 시스템을 만들 수 있습니다.

🌱 DIP 원칙의 두 가지 핵심:
고수준 모듈(비즈니스 로직): 주로 시스템의 중요한 비즈니스 로직을 담당합니다. 예를 들어, PaymentService처럼 결제 처리를 담당하는 클래스가 고수준 모듈이 될 수 있습니다.
저수준 모듈(구현체): 고수준 모듈의 기능을 실제로 수행하는 클래스입니다. 예를 들어, 결제 방식을 처리하는 CreditCardPaymentProcessor, PayPalPaymentProcessor 클래스가 저수준 모듈입니다.
추상화: 고수준 모듈과 저수준 모듈이 인터페이스나 추상 클래스를 통해 연결되어야 합니다. 즉, PaymentProcessor와 같은 인터페이스를 정의하여 두 모듈이 서로 의존하지 않도록 합니다.

🚀 DIP 적용 전: 고수준 모듈이 저수준 모듈에 의존하는 경우
``` package com.example.dip

import org.springframework.stereotype.Service

// 고수준 모듈 (결제 서비스)
@Service
class PaymentService {
    // 저수준 모듈 (결제 처리)
    private val creditCardPaymentProcessor = CreditCardPaymentProcessor()

    fun processPayment(amount: Double) {
        creditCardPaymentProcessor.process(amount)
    }
}

// 저수준 모듈 (결제 처리)
class CreditCardPaymentProcessor {
    fun process(amount: Double) {
        println("💳 Processing credit card payment of $$amount")
    }
}
```
❌ 문제점:
PaymentService는 **직접 CreditCardPaymentProcessor**에 의존하고 있습니다.
PaymentService가 저수준 모듈에 직접 의존하고 있기 때문에, CreditCardPaymentProcessor를 변경하거나 다른 결제 방식을 추가할 때 PaymentService도 수정해야 합니다.
DIP 위반! 고수준 모듈이 저수준 모듈에 의존하고 있기 때문에, 시스템의 확장성과 유연성이 떨어집니다.

✅ DIP 적용 후: 추상화(인터페이스) 도입
DIP를 적용하면, PaymentService가 PaymentProcessor와 같은 추상화된 인터페이스에 의존하게 됩니다. 이제 PaymentService는 구체적인 구현체(CreditCardPaymentProcessor)에 의존하지 않게 됩니다.

📌 1. PaymentProcessor 인터페이스 정의
package com.example.dip

interface PaymentProcessor {
    fun process(amount: Double)
}
📌 2. CreditCardPaymentProcessor, PayPalPaymentProcessor 구현체 정의
package com.example.dip

class CreditCardPaymentProcessor : PaymentProcessor {
    override fun process(amount: Double) {
        println("💳 Processing credit card payment of $$amount")
    }
}

class PayPalPaymentProcessor : PaymentProcessor {
    override fun process(amount: Double) {
        println("💰 Processing PayPal payment of $$amount")
    }
}

📌 3. PaymentService (DIP 준수: PaymentProcessor 인터페이스에 의존)
package com.example.dip

import org.springframework.stereotype.Service

@Service
class PaymentService(private val paymentProcessor: PaymentProcessor) {

    fun processPayment(amount: Double) {
        paymentProcessor.process(amount)
    }
}

PaymentService는 이제 구체적인 PaymentProcessor 구현체에 의존하지 않고, PaymentProcessor 인터페이스에 의존하게 됩니다.
PaymentService는 인터페이스만 알고 있고, 실제 결제 처리 방식은 다양한 PaymentProcessor 구현체에 의해 처리됩니다.

📌 4. PaymentController (컨트롤러에서 DI를 통해 결제 방식 선택)
package com.example.dip

import org.springframework.web.bind.annotation.*

@RestController
@RequestMapping("/payments")
class PaymentController(private val paymentService: PaymentService) {

    @PostMapping
    fun processPayment(@RequestParam amount: Double, @RequestParam processorType: String) {
        when (processorType) {
            "creditCard" -> paymentService.processPayment(amount)
            "paypal" -> {
                val paypalProcessor = PayPalPaymentProcessor()
                PaymentService(paypalProcessor).processPayment(amount)
            }
            else -> throw IllegalArgumentException("Unsupported processor type: $processorType")
        }
    }
}

✅ DIP 적용 후 장점:
고수준 모듈(PaymentService)이 저수준 모듈(CreditCardPaymentProcessor)에 의존하지 않고, 추상화된 PaymentProcessor 인터페이스에 의존하게 되어, 구현체가 변경되거나 확장되어도 PaymentService는 수정할 필요가 없음.
새로운 결제 방식(PayPalPaymentProcessor 등)을 추가할 때 PaymentService를 변경하지 않아도 되므로 유지보수와 확장성이 쉬워짐.
테스트 용이성: PaymentProcessor를 Mocking하여 PaymentService를 테스트할 수 있습니다.

🎯 DIP 원칙의 핵심 요약
고수준 모듈은 저수준 모듈에 의존해서는 안 됩니다.
두 모듈은 추상화된 인터페이스에 의존해야 합니다.
DIP를 준수하면 확장성이 높고, 변경에 유연하며, 테스트가 용이한 시스템을 만들 수 있습니다.

