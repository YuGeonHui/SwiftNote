# ImageView

- 이름 그대로, 이미지를 표시하는 View
- ContentMode는 기본적으로 ```.aspectFit```을 사용한다.
- 이미지 상태를 바꾸는 경우, ```highlighted``` 상태를 바꾸는 것이 좋다. (이미지 교체 보다 효율적)
- 백터 이미지를 사용하는 경우 -> single Scale / VectorData 선택 (Vector Data는 iOS 버전 13이상 추천)

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

## UIImage Custom 방법 

- draw 메서드를 사용하여 Custom 한다.
```swift
let starImg = UIImage(systemName: "star")
let bellImg = UIImage(systemName: "bell")
let umbrellaImg = UIImage(systemName: "umbrella")
    
 // Custom View
 override func draw(_ rect: CGRect) {
 super.draw(rect)
         
    starImg?.draw(at: CGPoint(x: 0, y: 0))
    bellImg?.draw(in: CGRect(x: 0, y: 80, width: 100, height: 100))
        
    umbrellaImg?.drawAsPattern(in: rect)
}
```

## UIImage를 Resize 하는 방법 

- 대표적인 방법으로 Context, Bitmap 방식이 존재한다.
1. Context 방식으로 Resize -> 방식이 간단하여 해당방법을 사용하는 경우가 많다.

```swift 
func resizingWithImageContext(image: UIImage, to size: CGSize) -> UIImage? {
    
    UIGraphicsBeginImageContextWithOptions(size, true, 0.0)
        
    let frame = CGRect(origin: .zero, size: size)
    image.draw(in: frame)
    let resultImage = UIGraphicsGetImageFromCurrentImageContext()
        
    UIGraphicsEndImageContext()
    return resultImage
}
```

2. Bitmap 방식으로 Resize

```swift
func resizingWithBitmapContext(image: UIImage, to size: CGSize) -> UIImage? {
        
    guard let cgImage = image.cgImage else { return nil }
        
    let bpc = cgImage.bitsPerComponent
    let bpr = cgImage.bytesPerRow
    let colorSpace = cgImage.colorSpace!
    let bitmapInfo = cgImage.bitmapInfo
        
    guard let context = CGContext(data: nil, width: Int(size.width), height: Int(size.height), bitsPerComponent: bpc, bytesPerRow: bpr, space: colorSpace, bitmapInfo: bitmapInfo.rawValue) else { return nil }
        
     context.interpolationQuality = .high
        
    let frame = CGRect(origin: .zero, size: size)
        
    context.draw(cgImage, in: frame)
    guard let resultImage = context.makeImage() else { return nil }
    
    return UIImage(cgImage: resultImage)
}
```

