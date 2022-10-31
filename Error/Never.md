## Never 
- 에러 타입을 사용하지 않는 경우 Never 타입을 선언해 사용할 수 있다.
- Result 타입에 들어가는 Error부분을 Never를 사용해서 바꿀 수 있다.

```swift 
import UIKit

struct Category {
    let name: String
}

protocol Service {
    associatedtype Value
    associatedtype Err: Error
    func load(completion: (Result<Value, Err>) -> Void)
}

class CategoryService: Service {
    
    func load(completion: (Result<[Category], Never>) -> Void) { 
        completion(.success([Category(name: "Fiction"), Category(name: "Horror"), Category(name: "Kids")]))
    }
    
}

CategoryService().load { (result) in
    switch result {
        case .success(let categories):
            print(categories)
    }
}
```
