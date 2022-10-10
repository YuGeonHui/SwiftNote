## convenience init

- 일반적인 초기화 외에도 사용할 수 있는 초기화 방법이다.
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
