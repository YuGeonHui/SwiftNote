# zip
- 시퀀스를 수행하고 쌍을 반환한다. 
- 배열의 수가 다를 때 적은 수의 맞춰서 Zip연산 수행 후 종료된다.

```swift 
import UIKit


let students = ["Alex", "Mary", "John", "Steven"]
let grades = [3.4, 2.8]

let pair = zip(students, grades)

for studentAndGrade in pair {
    print(studentAndGrade.0)
    print(studentAndGrade.1)
}
```
