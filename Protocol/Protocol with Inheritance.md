## Protocol with Inheritance
- 프로토콜의 상속을 통하여, 다양한 기본 기능들을 구현해보자

```swift 
import UIKit

struct Course {
    let courseNumber: String
    let name: String
    let creditHours: Int
}

protocol Student {
    var courses: [Course] { get set }
    mutating func enroll(_ course: Course)
}

// enroll 함수의 default 구현(기본 구현적용)
extension Student {
    mutating func enroll(_ course: Course) {
        courses.append(course)
    }
}

// Protocol의 상속
protocol VerifiedStudent: Student {
    func verify() -> Bool
}

// enroll 함수 제정의 가능 
extension VerifiedStudent {
    
    func enroll(_ course: Course) {
        if verify() {
            print("Enroll in course")
        }
    }
    
    func verify() -> Bool {
        return true
    }
    
}

struct InternationalStudent: VerifiedStudent {
    var courses: [Course] = []
}

let internationalStudent = InternationalStudent()
internationalStudent.enroll(Course(courseNumber: "1234", name: "Math", creditHours: 3))
```
