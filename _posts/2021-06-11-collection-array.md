---
title: Swift) 3-1. 컬렉션 - 배열
author: Henry Oh
date: 2021-06-11 21:10:00 +0900
categories: [Programming Language, Swift]
tags: [Swift, Array, Set, Dictionary]
image:
  src: https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/0.swift5.png
---

<span style="color: #0281C3"> 안녕하세요~ Hoax142 입니다~ 오늘은 컬렉션, 그중에서도 배열에 대해 포스팅을 해보려고 합니다! 제 나름대로 정리를 했는데, 혹시 잘못된 부분이 있으면 댓글을 통해 알려주시면 최대한 빠르게 수정하도록 하겠습니다. (해당 글은 swift 5.4 버젼을 기준으로 작성했습니다.) </span>

<br><br>
## **배열 (Array)**

배열은 순서(인덱스: index)가 있는 값의 모임입니다. 배열 안에는 같은 값이 있을 수 있습니다. 예를 들어 한 배열 안에 3이라는 값이 5개 들어있어도 아무런 문제가 없습니다.

```swift
let array = [3, 3, 3, 3, 3]
```
<br><br>
## **배열 읽기**
```swift
let array = [1, 2, 3, 4, 5]
```
배열 전체를 읽고 싶으면 배열의 이름을 출력하면 됩니다.
```swift
print(array) // [1, 2, 3, 4, 5]
```
그러면 배열 안에 있는 원소를 읽으려면 어떡해야 할까요?  대갈호와 원소의 위치를 이용하면 됩니다. 하지만 조심해야하는것이 있는데, 그건 바로 위 배열의 첫 번째 원소인 1의 자리는 1이 아니라는 것입니다. 배열의 첫 번째 원소는 항상 그 자릿수가 0입니다.
```swift
print(array[1]) // 2
print(array[0]) // 1

print(array[5]) // 컴파일 오류
print(array[4]) // 5
```

![No Element Error](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/8.no_element_error.png){: width="800" .left}  

<br>
> error: Execution was interrupted, reason EXC_BAD_INSTRUCTION  

잘못된 명령을 내려서 오류가 났습니다. `array[5]`의 원소를 출력해달라고 했지만, 그 자리에는 원소가 없기 때문입니다.
<br><br>
## **배열 선언**
<br>
### 비어있는 배열 선언

```swift
var emptyArray1: Array<Int> = []
var emptyArray2: [Int] = []
var emptyArray3= [Int]()
```
비어있는 배열은 이렇게 3가지 방법으로 선언할 수 있습니다. `Int`형 뿐만 아니라 모든 자료형으로 선언을 할 수 있습니다. 하지만 비어있는 배열을 선언할 때 자료형을 명시해주지 않으면 오류가 발생하니 꼭 조심하시길 바랍니다.

```swift
var emptyArray = [] //컴파일 오류
```

![Empty Array Declare Error](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/4.array_empty_declare_error.png){: width="500" .left}  

<br><br>
> Empty collection literal requires an explicit type  

빈 배열을 선언하려면 자료형을 명시해줘야 한다는 에러입니다.
<br>
### 데이터가 있는 배열 선언

```swift
var array1: Array<Int> = [1, 2, 3, 4]
var array2 = Array<Int>(1...4)
var array3: [Int] = [1, 2, 3, 4]
var array4 = [1, 2, 3, 4] // 타입 유추
```

데이터가 있는 배열은 이렇게 4가지 방법으로 선언할 수 있고, 모두 [1, 2, 3, 4]를 리턴합니다. 자료형을 입력하지 않아도 Xcode는 타입 유추를 통해 타입을 알아서 결정할 수 있습니다.

배열은 한번 선언하면 그 타입을 유지해 줘야 합니다. 예를 들어 위에 있는 배열 중 아무거에나 "a"라는 값을 집어넣으려 하면 오류가 발생합니다. 이유는 위 배열들은 모두 `Int`형인데, "a"는 `String`형이기 때문입니다.

```swift
var array1: Array<Int> = [1, 2, 3, 4]
array1.append("a") // 컴파일 오류
```
![Array Type Error](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/5.array_type_error1.png){: width="500" .left}  

<br><br>
> No exact matches in call to instance method 'append'  

"a"를 array1에 추가할 수 없다는 에러입니다.
<br>

또한 이미 타입이 정해진 배열은 타입이 변경되지 않습니다.
```swift
var array4 = [1, 2, 3, 4]  // 배열 array4를 Int형으로 타입 유추
array4 = [] 		   // 배열 초기화
array4.append("a")	   // 컴파일 오류
```
![Array Type Error](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/6.array_type_error2.png){: width="500" .left}  

<br><br><br><br>

그러면 배열은 꼭 하나의 자료형만 가질 수 있냐, 그건 또 아닙니다.
<br>

