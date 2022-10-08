## reduce
- 배열의 값을 가져와서 하나의 단일 값으로 줄이는 것
- 초기 값과, 그 다음의 값을 가져온다.

```swift 
import UIKit

struct Item {
    let name: String
    let price: Double
}

struct Cart {
    
    private(set) var items: [Item] = []
    
    mutating func addItem(_ item: Item) {
        items.append(item)
    }
   
    var total: Double {
        items.reduce(0) { (value, item) -> Double in
            return value + item.price
        }
    }
}

var cart = Cart()
cart.addItem(Item(name: "Milk", price: 4.50))
cart.addItem(Item(name: "Bread", price: 2.50))
cart.addItem(Item(name: "Eggs", price: 12.50))

print(cart.total) // 19.5

let items = [2.0,4.0,5.0,7.0]
let total = items.reduce(0, +)

print(total) // 18
```
