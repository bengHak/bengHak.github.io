---
layout: post

title: What is the \@dynamicMemberLookup ?

subtitle: -

tags: [Swift, Xcode, language]

comments: true

use_math: true
---

# @dynamicMemberLookup

> Ref. https://developer.apple.com/documentation/foundation/attributedynamiclookup

`@dynamicMemberLookup` is one of the property wrappers introduced in Swift 5.1. It allows dynamic access to properties and subscript members at runtime, enhancing code readability and convenience.

By default, in Swift, you need to know the exact names of members when accessing them in classes or structures. However, using the `@dynamicMemberLookup` attribute, you can dynamically determine member names at runtime.

For instance, you can define a structure using the `@dynamicMemberLookup` attribute as follows:

```swift
@dynamicMemberLookup
struct DynamicStruct {
    subscript(dynamicMember member: String) -> String {
        return "You accessed \(member)"
    }
}
```

In the above code, the `DynamicStruct` structure has a `subscript(dynamicMember:)` subscript, which handles dynamic member access. The `dynamicMember` parameter represents the actual member's name, and you can implement the behavior to return values for that member.

Now, you can use this structure to dynamically access members, like this:

```swift
let dynamicInstance = DynamicStruct()
print(dynamicInstance.someProperty)  // Output: "You accessed someProperty"
print(dynamicInstance.anotherProperty)  // Output: "You accessed anotherProperty"
```

In this way, by using the `@dynamicMemberLookup` attribute, you can dynamically access members that are not defined at compile time. This can be particularly useful when dealing with flexible access to data or properties in specific APIs or libraries.