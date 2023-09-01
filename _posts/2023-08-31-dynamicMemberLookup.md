---
layout: post

title: Swift - @dynamicMemberLookup 이란?

subtitle: subtitle

tags: [Swift, Xcode, language]

comments: true

use_math: true
---

## @dynamicMemberLookup

`@dynamicMemberLookup`는 Swift 5.1부터 도입된 속성 래퍼(property wrapper) 중 하나로, 런타임에서 속성 및 서브스크립트 멤버에 대한 동적 접근을 허용하는 기능을 제공합니다. 이를 통해 코드의 가독성을 높이고 편의성을 개선할 수 있습니다.

기본적으로, Swift에서는 클래스나 구조체의 멤버에 접근할 때 해당 멤버의 이름을 정확히 알아야 합니다. 하지만 `@dynamicMemberLookup` 속성을 사용하면 런타임에 멤버의 이름을 동적으로 결정할 수 있습니다.

예를 들어, 다음과 같이 `@dynamicMemberLookup` 속성을 사용하여 구조체를 정의할 수 있습니다:

```swift
@dynamicMemberLookup
struct DynamicStruct {
    subscript(dynamicMember member: String) -> String {
        return "You accessed \(member)"
    }
}
```

위의 코드에서 `DynamicStruct` 구조체는 `subscript(dynamicMember:)` 서브스크립트를 가지고 있는데, 이 서브스크립트는 동적 멤버 접근을 처리합니다. `dynamicMember` 매개변수는 실제 멤버의 이름을 나타내며, 해당 멤버에 대한 값을 반환하는 동작을 구현할 수 있습니다.

이제 이 구조체를 사용하여 다음과 같이 멤버에 동적으로 접근할 수 있습니다:

```swift
let dynamicInstance = DynamicStruct()
print(dynamicInstance.someProperty)  // 출력: "You accessed someProperty"
print(dynamicInstance.anotherProperty)  // 출력: "You accessed anotherProperty"
```

이처럼, `@dynamicMemberLookup` 속성을 사용하면 컴파일 시점에 정의하지 않은 멤버에 동적으로 접근할 수 있습니다. 이는 특정 API나 라이브러리에서 유연하게 데이터나 속성에 접근할 때 유용할 수 있습니다.

참조: https://developer.apple.com/documentation/foundation/attributedynamiclookup