### 여러 타입을 가진 배열 선언
[Swift) 2. 변수, 상수, 자료형](https://https://hoax142.github.io/posts/swift-var-let-type/)에서 말씀드린 `Any` 자료형을 통해 다양한 값을 가진 배열을 선언할 수 있습니다.

```swift
var anyArray1: [Any] = [1, 2, "a", "b"]
var anyArray2: Array<Any> = [1, true, 3.5, "b"]
```

이렇게 배열의 자료형을 `Any` 타입으로 지정하여 다양한 자료형을 넣어줄 수 있는데, 이때 주의해야 하는 점은 반드시 `Any` 타입을 선언해줘야 한다는 것입니다.

```swift
var array1 = [1, 2, 3.3, "a"] // 컴파일 에러
```

![Array Type Error2](https://cdn.jsdelivr.net/gh/Hoax142/github_assets/blog/swift/7.any_array_error.png){: width="800" .left}  


<br><br><br><br>
> Heterogeneous collection literal could only be inferred to '[Any]'; add explicit type annotation if this is intentional  

다양한 자료형이 들어간 배열을 사용하기 위해 [Any] 타입이라는걸 명시해줘야 한다는 에러입니다.
<br>
### 크기가 정해진 배열 선언

```swift
var threeMaxArray = [String](repeating: "a", count: 3) // ["a", "a", "a"]
var twoMaxArray = Array(repeating: 1, count 2) // [1, 1]
```
<br>
## **배열 수정**
<br>
### 값 추가
```swift
var array = [1, 2, 3] // [1, 2, 3]
array.append(4)   // [1, 2, 3, 4] 
array += [0, 1]   // [1, 2, 3, 4, 0, 1]
```
이렇게 2가지 방법으로 배열에 값을 추가할 수 있습니다. `append` 함수를 통해서 원소 1개, `+=` 연산자를 통해 여러 개의 원소를 추가해줄 수 있습니다. 하지만 이렇게 추가하면 위에 값을 확인하면 알 수 있다 시피 배열의 맨 뒤에 추가가 됩니다. 그러면 원하는 곳에 값을 추가하고 싶으면 어떻게 해야 할까요?
<br>
### 원하는 곳에 값 추가
```swift
var array = [1, 2, 3] // [1, 2, 3]
array.insert(0, at: 0) // [0, 1, 2, 3]
array.insert(5, at: 3) // [0, 1, 2, 5, 3]
````
`insert(at:)`함수를 사용하면 원하는 자리에 원소를 추가할 수 있습니다.

### 값 수정
```swift
var array = [1, 2, 3]
array[0] = 0
print(array) // [0, 2, 3]

array[0...1] // [0, 2]
array[0...1] = [5, 6]
print(array) // [5, 6, 3]
```
직접 자리를 지정하여 값을 변경할 수도 있고, 범위(range)를 지정하여 값을 수정해줄 수도 있습니다. 범위에 대해서는 [Swift) 4. 조건문과 반복문]()에서 더 자세히 다루도록 하겠습니다.

### 값 제거
```swift
var array = [1, 2, 3]
array.remove(at: 1)
print(array) // [1, 3]
```
`remove(at:)`함수를 사용하요 원하는 자리의 원소를 제거해줄 수 있습니다. 이 이외에도 `removeFirst()` 함수를 통해서 첫 번째 원소를 제거해줄수 있고, `removeLast()`, `popLast()` 함수를 통해 마지막 원소를 제거해줄 수 있습니다.

```swift
var array = [1, 2, 3, 4, 5, 6, 7, 8, 9]
array.removeFirst()
print(array) // [2, 3, 4, 5, 6, 7, 8, 9]

array.popLast()
print(array) // [2, 3, 4, 5, 6, 7, 8]

array.removeLast()
print(array) // [2, 3, 4, 5, 6, 7]
```

배열 전체를 초기화 해주고 싶으면 `removeAll()`함수를 사용하거나, 빈 배열을 사용하여 초기화 해줄 수 있습니다.
```swift
var array1 = [1, 2, 3]
var array2 = [4, 5, 6]

array1.removeAll()
array2 = []

print(array1) // []
print(array2) // []
```

### 오름차순, 내림차순
```swift
var array1 = [5, 3, 4, 1, 2]
var array2 = ["f", "s", "e", "a"]
array1.sort() // [1, 2, 3, 4, 5]
array2.sort() // ["a", "e", "f", "s"]

array1.reverse() // [5, 4, 3, 2, 1]
array2.reverse() // ["s", "f", "e", "a"]
```
`sort()`함수를 사용하여 배열을 오름차순으로, `reverse()`함수를 사용하여 배열을 내림차순으로 정렬할 수 있습니다. 

위 두 함수를 사용하면 원본 배열이 변경됩니다. 하지만 만약 원본 배열은 유지한 채 배열을 정렬하고 싶다면 어떡해야 할까요? 이때는 `sorted()`, `sorted(by: <)`, `sorted(by: >)` 함수들을 사용해주면 됩니다. (`sorted()`와 `sorted(by: <)`는 결과가 같습니다.)

```swift
var array = [5, 3, 4, 1, 2]

var newArray = array.sorted()
print(newArray) // [1, 2, 3, 4, 5]
print(array) // [5, 3, 4, 1, 2]

var newArray1 = array.sorted(by: <)
print(newArray1) // [1, 2, 3, 4, 5]
print(array) // [5, 3, 4, 1, 2]

var newArray2 = array.sorted(by: >)
print(newArray2) // [5, 4, 3, 2, 1]
print(array) // [5, 3, 4, 1, 2]
```

<br><br>
<span style="color: #0281C3"> 이상으로 컬렉션 중 하나인 배열에 대해 살펴봤습니다.. 다음에는 또 다른 컬렉션인 딕셔너리에 대해 포스팅해 보겠습니다.</span>
