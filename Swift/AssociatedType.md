# AssociatedType

protocol을 생성할 시 다음과 같이 type을 명시해야 하는 경우가 있다.

```swift
protocol MyProtocol {
    var name: String { get }
}
```

이때 type이 정해져 있지 않은 변수나 상수를 protocol 내에서 선언하고 싶을 때 사용하는 키워드가 바로 **Associated Type** 이다.

```swift
protocol MyProtocol {
    associatedtype typeName
    var name: typeName { get }
}

class MyClass: MyProtocol {
    var name: String { return "영미" }

    // var name: Int { return 100 }
}
```

Associated Type에 제약을 주는 것 또한 가능하다.

```swift
protocol MyProtocol {
    associatedtype typeName: Equatable
    var equatableValue: typeName { get }
}

class nonEquatable {
    // equatable을 준수하지 않는 class
}

class MyClass: MyProtocol {
    var equatableValue: nonEquatable { return nonEquatable() }

    // Error !!
}
```