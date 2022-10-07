## Collection
- Array, Set, Dictionary는 Collection 프로토콜을 채택하고 있다.
- Collection 프로토콜은 Sequence 프로토콜을 채택하고 있다.

## Sequence
- 한 번에 하나씩 단계별로 진행할 수 있는 값 목록이다. (list of value)

```swift 

struct Countdown: Sequence {
    
    let start: Int
    
    func makeIterator() -> some IteratorProtocol {
        return CountdownIterator(self)
    }
}

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
for count in countdown {
    print(count)
}
```
