## extenion을 이용한 초기화 방법 

```swift 

import UIKit


struct Student {
    let firstName: String
    let lastName: String
    let grade: String
    
}

extension Student {
    
    init(firstName: String, lastName: String) {
        self.firstName = firstName
        self.lastName = lastName
        self.grade = ""
    }
}
```

- extenion을 사용하지 않으면, grade가 필요한 경우에도 무조건 빈값을 넣을 수 있다.
- 하지만 extension을 통해서 값을 초기화하는 경우에는 

```swift 
let student = Student(firstName: "first", lastName: "last")
let studentWithGraude = Student(firstName: "first", lastName: "last", grade: "grade")
```

- 위 처럼, 2가지 방법 둘 다 가능하다.
