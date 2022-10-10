## Enum vs Class (2)

- 서브클래싱을 사용하는 경우 자신이 100% 프로퍼티가 공유될 것이라고 생각할 때 사용해야 한다.

```swift
import UIKit

class User {
    
    var name: String
    var courses: [String]
    var isFullTime: Bool
    
    init(name: String, courses: [String], isFullTime: Bool) {
        self.name = name
        self.courses = courses
        self.isFullTime = isFullTime
    }
}

class Staff: User {
    
}

class Teacher: User {
   
}

class Student: User {

}
```

- 서브클래싱을 통해 쉽게 구현할 수 있다.
- 만일, 이러한 과정에서 Staff에 courses가 필요 없어지는 경우에는 문제가 발생한다.

```swift
class User {
    var name: String
    var isFullTime: Bool
    
    init(name: String, isFullTime: Bool) {
        self.name = name
        self.isFullTime = isFullTime
    }
    
}

class Staff: User {
    
}

class Teacher: User {
    var courses: [String]
    
    init(name: String, courses: [String], isFullTime: Bool) {
        self.courses = courses
        super.init(name: name, isFullTime: isFullTime)
    }
}

class Student: User {
    var courses: [String]
    
    init(name: String, courses: [String], isFullTime: Bool) {
        self.courses = courses
        super.init(name: name, isFullTime: isFullTime)
    }
}
```

- courses 프로퍼티를 상속 받아서 사용하지 않고, 각각의 ```class```에 직접선언을 해줘야 하는 문제가 발생한다.
- 이를 Enum을 통해서 해결을 해보자 
- 각각의 해당하는 구조체를 만들고 enum으로 선언한다.

```swift 
struct Student {
    let name: String
    let courses: [String]
    let isFullTime: Bool
}

struct Teacher {
    let name: String
    let courses: [String]
    let isFullTime: Bool
}

struct Staff {
    let name: String
    let isFullTime: Bool
}

struct International {
    let name: String
    let isFullTime: Bool
    let courses: [String]
    let countryOfOrigin: String
}

enum User {
    case student(Student)
    case teacher(Teacher)
    case staff(Staff)
    case international(International)
}
```
- 이를 쉽게 사용하기 위해서는 단순히 enum형을 받아서 사용하면 된다.
 
```swift
func updateProfile(user: User) {
    switch user {
        case .student(let student):
            print(student)
        case .teacher(let teacher):
            print(teacher)
        case .staff(let staff):
            print(staff)
        case .international(let international):
            print(international)
    }
    
}

updateProfile(user: User.student(Student(name: "John Doe", courses: ["Math", "Science"], isFullTime: true)))
```
