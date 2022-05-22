# startWith

<img width="748" alt="image" src="https://user-images.githubusercontent.com/96224311/169682889-5374263a-4941-4ccb-9070-e5bc24ba218b.png">

- 값을 방출하기 전에, 해당 값을 맨 처음으로 포함하여 방출한다. 

```swift

let disposeBag = DisposeBag()

let numbers = Observable.of(2, 3, 4)

let observable = numbers.startWith(1)
observable.subscribe(onNext: {
  print($0) // 1, 2, 3, 4
}
```
