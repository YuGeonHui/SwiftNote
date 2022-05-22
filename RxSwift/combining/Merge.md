# merge

- 여러 옵저버블이 방출될 때, 그 시간 순서에 따라서 값을 방출한다. 

<img width="747" alt="image" src="https://user-images.githubusercontent.com/96224311/169683407-7d6e990b-8e84-4c39-aeff-02cac0fc6817.png">

```swift

let disposeBag = DisposeBag()

let left = PublishSubject<Int>()
let right = PublishSubject<Int>()

let source = Observable.of(left.asObservable(), right.asObservable())

let observable = source.merge()
observable.subscribe(onNext: {
  print($0)
}

left.onNext(5)
right.onNext(3)
left.onNext(2)
left.onNext(1)
right.onNext(99) // 5, 3, 2, 1, 99
```
