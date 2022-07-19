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

## AttachView 
- textView내부에 Image를 Attach하는 경우 사용한다.
- NSTextAttach()를 사용해서 구현한다. 
```swift
class ImageAttachmentViewController: UIViewController {
    
    @IBOutlet weak var textView: UITextView!
    
    let logo = UIImage(named: "logo")
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let attachment = NSTextAttachment()
        attachment.image = logo
        
        let attStr = NSAttributedString(attachment: attachment)
        textView.textStorage.insert(attStr, at: 0)
    }
}
```

## Selection 
- TextView 내부에서 해당되는 문자를 찾을 수 있다.
- scrollToRange 메서드를 사용하여, 해당 문자열로 이동도 가능하다.
```swift 
class TextSelectionViewController: UIViewController {
    
    @IBOutlet weak var textView: UITextView!
    
    @IBOutlet weak var selectedRangeLabel: UILabel!
    
    @IBAction func selectLast(_ sender: Any) {
        
        let lastWord = "pariatur?"
        
        if let text = textView.text as NSString? {
            
            let range = text.range(of: lastWord)
            textView.selectedRange = range
            textView.scrollRangeToVisible(range)
        }
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
                
    }
}

extension TextSelectionViewController: UITextViewDelegate {
    
    func textViewDidChangeSelection(_ textView: UITextView) {
        
        let range = textView.selectedRange
        selectedRangeLabel.text = "\(range)"
    }
    
}
```
