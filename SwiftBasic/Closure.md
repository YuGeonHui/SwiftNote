# Closure (익명함수)
- 클로저는 1급 객체이다.
- 함수의 input, ouput으로 사용이 가능하며, 하나의 타입으로 선언이 가능하다.
- 클로저는 클래스의 인스턴스 처럼 힙영역에 저장이된다. 
- 클로저를 사용하는 경우 메모리릭에 유의해야 하는 경우가 존재한다.

```swift
// MARK: Example1
func calculator(n1: Int, n2: Int, operation: (Int, Int) -> Int) -> Int {
    return operation(n1, n2)
}

func add(no1: Int, no2: Int) -> Int {
    return no1 + no2
}

func multiply(no1: Int, no2: Int) -> Int {
    return no1 * no2
}

calculator(n1: 2, n2: 3, operation: add)
calculator(n1: 2, n2: 3, operation: multiply)

calculator(n1: 2, n2: 3, operation: { (no1: Int, no2: Int) -> Int in
    return no1 * no2
})

// 1. 추측가능한 자료형은 삭제할 수 있다.
calculator(n1: 2, n2: 3, operation: { (no1, no2) in
    return no1 * no2
})

// 2. 클로저 내부에 return 키워드를 제거 할 수 있다.
calculator(n1: 2, n2: 3, operation: { (no1, no2) in
    no1 * no2
})

// 3. $0 : 첫번째 인자, $1: 두번째 인자로 둘 수 있다.
calculator(n1: 2, n2: 3, operation: { $0 * $1 })
calculator(n1: 2, n2: 3) { $0 * $1 }

// MARK: Example2
let array = [6, 2, 3, 9, 4, 1]

func addOne(n1: Int) -> Int {
    return n1 + 1
}

array.map(addOne)
array.map { $0 + 1 }
array.map { "\($0)" }
```
