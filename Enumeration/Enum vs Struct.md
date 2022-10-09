## Enum과 Sturct를 비교해서 사용해보자 

```swift
struct Session {
    let title: String
    let speaker: String
    let data: Date
    let isKeynote: Bool
    let isWorkshop: Bool
    let isRecorded: Bool
    let isNormal: Bool
    let isJoinSession: Bool
    var jointSpeakers: [String]?
}
```
- 위와 같은 모델이 존재할 때, 해당 구조체를 사용하기 위해서 
```swift
let session = Session(title: "Introduction to Swift", speaker: "johndoe", data: Date(), isKeynote: false, isWorkshop: false, isRecorded: true, isNormal: true,  isJoinSession: false)
 ```
 
- 위의 문장처럼 사용해야한다. 
- 불필요한 정보들이 겹쳐서 사용해야 하는 needs가 발생한다. 
- isKeyNote, isWorkShop, isJoinSession 해당 여부는 한가지만 선택되는 남은 경우에서도 사용을 한다.


### Enum으로 바꿔보자
```swift
enum Session {
    case keynote(title: String, speaker: String, date: Date, isRecorded: Bool)
    case normal(title: String, speaker: String, date: Date)
    case workshop(title: String, speaker: String, date: Date, isRecorded: Bool)
    case joint(title: String, speakers: [String], date: Date)
}

let keynote = Session.keynote(title: "WWDC 2021", speaker: "Tim Cook", date: Date(), isRecorded: true)
```
- enum의 연관값을 사용하여 case문으로 분리하여 간단하게 생성을 한다.

```swift 
func displaySession(session: Session) {
    switch session {
        case let .keynote(title: title, speaker: speaker, date: date, isRecorded: isRecorded):
            print("\(title) - \(speaker) - \(date) - \(isRecorded)")
        case let .normal(title: title, speaker: speaker, date: date):
            print("\(title) - \(speaker) - \(date)")
        default:
            print("")
    }
    
    /* keynote에 관련해서만 사용하고 싶은경우 해당 구문으로 변경
    if case let Session.keynote(title: title, speaker: speaker, date: date, isRecorded: isRecorded) = session {
        // it is a keynote session
    } */
    
}

displaySession(session: keynote)
```

- Session을 보여주는 함수를 만들고자 할때, 다음과 같이 case let으로 접근하여 쉽게 생성이 가능하다.
 
