# Subject

## Observable인 동시에 Observer인 존재이다.
## 이벤트를 전달 받을 수 있고, 이벤트를 전달 할 수 있다. 
## onNext, subscribe 모두 가능하다. 

- PublishSubject
- BehaviorSubject
- ReplaySubject

## PublishSubject

- Subject로 전달된 이벤트를 Observer에게 전달하는 기본적인 Subject 이다.
- 생성 시, 파라미터 를 전달하지 않는다. 
- 구독 이후에 전달되는 새로운 값만 받을 수 있다. (이전 onNext는 전달 되지 않는다.) 
- onCompleted() 이후에는 onNext 이벤트 이후에도 출력되지 않는다. 

```swift
let subject = PublishSubject<String>()
  
subject.onNext("Test1") // 전달되지 않는다.  
  
subject.subscribe { event in
  print(event)  
}  
  
subject.onNext("Test2") // 구독이후 이기 때문에 전달 가능하다.
subject.onNext("Test3") // 구독이후 이기 때문에 전달 가능하다.
  
subject.onCompleted() 
subject.onNext("Test3") // onCompleted() 가 출력되었기 때문에 해당라인은 무시된다.  
```
