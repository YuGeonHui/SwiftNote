## Comparable 프로토콜과 제너릭을 함께 사용해보자 

- 기본적으로 Comparable 프로토콜을 사용해보자
- 배열의 값에서 가장 작은 값을 추출하는 제너릭 함수이다.
- 비교하는 구문이 들어가기 때문에 Comparable 프로토콜을 따르고 있다.
```swift 
func lowest<T: Comparable>(list: [T]) -> T? {
    
    let sortedList = list.sorted {
        return $0 < $1
    }
    
    return sortedList.first
}

print(lowest(list: [4,5,6,1,200,-100, 999])) // - 100
print(lowest(list: ["b","c","a","z"])) // "a"
```

- 비교구문을 enum에도 적용을 시켜보자.
- 아래와 같은 enum 타입이 존재하고 < 함수를 구현해 보자.
```swift
enum Card: Comparable {
    case ace
    case king
    case queen
    
    static func <(lhs: Card, rhs: Card) -> Bool {
        switch(lhs, rhs) {
            case (king, ace): return true
            case (queen, king): return true
            case (queen, ace): return true
            default: return false
        }
    }
}

let ace = Card.ace
let queen = Card.queen

if queen < ace {
    print("queen < ace") // 출력이된다.
}

print(lowest(list: [Card.ace, Card.queen, Card.king]))  // Card.queen
```
