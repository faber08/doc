# 코틀린 개요

```kotlin
data class Person(val name:String,  // 데이터 클래스
                 val age: Int? = null) // nullable 값과 파라미터 디폴트값

fun main(args: Array<String>) {
    val persons = listOf(Person("영희"),
                         Person("철수", age=29))  // 이름 붙인 파라미터
    val oldest = persons.maxBy {it.age ?: 0}  // 람다식, 엘비스 연산자
    println("나이가 가장 많은 사람: $oldest")   // 문자열 템플릿
}
```
```
나이가 가장 많은 사람: Person(name=철수, age=29)
```

### 특징 : 정적언어 

정적언어이지만 타입추론이 가능하다. `var x = 1 // 타입지정 생략`

정적언어의 장점
- 성능 
- 신뢰성 : 컴파일러가 검사해준다.
- 유지보수성 : 객체가 어떤 타입인지 알 수 있다.
- 도구지원 : 리팩토링, 자동완성등


### 특징 : 함수형 프로그램밍

특징
- first-class 함수 : 함수를 값처럼 다룰 수 있으며 인자로 전달할 수도 있고 반환값으로도 사용가능하다.
- 불변성 : 
- 부수효과 없음 : 같은 입력에 같은 출력을 내놓는다.

장점
- 간결성  
  다른 부분만 람다로 뽑아서 추상화하기 쉽다.  
  `fun findAlice() = findPerson { it.name == "Alice" }`  
  `fun findBob() = findPerson { it.name == "Bob" }`
- 다중쓰레드에 대해서 안전
- 부수효과가 없으므로 테스트하기 쉬움

### 코틀린과 자바 호환

자바 6 이후로 호환

성능

- 코틀린 런타임이 작으므로 애플리케이션 크기가 크게 늘어나지 않음
- 람다는 대부분 컴파일시 inline 처리하기 때문에 객체 증가로 인한 GC를 걱정하지 않아도 됨

