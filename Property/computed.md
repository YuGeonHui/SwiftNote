## Computed Property 

- 연산 프로퍼티 속성을 언제 사용하면 좋을지 예시 부터 알아보자

```swift 
struct Workout {
    let startTime: Date
    let endTime: Date
}

let start = Date()
sleep(5)
let end = Date()

let workout = Workout(startTime: start, endTime: end)
let start = Date()
sleep(5)
let end = Date()

workout.endTime.timeIntervalSince(workout.startTime)
```

- 연산 프로퍼티를 사용하지 않는 경우, 운동시간을 계산하기 위해서 
- 위의 코드의 마지막 줄을 반복해서 계산해야 한다.
- 이를 Computed Property를 통해 변환을 해보면 
- 위의 코드처럼 timeElapsed의 속성을 통해 쉽게 접근 할 수 있다.

```swift

struct Workout {
    let startTime: Date
    let endTime: Date
    
    var timeElapsed: TimeInterval {
        endTime.timeIntervalSince(startTime)
    }
}

let start = Date()
sleep(5)
let end = Date()

let workout = Workout(startTime: start, endTime: end)
workout.timeElapsed
```

## Example 2
- Cart의 값이 추가될 때마다 총액을 구해야 하는 경우에도
- Computed Property를 사용하면 좋을 것이다.  

```swift 
struct CartItem {
    let name: String
    let price: Double
}

struct Cart {
    let items: [CartItem]
    
    // 새로운 항목이 추가될 때마다 총액 값을 추가해줘야 한다.
    var total: Double {
        items.reduce(0) {
            return $0 + $1.price
        }
    }
}

let items = [CartItem(name: "Bread", price: 4.50), CartItem(name: "Milk", price: 3.50), CartItem(name: "Pizza", price: 10.95)]

let cart = Cart(items: items)
print(cart.total)
```


