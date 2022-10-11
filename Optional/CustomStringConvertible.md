## CustomStringConvertible (Protocol)

```swift
struct Student {    
    let firstName: String
    let lastName: String
    let middleName: String?
    let grade: String?
}

let student = Student(firstName: "John", lastName: "Doe", middleName: "Smith", grade: "A")
print(student)
```

- 위와 같이 출력을 하면 Student(firstName: "John", lastName: "Doe", middleName: Optional("Smith"), grade: Optional("A")) 으로 출력이된다.
- 이러한 출력을 변경 하기 위해서는 CustomStringConvertibled을 준수하면된다 .
- 해당 프로토콜을 준수하는경우, var description을 채택해야 한다.

```swift 
struct Student: CustomStringConvertible {
    
    var description: String {
        var studentDescription = "\(firstName) "
        
        // Optional Unwrapping
        if let middleName = middleName {
            studentDescription += "\(middleName)"
        }
        
        studentDescription += " \(lastName) "
        
         // Optional Unwrapping
        if let grade = grade {
            studentDescription += "\(grade)"
        }
        
        return studentDescription
    }
    
    let firstName: String
    let lastName: String
    let middleName: String?
    let grade: String?
}

let student = Student(firstName: "John", lastName: "Doe", middleName: "Smith", grade: "A")
print(student)
```
- 해당 프로토콜을 채택하여 결과를 출력해보면, John Smith Doe A 의 결과를 볼 수 있다. 
