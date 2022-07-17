# TextView

## Label 
- 하나 이상의 정보 텍스트를 표시하는 View.

### Label의 속성 
1. numberOfLines : Label에서 보여줄 수 있는 라인 수를 의미한다. (Int)
> 0을 대입할 경우, 해당 Label에 속해있는 모든 텍스트를 다 보여준다. 

2. textColor : 라벨의 색상을 적용할 수 있다. (UIColor)
3. alignment : Label의 정렬 방식을 적용할 수 있다. (NSTextAlignment)
4. LineBreakMode : Label이 잘릴 경우 어떠한 방식으로 자를 지를 선택 할 수 있다. (NSLineBreakMode)

### Label의 폰트를 적용 시키는 방법 (UIFont)
- 라벨의 폰트크기를 바로 적용 시킬 수 없다. (Read-Only)
- 새로운 폰트를 생성해서 Label에 적용시켜준다. 
```swift
 @IBAction func updateFontSize(_ sender: UIStepper) {
        
    let newSize = CGFloat(sender.value)
        
    // 폰트크기를 바로 적용할 수 없음(read-only)
    // 새로운 폰트를 생성해서 넣어준다.
    let newFont = valueLabel.font.withSize(newSize)
    valueLabel.font = newFont
}
```

### Label에서 코드로 AutoShrink를 적용 시키는 방법 
- auto shrink의 속성을 지원하지 않기 때문에, ```minimumScaleFactor```, ```adjustsFontSizeToFitWidth```을 조합해서 사용한다.
```swift
// Example
autoshrinkSwitch.isOn = valueLabel.minimumScaleFactor != 0 && valueLabel.adjustsFontSizeToFitWidth
```
