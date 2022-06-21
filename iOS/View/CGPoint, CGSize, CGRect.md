# CGPoint, CGSize, CGRect

- iOS에서 View를 그리기 위해서는 필요한것 
1. x, y 좌표 -> CGPoint(CGFloat)
2. width, height -> CGSize(CGFloat)

- CGRect -> CGPoint와 CGSize를 품은 객체 

```swift
public struct CGPoint {

  public var x: CGFloat
  public var y: CGFloat
  public init()
  public init(x: CGFloat, y: CGFloat)
}
```

