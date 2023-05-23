## convenience init

- 일반적인 초기화 외에도 사용할 수 있는 초기화 방법이다.
- 자기 자신이 가지고 있는 지정생성자를 호출하여 편리(convenience)하게 사용가능한 생성자이다.
- 구조체의 경우에는, 해당 키워드를 붙이지 않고 사용이 가능하다.
- 해당 방법을 사용하여, color의 값을 기본 값을 넣어줄 수 있다.

```swift 
import UIKit


class Car {
    
    var make: String
    var model: String
    var color: String
    
    init(make: String, model: String, color: String) {
        self.make = make
        self.model = model
        self.color = color
    }
    
    convenience init(make: String, model: String) {
        self.init(make: make, model: model, color: "White")
    }
    
}

let whiteCar = Car(make: "Honda", model: "Accord")
let redCar = Car(make: "redCar", model: "model", color: "Red")
```
