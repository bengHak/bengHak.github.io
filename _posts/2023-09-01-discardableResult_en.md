---
layout: post

title: Swift - What is @discardableResult?

subtitle:

tags: [Swift, Xcode, language]

comments: true

use_math: true
---

In Swift, the `@discardableResult` attribute is used to indicate that the return value of a function can be ignored and doesn't need to be used. This is particularly useful when a function has side effects or when you intentionally want to ignore its return value. Let's illustrate this with a simple example:

```swift
class FileManager {
    @discardableResult
    func openFile(withName name: String) -> Bool {
        // Code to open and perform operations on the file
        print("Opening file: \(name)")
        return true
    }
}

let fileManager = FileManager()
fileManager.openFile(withName: "example.txt") // The return value can be ignored
```

In the code above, the `openFile(withName:)` function opens a file, performs some operations, and returns `true`. However, because we may not need to use the return value, we use the `@discardableResult` attribute to indicate that it's acceptable to ignore the return value.

Without the `@discardableResult` attribute, you might receive a compiler warning like this:

```
Result of call to 'openFile(withName:)' is unused
```

Using `@discardableResult` allows you to suppress this warning when you intentionally don't need to use the return value. However, it's important to note that you should only use `@discardableResult` when you genuinely don't need the return value. If the return value is necessary for your code logic, it's better not to use the attribute.

[Swift Docs includes "discardableResult"](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/methods/)