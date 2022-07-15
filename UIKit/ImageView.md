# ImageView

- 이름 그대로, 이미지를 표시하는 View
- ContentMode는 기본적으로 ```.aspectFit```을 사용한다.
- 이미지 상태를 바꾸는 경우, highlighted 상태를 바꾸는 것이 좋다. (이미지 교체 보다 효율적)

## Image Sequence
- 이미지 시퀀스를 사용하여 .gif와 같은 효과를 줄 수 있다. 
- 여러 이미지를 반복적으로 (이미지 배열) 사용하여 효과를 준다.

```swift 

imageView.animationImages = images // images는 이미지 배열
imageView.animationDuration = 1.0 (전체 duration)
imageView.animationRepeatCount = 3 (0으로 setting시 무한 반복)

imageView.startAnimating() // 애니메이션 시작 

If imageView.isAnimating { // 애니메이션 종료
	imageView.stopAnimating
}
```

## Asset 라이브러리 
- xCode에는 Aseest 라이브러리를 사용할 수 있다.
- 사이즈는 1x, 2x, 3x를 사용한다. (현재 1x는 사용을 안한다고 봐도 무방하다.)
- 이미지 이름에 @1x, @2x, @3x를 사용하여 넣어주는 경우 바로 적용이 가능하다.
- Device를 다양하게 추가가 가능하다. (Asset라이브러리가 앱을 다운로드 할때 최적의 값만 다운로드 해준다.)

## 이미지를 바이너리 형식으로 바꾸는 방법 

- compressionQuality은 0.0에서 1.0 까지 선택이 가능하다. (높을수록 좋은 quality)
```swift
let pngData = img1?.pngData()
let jpgData = img1?.jpegData(compressionQuality: 1.0) 
```

## UIimage 크기를 구하는 방법 

```swift 
if let ptSize = img1?.size {
  print("Image Size : \(ptSize)")
}
        
if let ptSize = img1?.size, let scale = img1?.scale {

  let px = CGSize(width: ptSize.width * scale, height: ptSize.height * scale)
  print("Image Size(px) : \(px)")
}
```
 

