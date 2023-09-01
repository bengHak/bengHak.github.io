---
layout: post

title: Swift - @discardableResult 란?

subtitle:

tags: [Swift, Xcode, language]

comments: true

use_math: true
---

Swift의 `@discardableResult` 어트리뷰트는 함수의 반환값을 무시하고 사용하지 않아도 되는 것을 나타냅니다. 이것은 주로 함수가 부수적인 효과(side effect)를 가지거나 반환값을 사용하지 않을 때 유용합니다. 예를 들어, 파일을 열고 닫는 함수에서 반환되는 파일 핸들을 사용하지 않는 경우 이 어트리뷰트를 사용하여 경고 메시지를 제거할 수 있습니다.

다음은 `@discardableResult` 어트리뷰트를 사용한 간단한 예시입니다:

```swift
class FileManager {
    @discardableResult
    func openFile(withName name: String) -> Bool {
        // 파일을 열고 작업을 수행하는 코드
        print("파일 열기: \(name)")
        return true
    }
}

let fileManager = FileManager()
fileManager.openFile(withName: "example.txt") // 반환값을 사용하지 않아도 됨
```

위의 코드에서 `openFile(withName:)` 함수는 파일을 열고 작업을 수행하며 `true`를 반환합니다. 그러나 반환값을 사용하지 않아도 되기 때문에 `@discardableResult` 어트리뷰트를 사용하여 반환값을 무시할 수 있습니다.

만약 `@discardableResult` 어트리뷰트를 사용하지 않았다면 다음과 같은 경고가 발생할 수 있습니다:

```
Result of call to 'openFile(withName:)' is unused
```

즉, 이 어트리뷰트를 사용하면 반환값을 무시하더라도 컴파일러 경고를 피할 수 있습니다. 그러나 주의해야 할 점은 반환값이 실제로 필요한 경우에는 `@discardableResult` 어트리뷰트를 사용하지 않는 것이 좋습니다.

[discardableResult 참고 문서](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/methods/)