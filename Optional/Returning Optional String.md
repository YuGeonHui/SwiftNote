## Returning Optional String

- 아래와 같은 학생 구조체가 존재하고 이를 화면에 보여주는 로직을 짤때
- Optional이 문제가 될 것이다.

```swift 
struct Student {
    let firstName: String?
    let lastName: String?
    
  
    var displayName: String {
        
        guard let firstName = firstName, let lastName = lastName else {
            return ""
        }
        
        return "\(firstName) \(lastName)"
    }
}

let student = Student(firstName: "John", lastName: "Doe")

func createGreetingMessage(student: Student) -> String {
   let message = """
        Dear \(student.displayName ?? "Student"), Welcome to Swift University
    """
    return message
}

let message = createGreetingMessage(student: student)
print(message)
```
- displayName 이라는 프로퍼티를 언래핑을 하여 사용하는 경우,
- firstName, lastName 둘다 옵셔널이 아닌경우는 언래핑 이후 사용이 가능하지만
- 둘 중 하나라도, 언래핑이 되지 않으면 빈 문자열을 출력하게 된다.
- 이를 해결하기 위해 아래와 같이 case let을 사용하여 언래핑 한다.

```swift
var displayName: String? {
    switch (firstName, lastName) { // unwrapping
        case let (first?, last?): return "\(first) \(last)" // 둘다 존재 하는경우
        case let (first?, nil): return first
        case let (nil, last?): return last
        default: return nil
    }
}
```
- 첫번째 케이스의 경우 firstName, lastName 둘다 옵셔널이 언래핑 된경
- 두번째 케이스의 경우, firstName만 언래핑이 된 경우
- 세번째 케이스의 경우, lastName만 언래핑이 된 경우를 나타낸다.
