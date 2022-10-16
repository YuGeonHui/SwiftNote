## generic의 기본적인 내용에 대해서 공부해보자

```swift 

import UIKit


let numbers = [1,2,3,5,6,7,10]
let names = ["Alex", "John", "Mary", "Steve"]


func firstLast(_ numbers: [Int]) -> (Int, Int) {
    return (numbers[0], numbers[numbers.count - 1] )
}

func firstLast(_ names: [String]) -> (String, String) {
    return (names[0], names[names.count - 1] )
}

let (first, last) = firstLast(numbers)

print(first)
print(last)
```
- firstLast라는 함수를 구현하기 위해서, 데이터 타입에 따라 구현을 무한대로 늘릴 수 없다.
- 그럴 때 사용할 수 있는게 generic이다. 아래와 같이 사용해 보자 

```swift 
func firstLast<T>(_ list: [T]) -> (T, T) {
    return (list[0], list[list.count - 1] )
}
```

- 위처럼 함수를 변환하면 된다. <T>는 타입을 나타내게 된다. 
- 해당 기능을 통해서, 전체 코드를 살펴보면 
  
 
