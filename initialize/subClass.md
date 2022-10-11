## Sub Class

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
``` 
- 위와 같은 클래스가 존재할 때, 서브클래싱을 이용해보자 

```swift 
class Tesla: Car {
    var range: Double
   
    init(make: String, model: String, color: String, range: Double) {
        self.range = range
        super.init(make: make, model: model, color: color)
    }
}
```
- 위와 같이 range 프로퍼티가 추가 된 경우, 부모 클래스의 init, convenience 모두 사용 할 수 없다.
- 이를 해결학기 위행 override 키워드를 사용하고, range의 값의 임의 값을 넣어서 해결해준다.

```swift 
class Tesla: Car {
    var range: Double
    
    override init(make: String, model: String, color: String) {
        self.range = 300
        super.init(make: make, model: model, color: color)
    }
}
```
