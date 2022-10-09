## Enum vs Struct 

- Student, Teacher 구조체가 각각존재하는 경우를 나타내보면 아래와 같이 나타낼 수 있다.

```swift
import UIKit

struct Teacher {
    let name: String
    let courses: [String]
}

struct Student {
    let name: String
    let courses: [String]
    var grade: String?
}
```

- 해당 구조체를 통해서 인스턴스를 생성해보면 아래와 같이 생성할 수 있다.
```swift
let teacher = Teacher(name: "John Doe", courses: ["Math", "Science"])
let student = Student(name: "Patrick Hoffman", courses: ["Math", "History"])
``` 
- 하지만 이 두개의 구조체를 같이 사용해야 하는 경우 
- 배열의 타입을 지정해야 하기 때문에 Any 타입으로 지정을 해줘야 한다.

```swift
let users: [Any] = [teacher, student]
```

- Any 타입을 지정을 해줬기 때문에 불 필요한 casting 과정이 필요하게 된다.
- 또한 Any 타입이기 때문에 default 값도 지정해줘야 한다.

```swift
for user in users {
    switch user {
        case let user as Student: // Casting
            print(user.grade ?? "")
        case let user as Teacher: // Casting
            print(user.courses)
        default:
            print("Not student or teacher")
    }
}
````

- 이를 아래와 같이 enum 타입의 연관값으로 지정을 해보자.

```swift
enum User {
    case teacher(Teacher)
    case student(Student)
}
``` 

- 2개의 구조체 모두 User Enum을 따로고 있기 때문에 아래와 같이 나타낼 수 있으며
- User 타입의 배열로 받을 수 있다. 

```swift
let allUsers = [User.teacher(teacher), User.student(student)]
```

- 또한 이 모든걸 표현하기 위해서는 캐스팅 없이 바로 접근이 가능하다.

```swift
for user in allUsers {
    switch user {
        case .student(let student):
            print(student.grade ?? "")
        case .teacher(let teacher):
            print(teacher.courses)
    }
}
```
