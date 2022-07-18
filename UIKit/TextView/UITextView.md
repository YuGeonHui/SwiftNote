# UITextView
- UITextField와 같이 입력을 받지만, multiLine에 최적화 되어있다. (UITextField 단일 행)
- MultiLine을 지원하기 때문에, Scroll 또한 지원한다.
- Text를 출력할 때, 사용한다.

## Behavior
- Editable : 수정이 가능하게 하는 옵션
- Selectalbe : 선택을 할 수 있게 하는 옵션

## Padding 
- Top, Bottom : 8, leading, Trailing : 0
- textContainerInset을 사용하여 Padding을 적용할 수 있다. (UIEdgeInsets)
- 위의 속성을 사용하는 경우에는, Indicator에도 같은 속성을 제공해야 한다.

```swift
@IBOutlet weak var textView: UITextView!
    
  override func viewDidLoad() {
    super.viewDidLoad()
        
    textView.textContainerInset = UIEdgeInsets(top: 30, left: 0, bottom: 30, right: 0)
    textView.scrollIndicatorInsets = UIEdgeInsets(top: 30, left: 0, bottom: 30, right: 0)
}
```
