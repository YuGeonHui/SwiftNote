## Chaning Optional

- 아래와 같은 구조체가 존재할 때, 학점에 다가가기 위해 옵셔널 래핑을 일반적으로 진행하는 경우 
```swift 
import UIKit

struct Grade {
    let gpa: Double?
    let letter: String?
}

struct Student {
    let firstName: String
    let lastName: String
    let grade: Grade?
}

let student = Student(firstName: "John", lastName: "Doe", grade: Grade(gpa: 3.2, letter: "B"))

if let grade = student.grade {
    if let gpa = grade.gpa {
        //print(gpa)
    }
}
```

- 위와 같은 방법을 사용하는 경우, 중첩 if-let 구문을 사용해야 하는 번거러움이 존재한다.
- 이를 해결하기 위해 Optional값의 default 값을 줘서 해결하는 방법을 사용하면, 쉽게 해결할 수 있다.

```swift 
print(student.grade?.gpa ?? "N/A")
```
