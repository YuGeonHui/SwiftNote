# UIDatePicker
- 날짜 및 시간 값을 입력하기 위한 컨트롤입니다.

## Picker Style
- picker를 나타내는 style을 알려준다.
- 버전에 따른 picker 이미지를 나타내 줄 수 있다.
```swift
picker.preferredDatePickerStyle = .wheels
```

## Picker Mode
- picker를 나타내는 모드를 설정해 줄 수 있다. 
```swift
picker.datePickerMode = .dateAndTime
```

## Picker Locale
- 기본 Locale은 아이폰 설정에 되어 있는 값으로 정해져 있다. 
```swift
picker.locale = Locale(identifier: "ko_kr")
```

## Picker Interval
- picker에서 나타낼 수 있는 간격을 나타내 준다.
- 60의 약수 값으로만 전달 해 줄 수 있다.
```swift
picker.minuteInterval = 1
```

## Picker Date Select
- picker에서 처음으로 선택된 값을 나타내 줄 수 있다.
```swift
picker.date = Date()
picker.setDate(Date(), animated: true) // 날짜 선택 (Animation)

picker.minimumDate = Date() // picker의 최소
picker.maximumDate = Date() // picker의 최대
```
## Calendar와 TimeZone 
- picker에서 Calendar와 TimeZone을 선택할 수 있다.
```swift
picker.calendar = Calendar.current
picker.timeZone = TimeZone.current
```

## Picker CountDown Example
```swift
import UIKit
import AudioToolbox

class CountDownTimerViewController: UIViewController {
    
    // 최소 1분 최대 23시간 59분
    @IBOutlet weak var timeLabel: UILabel!
    
    
    @IBOutlet weak var picker: UIDatePicker!
    
    @IBAction func start(_ sender: Any) {
        timeLabel.text = "\(Int(picker.countDownDuration))"
        
        remainingSeconds = Int(picker.countDownDuration)
        
        // Timer 제공 (타이머 중지 전까지 반복 실행)
        Timer.scheduledTimer(withTimeInterval: 1, repeats: true) { timer in
            
            self.remainingSeconds -= 1
            self.timeLabel.text = "\(self.remainingSeconds)"
            
            if self.remainingSeconds == 0 {
                timer.invalidate()
                
                AudioServicesPlaySystemSound(1315) // 완료 후 기본사운드를 틀어주기 위함.
            }
        }
    }
    
    var remainingSeconds = 0
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        picker.countDownDuration = 60 // 원하는 시간 초 단위로 입력한다. (1분)
    }
}
```










