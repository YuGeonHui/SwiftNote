## reduce
- 배열의 값을 가져와서 하나의 단일 값으로 줄이는 것
- 초기 값, 그 다음의 값을 가져온다.

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

## reduce(into: ) 

```swift
import UIKit


let ratings = [4, 8.5, 9.5, 2, 6, 3, 5.5, 7, 2.8, 9.8, 5.9, 1.5]

let ratingsResult = ratings.reduce([:]) { (results: [String: Int], rating: Double) in
    var copy = results // <<< How can you make sure that copy is NOT created. Creating a lot of copies can reduce performance 
    switch rating {
        case 1..<4: copy["Very bad", default: 0] += 1
        case 4..<6: copy["Ok", default: 0] += 1
        case 6..<8: copy["Good", default: 0] += 1
        case 8..<11: copy["Excellent", default: 0] += 1
        default: break
    }
    
    return copy
}

// 값 복사를 제거하기 위해서 into -> inout을 사용해서 적용한다.
let results = ratings.reduce(into: [:]) { (results: inout [String: Int], rating: Double)  in
    
    switch rating {
        case 1..<4: results["Very bad", default: 0] += 1
        case 4..<6: results["Ok", default: 0] += 1
        case 6..<8: results["Good", default: 0] += 1
        case 8..<11: results["Excellent", default: 0] += 1
        default: break
    }

}

print(results)
```
