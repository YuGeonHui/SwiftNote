## TImeLineView

- TimeLineView를 통하여 구현 할 수 있다.
- 1초마다 스케줄러를 실행시켜 화면에 표출 할 수 있다.
```swift
TimelineView(PeriodicTimelineSchedule(from: Date(), by: 1)) { context in
    Text("\(context.date)")
}
```
