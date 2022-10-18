## Node 

- Linked List를 연결하는 하나의 노드를 코드로 구현해보았다.
- 제너릭 타입의 Value를 선언하여, 어떠한 값이라도 올 수 있게 적용했다.
- 또한 출력을 위해서 CustomStringConvertible을 채택하고 값을 볼 수 있게 진행했다.

```swift 
import UIKit

class Node<Value> {
    
    var value: Value
    var next: Node?
    
    init(value: Value, next: Node? = nil) {
        self.value = value
        self.next = next
    }
}

extension Node: CustomStringConvertible {
    
    var description: String {
        
        guard let next = next else {
            return "\(value)"
        }
        
        return "\(value) -> " + String(describing: next) + " "
    }
    
}

let node1 = Node(value: 1)
let node2 = Node(value: 2) 
let node3 = Node(value: 3)

node1.next = node2 // 1 -> 2 
node2.next = node3 // 2 -> 3 

print(node1) // 1 -> 2 -> 3 
```
