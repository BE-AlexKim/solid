# 단일책임원칙 (SRP)

### SRP ( Single Responsebility Principle ) 단일 책임 원칙이란?
#### SRP는 SOLID 원칙 중 하나로, "하나의 클래스는 단 하나의 책임만 가져야 한다" 는 개념입니다. 즉, 한 클래스가 변경되는 이유는 단 하나뿐이어야 합니다.

🚀 SRP 적용 전: 단일 클래스에 여러 책임이 있는 경우  
먼저, SRP를 위반하는 코드를 작성해 보겠습니다.  
```
package com.example.srp

import org.springframework.stereotype.Service

data class User(val id: Long, val name: String, val email: String)

@Service
class UserService {

    private val users = mutableListOf<User>()

    // 1️⃣ 사용자 추가 기능
    fun addUser(user: User) {
        users.add(user)
        sendWelcomeEmail(user) // ❌ SRP 위반 (비즈니스 로직 + 이메일 전송 로직 혼합)
    }

    // 2️⃣ 사용자 목록 조회 기능
    fun getUsers(): List<User> {
        return users
    }

    // 3️⃣ 이메일 전송 기능 (책임이 다름)
    private fun sendWelcomeEmail(user: User) {
        println("Sending welcome email to ${user.email}")
    }
}
```
❌ 문제점:  
UserService 클래스가 사용자 관리와 이메일 전송 두 가지 역할을 수행합니다.  
비즈니스 로직(User 관리)과 인프라 로직(이메일 전송)이 섞여 있어 변경이 어렵고 확장성이 낮음.

✅ SRP 적용 후: 역할 분리
이제 SRP 원칙을 준수하여 UserService와 EmailService를 분리해 보겠습니다.
```
package com.example.srp

import org.springframework.stereotype.Service

data class User(val id: Long, val name: String, val email: String)

// 📌 사용자 관리 책임 (UserService)
@Service
class UserService(private val emailService: EmailService) {

    private val users = mutableListOf<User>()

    // 사용자 추가 기능 (이메일 전송은 EmailService가 담당)
    fun addUser(user: User) {
        users.add(user)
        emailService.sendWelcomeEmail(user) // ✅ SRP 준수 (각 클래스가 하나의 책임만 가짐)
    }

    fun getUsers(): List<User> {
        return users
    }
}

// 📌 이메일 전송 책임 (EmailService)
@Service
class EmailService {
    fun sendWelcomeEmail(user: User) {
        println("📧 Sending welcome email to ${user.email}")
    }
}
```
✅ 개선된 점  
UserService는 사용자 관리만 담당하고, EmailService는 이메일 전송만 담당합니다.  
UserService에서 이메일 전송 로직을 분리했기 때문에, 이메일 전송 방식이 변경되어도 UserService에 영향을 주지 않음.  
각 클래스의 역할이 명확해져 테스트와 유지보수가 쉬워짐.  
