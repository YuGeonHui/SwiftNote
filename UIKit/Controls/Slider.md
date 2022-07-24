# UISlider
- 연속형 값 범위에서 단일 값을 선택하기 위한 컨트롤입니다.
![image](https://user-images.githubusercontent.com/96224311/180641122-8c33bd5d-77f3-43cd-9098-a7e5c976b756.png)

## UISlider value
- value : UISlider에 값을 기본적으로 설정해주고 싶을 때 사용한다. (Float)
- setValue : 값을 지정해주나, 애니메이션과 함께하고 싶을 때 사용한다. (Float)
- inContinuous : Slider의 이벤트가 끝나고나서 받을지, 연속적으로 받을지 적용한다. (Bool)

## UISlider Custom
```swift
class CustomSliderViewController: UIViewController {
    
    @IBOutlet weak var slider: UISlider!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let img = UIImage(systemName: "lightbulb")
        
        slider.setThumbImage(img, for: .normal)
        slider.minimumTrackTintColor = UIColor.red
        slider.maximumTrackTintColor = UIColor.black
    }
}
```
