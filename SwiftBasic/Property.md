# Get 

1. 프로퍼티에 get을 사용하기 위해서는 var 형태로 지정해야한다.
2. 명확한 데이터 타입을 정의 해야한다.
3. get만 사용하는 경우, 일반적으로 생략이 가능하다.

# set

1. 새 값을 가져올 때마다 안의 코드가 실행된다.
2. 속성이 생성되는 정확한 순간을 활용할 수 있다.
3. newValue 값으로 접근이 가능하다.

```swift
let pizzaInInches: Int = 10

var numberOfSlices: Int {
    get {
        return pizzaInInches - 4
    }
    set { // 
        print("numberSlices now has a new value which is \(newValue)")
    }
}
```
