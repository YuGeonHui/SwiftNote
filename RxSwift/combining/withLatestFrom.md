# withLatestFrom 

- 방출하는 값 중에서, 가장 최신의 값을 방출해준다. 

```swift

let disposeBag = DisposeBag()

let button = PublishSubject<Void>() 
let textField = PublishSubject<String>()

let observable = button.withLatestFrom(textField)
let disposable = observable. subscribe(onNext: [
  print($0)
})

textField.onNext("Sw")
textField.onNext("Swif")
textField.onNext("Swift")

button.onNext(()) // Swift
button.onNext(()) // Swift 

```

