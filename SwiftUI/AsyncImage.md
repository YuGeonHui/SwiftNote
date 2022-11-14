## AsyncImage (iOS15 이상)

- SwiftUI에서는 ```AsyncImage```를 사용하여 이미지의 상태를 표핸할 수 있다.

```swift 
let testURL = URL(string: "")!
AsyncImage(url: testURL) { phase in
    if let image = phase.image {
      image
    } else if phase.error != nil {
      Image(systemName: "exclamationmark.circle")
    } else {
      Image(systemName: "photom")
    }
}
```

- 의의 문장을 해석해보면, 이미지가 존재하는 겨웅 이미지를 출력해준다.
- 에러가 존재하는 경우 에러와 관련된 이미지를 표출해준다.
- 이미지 로드가 진행 중이지만, 보여주기 전까지를 보여주는 이미지도 출력해준다.
