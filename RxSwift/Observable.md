# Observable 이란 

## Observable의 전체 개념은 구독(Subscribe)할 수 있고, 해당 이벤트를 얻을 수 있다. 

```swift
let observable1 = Observable.just(1) 

let observable2 = Observable.of(1, 2, 3)

let observable3 = Observable.of([1, 2, 3])

let observable4 = Observable.from([1, 2, 3, 4 ,5])

```
