# Coding Convetion이란?
- 코딩을 하는 프로그래머 사이의 규칙을 의미합니다.
- 코딩 규칙을 지킨다면 다른 개발자가 개발한 소스코드를 처음 보았을 때 더 빠른 시간 안에 완벽하게 이해할 수 있도록 도와주기 때문에, 소프트웨어의 가독성이 높아진다고 합니다.

1. 코드 포매팅

1-1 ## import 
- 모듈 임포트는 알파벳 순으로 정렬합니다.
- 내장 프레임워크를 먼저 import하고, 빈줄로 구분에 써드파티 프레임워크를 임포트 합니다.

```swift
import UIKit

import SwiftyColor
import SwiftyImage
import Then
import URLNavigator

```
1-2 ## 빈줄
- 빈 줄에는 공백이 포함되지 않도록 합니다.
- 모든 파일은 빈줄로 끝나도록 합니다.

1-3 ## 들여쓰기 
- Tab을 눌렀을 시, 4개의 Space를 사용합니다.
- 들여쓰기는 Xcode에서 제공하는 ^ + i 를 눌렀을 때, 적용되는 space를 사용합니다.
- 최대 가로 길이는 100 characters를 사용합니다.

1-4 ## 띄어쓰기
- 콜론(:)을 사용할 때는 콜론의 오른쪽에만 공백을 둡니다.
- 삼항 연산자의 경우 콜론 앞뒤로 띄웁니다. 
- 일반적으로 콤마(,) 뒤네는 공백을 추가합니다.

```swift
let name: [String: String]?

class MyClass: SuperClass { } 

func application(_ application: UIApplication, supportedInterfaceOrientationsFor window: UIWindow?) -> UIInterfaceOrientationMask {
	return shouldRotate ? .allButUpsideDown : .portrait
}

```

