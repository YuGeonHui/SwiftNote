# merge

- 방출되는 값을 병합하여 항목을 하나로 결합
- 병합 연산자를 사용하여 여러 관측치의 출력을 결합하여 단일 관측치처럼 작동할 수 있다.

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
