# combineLatest

- 두 개의 Observable 중 하나에 의해 항목이 배출될 경우, 지정된 기능을 통해 각 Observable에서 배출되는 최신 항목을 결합하고 이 기능의 결과에 따라 항목을 배출합니다.

<img width="739" alt="image" src="https://user-images.githubusercontent.com/96224311/169683676-20346668-72ae-422a-ab8a-9fe47b5e4403.png">

```swift

let disposeBag = DisposeBag()

let left= PublishSubject<Int>()
let right = PublishSubject<Int>()

let observable = Observable.combinelatest(left, right, resultSelect: { lastLeft, lastRight in
  
  "\(lastLeft) \(lastRight)"
  
})

let disposable = Observable.subscribe(onNext: { value in 
  print(value)
})

left.onNext(45)
right.onNext(1) // 45 1
left.onNext(30) // 30 1
right.onNext(99) // 30 99
right.onNext(2) // 30 2
