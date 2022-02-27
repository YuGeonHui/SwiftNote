### BehaviorRelay

- RxCocoa를 import 하여 사용가능하다. 
- BehaviorRelay는 초기 값을 갖는다. 
- BehaviorRelay의 값을 저장하기 위해서는 .accept()를 사용한다. 
- BehaviorRelay의 기존의 값을 손실하지 않기 위해 새로운 변수에 value값을 저장해준다. 


```swift
let relay = BehaviorRelay(value: ["Item 1"])

var value = relay.value
value.append("Item 2")
value.append("Item 3")

relay.accept(value)

relay.asObservable().subscribe { print($0) }
```
