# ToArray
- Observable에서 단일 요소들을 배열로 바꿔주는 연산자이다.

```swift
Observable.of(1, 2, 3, 4, 5).toArray()
  .subscribe(onNext: { print($0) } // [1, 2, 3, 4, 5] 배열로 변경되어 출력 
  .disposed(by: disposeBage)
```

# Map
- 배출하는 연산 각각에 대하여 map 내부에 있는 형태로 변환해준다.

```swift
Observable.of(1, 2, 3, 4, 5)
  .map { return $0 * 2 }
  .subscribe(onNext: { print($0) } // 2, 4, 6, 8, 10  
  .disposed(by: disposeBage)
```

# FlatMap

```swift
struct Student {
  var score: BehaviorRelay<Int>
}
   
```

# FlatMapLatest 
