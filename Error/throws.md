## throws 
- 스위프트에서 에러구문을 실행을 하기 위해서는 ```throws```를 사용해야 한다.
- Error 프로토콜을 채택하고 Error케이스를 만들어 보자.

```swift
import UIKit

enum BankAccountError: Error {
    case insufficientFunds
    case accountClosed
}
```
- enum을 통하여 다양한 에러케이스를 만들 수 있다.
- 해당 에러를 사용하기 위해서 BankAccount 클래스를 만들고 함수를 생성한다.
- throw를 사용하기 위해선, throws를 사용해야 한다.

```swift
class BankAccount {
    
    var balance: Double
    
    init(balance: Double) {
        self.balance = balance
    }
    
    func withdraw(amount: Double) throws {
        if balance < amount {
            throw BankAccountError.insufficientFunds
        }
        
        balance -= amount
    }
    
}
```
- 해당 함수를 실행하기 위해서는 try를 통해 사용해야 한다.
- 해당 함수를 사용하려면 아래와 같이 사용하면된다.
```swift
let account = BankAccount(balance: 100)

do {
    try account.withdraw(amount: 300)
} catch {
    print(error) // insufficientFunds
}
```
 
