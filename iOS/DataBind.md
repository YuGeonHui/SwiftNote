# Swift 내부에서 데이터를 binding 하는 방법

> DataBinding 이란 ?
- View Model과 View Controller는 서로에게 데이터의 변경을 알려줄 수 있는 방법이 필요합니다.
- 그 방법을 DataBinding 이라고 한다.

> DataBiding의 종류
1. Observables
2. Event Bus / Notification Center
3. FRP Technique (RxCocoa / RxSwift)
4. Combine


## Notification Center 
- Notification Center에 등록된 event가 발생하면 해당 event에 대한 행동을 취한다. 
- 앱 내부에서 메세지를 던지면, 아무데서나 이 메세지를 받을 수 있게 하는 역할을 한다.
- 현재 작업과 다른 흐름의 작업으로 부터 이벤트를 받을 때 사용 
> Ex) 백그라운드 작업의 결과, 비동기 작업의 결과 

![image](https://user-images.githubusercontent.com/96224311/174485126-92e4e384-7b50-47ab-b5fe-3a1fff5231a6.png)

### NotificationCenter를 통해 정보를 저장하기 위한 구조체입니다.
```swift
var name: Notification.Name // 알림을 식별하는 태크
var object: Any? // 발송자가 옵저버에게 보내려고 하는 객체, 주로 발송자 객체를 전달하는데 쓰임
var userInfo: [AnyHashable : Any]? // Notification과 관련된 값 또는 객체의 저장소 
```
### Notification Center
- 등록된 observer에게 동시에 notification을 전달하는 클래스 입니다.
- NotificationCenter는 notification 을 발송하면, NotificationCenter에서 메세지를 전달한 observer를 처리할 때까지 대기합니다.
- 흐름이 동기적으로 흘러간다.

```swift 
// 노티피케이션 발송
NotificationCenter.default.post(name: NSNotification.Name("TestNotification"), object: nil, userInfo: nil)
 
// 옵저버 등록
NotificationCenter.default.addObserver(self, selector: #selector(didRecieveTestNotification(_:)), name: NSNotification.Name("TestNotification"), object: nil)

@objc func didRecieveTestNotification(_ notification: Notification) {
  print("Test Notification")
}
```
- ```.post``` : Name의 해당자들에게(옵저버) 일을 수행하라고 시킨다.
- ```addObserver``` : 관찰자를 대기시킨다.
- ```selector``` : 관찰자가 수행 할 업무를 의미한다. 

### Name 등록 방식 
1. addObserver 할 때 한번에 하기 
```swift
// Post
NotificationCenter.default.post(name: Notification.Name("doItSomeThing"), object: nil)

// Add Observer
NotificationCenter.default.addObserver(self, selector: #selector(printSomeThing(_:)), name: Notification.Name("doItSomeThing"), object: nil)
```

2. Extentsion으로 property 추가 

```swift
extenstion Notification.Name {
  static let doItSomeThing = Notification.Name("doItSomeThing")
}

```
### Post 값 전달하기 
- Post 메소드 파라미터에 object가 존재햔다.
- object의 값을 넣어 보낼 수 있다.

```swift
NotificationCenter.default.post(name: .testnoti, object: "testObject")

@objc func getValue(_ notification: Notification){
	let getValue = notification.object as! String
	print(getValue)
}
```
 
 
 
 
 
 
 
 
 
