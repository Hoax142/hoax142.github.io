---
title: Swift) 2. 변수, 상수, 자료형
author: Henry Oh
date: 2021-05-08 08:20:00 +0900
categories: [Swift, Grammer]
tags: [Swift, Int, UInt, Double, Float, Character, String, Any, AnyObject, Nil]
image:
  src: https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/0.swift5.png
---


<span style="color: #0281C3">
안녕하세요. Hoax142입니다~  저번 포스트에서 말씀드린 대로 변수와 상수란 무엇이고, Swift에는 어떤 자료형들이 있는지에 대해 살펴보도록 하겠습니다. 제 나름대로 정리를 했는데, 혹시 잘못된 부분이 있으면 댓글을 통해 알려주시면 최대한 빠르게 수정하도록 하겠습니다. (해당 글은 swift 5.4 버젼을 기준으로 작성했습니다.)
</span>

<br><br>
## 변수와 상수

변수(variable)는 값을 수정할 수 있고, 상수(constant)는 값을 수정할 수 없습니다. 애플은 언제 어디서 바뀔지 모르는 변수보다는 상수를 사용하는 것을 권장해줍니다.  

변수는 `var` 키워드로, 상수는 `let` 키워드로 선언을 합니다.
```swift
var aVariable = 50 // 값 변경이 가능한 변수
let aConstant = 50 // 값 변경이 불가능한 상수
```

변수는 나중에 값을 변경해야 한다면 다음과 같이 변경할 수 있습니다.

```swift
aVariable = 100
```

상수는 값을 변경하려 하면 컴파일 에러가 발생합니다.

```swift
aConstant = 100 // 컴파일 에러
```
![let Compile Error](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/1.let_error.png){: width="500" .left}  
<br><br><br>
>Cannot assign to value: 'aConstant' is a let constant  

`let` 키워드로 선언된 상수 값을 변경할 수 없다는 에러입니다.

<br>

## 변수/상수 선언 방법

Swift는 정적 타이핑 언어입니다. 쉽게 말해서 상수(변수)를 정의할 때 그 자료형(타입)이 무엇인지 명시해주어야 한다는 겁니다. 상수(변수)를 선언하는 방법은 아래와 같습니다.

- **let  (상수명):  (타입)  =  (값)**  
상수(변수) 선언과 동시에 타입과  값을 선언해 줄 수 있습니다.

```swift
let aConstant: Int = 10
```
<br>

- **var  (변수명)  =  (값)**  
상수(변수)를 초기화하지 않고 선언할 때 타입을 명시해주지 않으면 오류가 발생합니다. 하지만 스위프트는 *타입추론*을 할 수 있습니다. 타입추론이란 스위프트에서 상수(변수)가 선언될 때 초기화되는 값을 보고 컴파일러가 생성된 타입을 추론하여 지정해주는 것입니다.

```swift
var aVariable = 20

var b Variable //	컴파일 오류
```
<br>
- **let  (상수명):  (타입)**  
상수(변수)와 타입만 선언해 주고 값은 프로그래밍하다가 나중에 필요할 때 선언해 줄 수 있습니다. 

```swift
let aConstant: Int

aConstant = 10
```



### 주의해야 할 점
타입추론이 가능 하더라도, 상수(변수) 선언과 동시에 초기화 해주지 않으면 컴파일러는 타입을 추론해주지 못합니다. 이럴 땐 꼭 타입을 명시해줘야 오류가 나지 않습니다.

![Initialize Error](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/3.annotation_missing_error.png){: width="500" .left}  
<br>

>Type annotation missing in pattern

Type annotation이란 ": (타입)" 을 뜻합니다. 즉, 어떤 타입인지 지정해주지 않아서 발생하는 에러입니다.

상수(변수)를 선언만 하고 초기화 하지 않은 상태에서 값을 출력하려고 하면 오류가 발생합니다. C나 Java같은 다른 언어에서는 이렇게 하면 자동으로 null 값이 출력 되지만, 스위프트에서는 값을 nil로 초기화하지 않거나 선언을 옵셔널로 하지 않으면 컴파일 에러가 발생합니다.

> 옵셔널에 관해서는 나중에 따로 다루도록 하겠습니다.  

