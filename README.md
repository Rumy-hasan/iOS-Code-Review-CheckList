# iOS-Code-Review-CheckList
I am adding this list with the collection of different source and my personal view.
Some are:
- https://gist.github.com/pallavtrivedi03/8f4975a41f5b64d8a6af4fd119949d39
- https://dev.to/bornfightcompany/ios-code-review-checklist-53ia
- https://medium.com/swiftcairo/ios-code-review-checklist-482f17f5c7c6

## General:
  - Avoid Type Inference: If you know the actual type the write it done because type inference increase compiler time. To Usderstand properly, please read [this](https://stackoverflow.com/questions/37707403/what-is-the-difference-between-type-safety-and-type-inference) 
  
  - **Prefer using Higher Order Functions:** If possible use Higher Order Functions as they are more optimal. Increase the code quality.
  
  - **force unwraps:** Make sure that there are no force unwraps.
  
  - **Memory leaks:** 
    - Make sure that there are no retain cycles
    - Closures should use weak self
    - Delegates should be weak
    - Check if unowned is misused

  - **Check encapsulation:** Check if public variable or function can be private or private(set)? If a class won’t be ever instantiated - use enum instead.
  
  - **deprecated API:** Check if any deprecated API is being used
  
  - **Check for magic numbers and use enum:** Avoid harcoding, avoid magic numbers, if needed extract into a constant. If added, magic numbers should be commented. Better to use enum.

  - **Check polymorphism:** Should we mark the class final? Should we use class or static keyword for a function/variable.

  - **Some performance check:** 
    - use strings concatenation with \() instead of +
    - use isEmpty instead of == nil
    - use ! instead of == false
  
  - **Use native API:** Check if there’s any API provided by Apple which can make things simple. 
  
  - Try to avoid nested structures as much as possible. (loops, if/else)

  - **don't be hurry:** The code you write was read very often by others. So take time to write nice readable code instead it works and submit. If you don't write proper code you are besically increase project time as other don't usderstand and it will generate more bug.

  - **Index Out Of Bound Exception:** Wherever accessing the values from an Array is involved, check if there’s any possibility of Index Out Of Bound Exception.
  
  - Check if there are any unintended changes in the code.
  
  - Check for the corner cases. Example -  Error Handling (what if the backend doesn’t send an error message).
  
  - If there’s any complex logic involved, check if there’s a comment to explain it. 
  
  - Do proper Indentations.
  
  - Fonts, Colors etc shouldn’t be accessed randomly. There should be a separate file for them. 
  
  - Make sure that the directory structure is being followed.
  
  - See if the guidelines set by the team is being followed - SwiftLint (I also not use it. Need to learn.)
  
  - Test Cases(if we write) - Code Coverage of the new code. Also see that the code is written for isolate test.
  
  - Prefer static constants over computed properties

  - Extract constant to a struct

## Common responsibility for all developer:

  -**Kiss:** keep is simple and stupid.
  -**Follow Boy Scout Rule:** See if any existing bad code can be improvised - though it is not written by the developer who raised the pull request.
  -**YAGNI principle:** If you comment some code for future use then you Aren’t Gonna Need It because when it come the context will change.
  -**DRY:** Try to do not repeat yourself.

## Some very basic Principle:

  - **SOLID**
    - Single responsibility
    - Open close(open to extend but close to modify)
    - Substitution
    - Interface segrigation(protocol)
    - Dependency Inversion

  - **Avoid use singletone** Use DI container or DI. Code collected from [here](https://www.kodeco.com/14223279-dependency-injection-tutorial-for-ios-getting-started).

```swift
protocol DIContainerProtocol {
  func register<Component>(type: Component.Type, component: Any)
  func resolve<Component>(type: Component.Type) -> Component?
}

final class DIContainer: DIContainerProtocol {
  // 1
  static let shared = DIContainer()
  
  // 2
  private init() {}

  // 3
  var components: [String: Any] = [:]

  func register<Component>(type: Component.Type, component: Any) {
    // 4
    components["\(type)"] = component
  }

  func resolve<Component>(type: Component.Type) -> Component? {
    // 5
    return components["\(type)"] as? Component
  }
}

```

  - **Dependency Injection:** 
    - initializer injection
    - property injection or lazy property inject.
    - method injection or closure inject.

  - **Seperation of Concern:**
    - Always try to seperate or break your code.

  - **Proper modularization:**
    - If something is totally independent then modularize it and add it to your project as a service.

  - **Try to compose instead of inherit.** If you able to compose some protocol(interface) instead of concrete class it will be a very good code to write.

  - **Write code in protocol Extension** Try as many code write in the extention. It will provide a default implementation and clean code.

