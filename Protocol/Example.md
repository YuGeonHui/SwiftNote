## 간단한 예제를 통해 프로토콜의 사용성을 알아보자 

```swift
protocol AirlineTicket {
    var name: String { get }
    var departure: Date? { get set }
    var arrival: Date? { get set }
}
```
- 위와 같은 프로토콜이 있다고 가정해보자
- AirlineTicket을 채택하는 프로토콜을 만들어 보면

```swift 
struct Economy: AirlineTicket {
    let name = "ECON"
    var departure: Date?
    var arrival: Date?
}

struct Business: AirlineTicket {
    let name = "BUS"
    var departure: Date?
    var arrival: Date?
}

struct First: AirlineTicket {
    let name = "FIRST"
    var departure: Date?
    var arrival: Date?
}
```

- 3개의 구조체를 정의 하였다. (AirlineTicket 프로토콜을 준수하는)
- tickets라는 프로퍼티는 값이 프로토콜로 정의한다. 
- 그렇다면, 해당 프로토콜을 채택하는 모든 값을 사용할 수 있다.

```swift
class CheckoutService {
    
    var tickets: [AirlineTicket]
    
    init(tickets: [AirlineTicket]) {
        self.tickets = tickets
    }
    
    func addTicket(_ ticket: AirlineTicket) {
        self.tickets.append(ticket)
    }
    
    func processTickets() {
        tickets.forEach {
            print($0)
        }
    }
    
}

let economyTickets = [Economy(departure: Date(), arrival: Date.fiveHoursFromNow())]

let service = CheckoutService(tickets: economyTickets)

service.addTicket(First(departure: Date(), arrival: Date.fiveHoursFromNow()))

service.processTickets() // "Econ First" 두가지가 나타난다.
```
- 만일 제너릭 타입으로 선언을 한다면, 하나의 타입으로 연결이 되기 때문에 
- append 하는 로직에서 문제가 발생할 수 있다. 