```swift
var aVariable: Int

print(aVariable) // 컴파일 에러
```

![Initialize Error](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/2.initialize_error.png){: width="500" .left}
<br><br><br>

>Variable 'aVariable' used before initialized

변수가 초기화 되기 전에 사용되었다는 오류입니다.

<br>

## 데이터 타입

 그럼 Swift에는 어떤 자료형들이 있을까요?


### Bool

true와 false 값만 가지는 타입입니다. 
```swift
var aBool = true
let bBool = false
```

### Int & UInt

정수 타입입니다. Int는 +, - 를 포함한 정수이며 UInt는 + 값만 가지는, 즉 양의 정수만 표현할 수 있습니다.  
Int와 Uint형의 최대값과 최소값은 각각 max와 min 프로퍼티를 통해 확인 할 수 있습니다.  
Int와 UInt는 각각 8비트, 16비트, 32비트, 64 비트의 형태를 가지고 있습니다.

```swift
var aInteger: Int = -100
let aUnsignedInteger: UInt = 100

Int.max // 9223372036854775807
Int.min // -9223372036854775808

UInt.max // 18446744073709551615
UInt.min // 0
```

### Double & Float

부동소수점을 사용하는 실수이며 부동소수 타입이라고 합니다. 우리가 흔히 이야기하는 소수점 자리가 있는 수 입니다.  
Double은 64비트의 부동소수를 표현할 수 있고 Float는 32 비트를 표현할 수 있습니다.  
64비트 환경에서 Double은 최소 15자리의 소수점을, Float은 6자리까지만 표햔이 가능합니다.   
상황에 맞게 둘 중 하나를 선택하여 사용하면 되는데, 잘 모르겠으면 애플은 Double을 권장합니다.

```swift
let aDouble: Double = 10.12345678987654321
let aFloat: Float = 10.123456789

let bDouble: Double = 1.12345678987654321

print(aDouble) // 10.123456789876544
print(bFloat)  // 10.123457

print(bDouble) // 1.1234567898765433
```

### Character

Character는 말 그래도 '문자'를 의미합니다.   
단어나 문장처럼 문자의 집합이 아닌 단 하나의 문자를 의미합니다.  
스위프트는 유니코드 문자를 사용하므로 영어 뿐만 아니라 [유니코드](https://unicode-table.com/kr/)에서 지원하는 모든 언어 및 특수기호 등을 사용할 수 있습니다.   
문자를 표현하기 위해서는 큰 따옴표(" ")를 사용합니다.
```swift
let aChar: Character = "A"
let bChar: Character = "가"
let cChar: Character = "😎"
```

### String

String은 문자열입니다.  
String은 Character와 마찬가지로 유니코드를 사용할 수 있으며 큰 따옴표(" ")를 사용합니다.
```swift
let aString: String = "Hello World"
let bString: String = "안녕하세요"
let cString: String = "ἀπατάω"
```

### Any

Any는 말 그대로 '어떤'을 의미합니다.  
Any를 이용하면 상수 혹은 변수를 초기화 할 때 정수 값, 문자열 값 등 그 어떤 값을 집어 넣을 수 있습니다.  
(단 상수는 한 번 값을 할당하면 변경이 안됩니다.)
```swift
var aAny: Any = 100
aAny = "어떤 타입이든 상관 없습니다."
aAny = 123.456

let bAny: Any
bAny = "얘도 어떤 타입이 들어와도 상관없습니다." // 변경이 불가능합니다.
```

### AnyObject

모든 클래스 타입을 지칭하는 프로토콜입니다.  
>클래스와 프로토콜은 나중에 따로 다루도록 하겠습니다.  

```swift
class AClass {}

var aAnyObject: AnyObject = AClass()
```

### Nil

아무것도 없다는 것을 의미합니다.  
C언어나 Java에서 사용하는 NULL, null과 비슷합니다.
>자세한 내용은 나중에 따로 다루도록 하겠습니다.

```swift
var nothing: Int = nil

print(nothing) // nil
```

<br><br>
<span style="color: #0281C3"> 이상으로 변수와 상수란 무엇이고, Swift에는 어떤 자료형들이 있는지에 대해 살펴봤습니다. 다음에는 배열에 대해 포스팅해 보겠습니다.</span>
