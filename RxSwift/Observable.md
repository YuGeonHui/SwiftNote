# Observable 이란 

## Observable의 전체 개념은 구독(Subscribe)할 수 있고, 해당 이벤트를 얻을 수 있다. 
### 1) Just: Observable의 1개의 원소를 그대로 방출
```swift
let observable = Observable.just(1) 
observable.subscribe(onNext: { element
  print(element)
})
```
### 2) of : 원소 여러개 출력 (배열인 경우 배열 그대로 출력) 
```swift
let observableNormal = Observable.of(1, 2, 3)
let observableArray = Observable.of([1, 2, 3])

observableNormal.subscribe(onNext: { element
  print(element)
})

observableArray.subscribe(onNext: { element
  print(element)
})

```
### 3) from : 배열에 있는 원소를 하나씩 출력 
```swift
let observable = Observable.from([1, 2, 3, 4 ,5])
observable.subscribe(onNext: { element
  print(element)
})
```
