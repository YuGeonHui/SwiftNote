# Ignore 
- next 이벤트를 금지 시키는 필터이다.
- completed(), error()는 사용이 가능하다. 

# ElementAt 
- Observable에서 발생하는 이벤트 중 n번째 이벤트만 받고 싶은 경우 사용한다. 
- n만큼 들어오고 나서 값이 출력되는 것을 볼 수 있다.

```swift
let strikes = PublishSubject<String>()
let disposeBag = DisposeBag()

strikes.elementAt(2)
  .subscribe(onNext: { print("Return") }
  .disposed(by: self.disposeBag)
  
strikes.onNext("0")
strikes.onNext("1")
strikes.onNext("2") // Return이 출력된다. 
```
# Filter 
- 해당 조건을 클로저를 만족하는 값만 넘어가는 함수 
```swift
Observable.of(1, 2, 3, 4, 5, 6, 7)
  .filter { $0 % 2 == 0 }
  .subscribe(onNext: { print($0) } // 2, 4, 6이 출력된다. 
  .disposed(by: self.disposeBag) 
```
## Skip과 take 연산자는 서로 비슷하지만 아예 다른 연산자이다.

# Skip 
- 해당 연산자에 들어오는 값만 큼 이벤트를 무시 할 수 있는 함수   
```swift
Observable.of("A", "B", "C", "D", "E", "F")
  .skip(4)
  .subscribe(onNext: { print($0) } // E, F이 출력된다. 
  .disposed(by: self.disposeBag)  
```

# SkipWhile
- 처음으로 해당 조건을 만족하지 못한 이벤트가 나타나면, 그 이후 값들은 모두 전달된다.
```swift
Observable.of(2, 2, 3, 4, 4)
  .skipWhile { $0 % 2 == 0 }
  .subscribe(onNext: { print($0) } // 3, 4, 4이 출력된다. 
  .disposed(by: self.disposeBag)  
```

# SkipUntil 
- 두개의 시퀀스가 존재할 때, 두 시퀀스에서 모두 .next이벤트가 발생해야 값을 전달한다.
```swift
let subject = PublishSubject<String>()
let triger = PublishSubject<String>()
let disposeBag = DisposeBag()

subject.skipUntil(triger)
  .subscribe(onNext: { print($0) }
  .disposed(by: self.disposeBag)
  
subject.onNext("0")
subject.onNext("1")

triger.onNext("trigger!!!")
subject.onNext("3") // 3
```

# Take 
- skip과 정반대의 개념을 지니고 있다.
- 처음 발생하는 n개의 이벤트만 출력이 가능하다.
```swift
Observable.of(1, 2, 3, 4, 5, 6)
  .take(3)
  .subscribe(onNext: { print($0) } // 1, 2, 3이 출력된다. 
  .disposed(by: self.disposeBag)  
```

# TakeWhile 
- 특정조건이 거짓이 되면 그 이후의 모든 이벤트는 무시가된다. 
```swift
Observable.of(2, 4, 6, 7, 8, 10)
  .takeWhile { return $0 % 2 == 0 }
  .subscribe(onNext: { print($0) } // 2, 4, 6이 출력된다. 
  .disposed(by: self.disposeBag)  
```

# TakeUntil 
- 두개의 시퀀스가 존재할 때, 두 시퀀스에서 모두 .next이벤트가 발생하는 경우 전달을 멈춘다.
```swift
let subject = PublishSubject<String>()
let triger = PublishSubject<String>()
let disposeBag = DisposeBag()

subject.takeUntil(triger)
  .subscribe(onNext: { print($0) }
  .disposed(by: self.disposeBag)
  
subject.onNext("0")
subject.onNext("1") // 0, 1 출력 

triger.onNext("trigger!!!")
subject.onNext("3") // 더 이상 값이 출력되지 않는다. 
```
