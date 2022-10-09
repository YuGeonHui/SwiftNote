## Nested Function (중첩 함수)
- 메서드 안에 메서드가 중첩으로 정의되어있는 경우 중첩함수라고 한다.

```swift 
import UIKit

struct Pizza {
    let sauce: String
    let toppings: [String]
    let crust: String
}

class PizzaBuilder {
    
    func prepare() -> Pizza {
        
        // Nested Fucntion #1
        func prepareSauce() -> String {
            return "Tomato Sauce"
        }
        
        // Nested Fucntion #2
        func prepareCrust() -> String {
            return "Hand Tossed"
        }
        
        // Nested Fucntion #3
        func prepareToppings() -> [String] {
            return ["Chicken", "Mushroom", "Onions"]
        }
        
        let crust = prepareCrust()
        let sauce = prepareSauce()
        let toppings = prepareToppings()
        
        return Pizza(sauce: sauce, toppings: toppings, crust: crust)
        
    }

}

let pizzaBuilder = PizzaBuilder()
let pizza = pizzaBuilder.prepare()

```
