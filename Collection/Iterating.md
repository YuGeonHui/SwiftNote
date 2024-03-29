## Collection
- Array, Set, Dictionary는 Collection 프로토콜을 채택하고 있다.
- Collection 프로토콜은 Sequence 프로토콜을 채택하고 있다.

## Sequence
- 한 번에 하나씩 단계별로 진행할 수 있는 값 목록이다. (list of value)
- Countdown 구조체에 for-in loop를 사용할 수 있도록 예제를 구현

```swift 

struct Countdown: Sequence {
    
    let start: Int
    
    // required method
    func makeIterator() -> some IteratorProtocol {
        return CountdownIterator(self)
    }
}

// IteratorProtocol을 구현하는 구조체 만들기
struct CountdownIterator: IteratorProtocol {
    let countdown: Countdown
    var currentValue = 0
    
    init(_ countdown: Countdown) {
        self.countdown = countdown
        self.currentValue = countdown.start
    }
    
    mutating func next() -> Int? {
        if currentValue > 0 {
            let value = currentValue
            currentValue -= 1
            return value
        } else {
            return nil
        }
    }
}

let countdown = Countdown(start: 10)

// for-in loop에서 사용가능!!
for count in countdown {
    print(count)
}
```
