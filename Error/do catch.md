## do-catch를 사용해서 오류 처리해보기
- prepareDough(), prepareToppings() 함수에서 각각 throw 를 통해 오류를 뱉은것을 
- prepare() 함수의 do-catch문에서 오류를 뱉을 수 있다.
- 오류의 전파를 통해 오류를 전달하는 모습을 볼 수 있다.

```swift
import UIKit

struct Pizza {
    let dough: String
    let toppings: [String]
}

enum PizzaBuilderError: Error {
    case doughBurnt
    case noToppings(String) // 에러를 String을 통해 전달가능 하다.
}

struct PizzaBuilder {
    
    func prepare() -> Pizza? {
        
        do {
            let dough = try prepareDough()
            let toppings = try prepareToppings()
            // return pizza
            return Pizza(dough: dough, toppings: toppings)
        } catch {
            print("Unable to prepare pizza")
            return nil
        }
    }
    
    private func prepareDough() throws -> String {
        // prepare the dough
        
        throw PizzaBuilderError.doughBurnt
    }
    
    private func prepareToppings() throws -> [String] {
          
          // prepare the toppings
          
        throw PizzaBuilderError.noToppings("Chicken and onions are missing!") // 문자열을 통해 에러를 전달 할 수 있다.
    }
}
```
