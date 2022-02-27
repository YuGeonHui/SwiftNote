# Subject

## Observable인 동시에 Observer인 존재이다.
## 이벤트를 전달 받을 수 있고, 이벤트를 전달 할 수 있다. 
## onNext, subscribe 모두 가능하다. 

- PublishSubject
- BehaviorSubject
- ReplaySubject

### PublishSubject

- Subject로 전달된 이벤트를 Observer에게 전달하는 기본적인 Subject 이다.
- 생성 시, 파라미터 를 전달하지 않는다. 
- 구독 이후에 전달되는 새로운 값만 받을 수 있다. (이전 onNext는 전달 되지 않는다.) 
- onCompleted() 이후에는 onNext 이벤트 이후에도 출력되지 않는다. 

```swift
let subject = PublishSubject<String>()
  
subject.onNext("Item1") // subject를 구독하지 않아 전달되지 않는다.  
  
subject.subscribe { event in
  print(event)  
}  
  
subject.onNext("Item2") // 구독이후 이기 때문에 전달 가능하다.
subject.onNext("Item3") // 구독이후 이기 때문에 전달 가능하다.
  
subject.onCompleted() 
subject.onNext("Item4") // onCompleted() 가 출력되었기 때문에 해당라인은 무시된다.  
```

### BehaviorSubject 

- 초기 값을 설정해야 하는 Subject 이다.
- 구독 하는 시점에서 과거에 갱신된 데이터중 가장 최근의 값이 필요할 때 사용하면 좋다.

```swift
let subject = BehaviorSubject<String>(value: "Initial Value")
  
subject.subscribe { event in
  print(event)   // 초기 값이 출력된다.   
}  

subject.onNext("Item1") 
```

### ReplaySubject 

- 버퍼 크기를 기반으로 하는 Subject 
- 해당 Subject의 bufferSize만큼의 값을 방출 시킨다.
- Buffer를 이용하기 때문에 메모리 누수를 조심해야 한다. 

```swift
let subject = ReplaySubject<String>.create(bufferSize: 2)
  
subject.onNext("Item1") 
subject.onNext("Item2") 
subject.onNext("Item3") 

subject.subscribe { event in
  print(event)   // Test2, Test3가 출력된다.  
}  
```
