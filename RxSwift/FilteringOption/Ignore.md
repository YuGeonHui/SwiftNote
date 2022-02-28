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
  .disposed(by: disposeBag)
  
strikes.onNext("0")
strikes.onNext("1")
strikes.onNext("2") // Return이 출력된다. 
```
# Filter 
- 해당 조건을 클로저를 만족하는 값만 넘어가는 함수 
```swift
Observable.o9f(1, 2, 3, 4, 5, 6, 7)
  .filter { $0 % 2 == 0 }
  .subscribe(onNext: { print($0) }
  .disposed(by: disposeBag) // 2, 4, 6이 출력된다. 
```

# Skip 
- 해당 값에 들어 온 값 만큼 skip하는 함수  

# SkipWhile
- next 이벤트를 금지 시키는 필터이다.
- completed(), error()는 사용이 가능하다. 

# SkipUntil 
- next 이벤트를 금지 시키는 필터이다.
- completed(), error()는 사용이 가능하다. 

# Take 
- 해당 값에 들어 온 값 만큼만 출력하는 함수 

# TakeWhile 
- 특정조건이 거짓이 되면 더 이상 항목을 제공하지 않는다.

# TakeUntil 
- next 이벤트를 금지 시키는 필터이다.
- completed(), error()는 사용이 가능하다. 
