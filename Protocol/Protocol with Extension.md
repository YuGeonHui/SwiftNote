## Protocol에 Extension을 사용하여 확장성을 알아보자

- 아래와 같은 프로토콜이 존재 한다고 하자

```swift 
protocol Account {
    
    var balance: Double { get set }
    
    mutating func deposit(_ amount: Double)
    mutating func withdraw(_ amount: Double)
    func transfer(from: Account, to: Account, amount: Double)
    func calculateInterestEarned() -> Double
}
```

- 아래의 프롵토콜을 구현하는 구조체를 2개 만들어 보자 

```swift 
struct CheckingAccount: Account {
    
    var balance: Double
    
    mutating func deposit(_ amount: Double) {
        balance += amount
    }
    
    mutating func withdraw(_ amount: Double) {
        balance -= amount
    }
    
    func calculateInterestEarned() -> Double {
           return (balance * (0.1/100))
    }
    
    func transfer(from: Account, to: Account, amount: Double) {
        
    }
    
}

struct MoneyMarketAccount: Account {
    
    var balance: Double
    
    mutating func deposit(_ amount: Double) {
        balance += amount
    }
    
    mutating func withdraw(_ amount: Double) {
        balance -= amount
    }
    
    func calculateInterestEarned() -> Double {
           return (balance * (0.1/100))
    }
    
    func transfer(from: Account, to: Account, amount: Double) {
        
    }
    
}
```
- 위으 코드처럼 프로토콜을 준수 했을 뿐인데, deposit, withdraw, calculateInterestEarned 함수들이 중복으로 처리된다.
- 이러한 중복을 막기 위해서는 Protocol의 Extension을 사용하여 확장한다.
- 중복 되는 코드들을 Extension에 선언해보자.

```swift 
extension Account {
    
    mutating func deposit(_ amount: Double) {
        balance += amount
    }
    
    mutating func withdraw(_ amount: Double) {
        balance -= amount
    }
    
    func calculateInterestEarned() -> Double {
           return (balance * (0.1/100))
    }
    
}
```
- 위와 같이 프로토콜의 기본 구현을 만들어 놓는다면, 기존의 구조체는 아래와 같이 바뀔것이다.

```swift 

struct CheckingAccount: Account {
    
    var balance: Double
    
    func transfer(from: Account, to: Account, amount: Double) {
        
    }
    
}

struct MoneyMarketAccount: Account {
    
    var balance: Double
    
    
    func transfer(from: Account, to: Account, amount: Double) {
        
    }
    
}
```

- 코드가 위 처럼 간결해졌다. 만일 기본 구현과 다른 구현을 하고 싶은경우에는 기존 처럼 똑같이 구현하여 사용하면된다.
- calculateInterestEarned 함수를 다르게 구현하고 싶은경우라면 

```swift 
struct CheckingAccount: Account {
    
    var balance: Double
    
    func calculateInterestEarned() -> Double {
           return (balance * (0.2/100))
    }
    
    func transfer(from: Account, to: Account, amount: Double) {
        
    }
    
}
```

- 위외 코드철머 구현을 하면, 새롭게 적용된 함수를 적용할 수 있다.
