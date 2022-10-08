## 배열 내부에서의 Array 
- 큰 항목이 존재하는 경우에서 하위의 목록이 필요한 경우 ```lazy```를 사용한다.

```swift 
import UIKit

let indexes = 1..<5000

// 일반적인 filter를 사용하는 경우 : 5000번 이후 map으로 진행한다.
// 긴 목록이 있고 해당 항목의 하위 집합만 원하는 경우 lazy를 사용한다.
let images = indexes.lazy.filter { index -> Bool in
    print("[filter]")
    return index % 2 == 0
}.map { index -> String in
    print("[Map]")
    return "image_\(index)"
}

let lastThreeImages = images.suffix(3) // 마지막 3개의 이미지의 도달하기 위해서
for img in lastThreeImages {
    print(img)
}
```
