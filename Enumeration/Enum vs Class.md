## Enum vs Class 

- Ticket이라는 클래스를 만들고 해당 클래스를 상속받는 클래스가 존재하는 경우 

```swift 
class Ticket {
    
    var departure: String
    var arrival: String
    var price: Double
 
    // 만일 새로운 개념이 추가된다면, 모든 상속받고 있는 모든 클래스에 적용을 해야한다.
    
    init(departure: String, arrival: String, price: Double) {
        self.departure = departure
        self.arrival = arrival
        self.price = price
    }
}

class Economy: Ticket {
    
}

class FirstClass: Ticket {
    
    var meal: Bool
    
    init(departure: String, arrival: String, price: Double, meal: Bool) {
        self.meal = meal
        super.init(departure: departure, arrival: arrival, price: price)
    }
    
}

class Business: Ticket {
    
    var meal: Bool
    var chargingPorts: Bool
    
    init(departure: String, arrival: String, price: Double, meal: Bool, chargingPorts: Bool) {
        self.meal = meal
        self.chargingPorts = chargingPorts
        super.init(departure: departure, arrival: arrival, price: price)
    }
    
}

func checkIn(ticket: Ticket) {
    
    switch ticket {
        case let ticket as Economy:
            print(ticket)
        case let ticket as FirstClass:
            print(ticket)
        case let ticket as Business:
            print(ticket)
        default:
            print("Unidentified ticket!")
    }
    
}
```

- 해당 상황의 경우 바람직한 사용 방법이라고 볼 수 있다.
- 하지만 상속 받는 개념이 공유가 되지 않는 상황인 경우 어떻게 해야될까 ?

```swift 
class BuddyPass: Ticket {
    
}
```

- 해당 클래스는 Ticket이지만 price의 개념이 전혀 필요하지 않는 경우 일때, 문제가 발생한다. 
- 이와 같은 상황을 클래스마다 케이스가 달라 분기가 필요한 경우라고 볼 수 있다.
- 해당상황의 경우 Enum을 사용해서 해결 하는 것이 좋다 .

```swift 
struct Economy {
    let departure: String
    let arrival: String
}

struct FirstClass {
    let departure: String
    let arrival: String
    let meal: Bool
}

struct Business {
    let departure: String
    let arrival: String
    let meal: Bool
    let chargingPorts: Bool
}

enum Ticket {
    case economy(Economy)
    case firstClass(FirstClass)
    case business(Business)
}

let ticket = Ticket.business(Business(departure: "Houston", arrival: "Denver", meal: true, chargingPorts: true))

func checkIn(ticket: Ticket) {
    switch ticket {
        case .economy(let economy):
            print(economy)
        case .firstClass(let firstClass):
            print(firstClass)
        case .business(let business):
            print(business)
        case .international(let international):
            print(international)
    }
}

```

- 만일 추가적으로 아래와 같은 구조체가 생겼다고 한다고 가정을 해보면,
 
```swift 
struct International {
    let departure: String
    let arrival: String
    let meal: Bool
    let chargingPorts: Bool
    let baggageAllowed: Bool
}
```

- 아무런 문제 없이 enum의 case만 추가해주면 된다.
- checkIn 함수에도 또한 case문만 추가해서 해결할 수 있다.

```swift 

enum Ticket {
    case economy(Economy)
    case firstClass(FirstClass)
    case business(Business)
    case international(International)
}

func checkIn(ticket: Ticket) {
    switch ticket {
        case .economy(let economy):
            print(economy)
        case .firstClass(let firstClass):
            print(firstClass)
        case .business(let business):
            print(business)
        case .international(let international):
            print(international)
    }
}
```
