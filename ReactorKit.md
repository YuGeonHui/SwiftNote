# ReactorKit

- ReactorKit은 반응형 단방향 앱을 위한 프레임워크로, StyleShare와 Kakao를 비롯한 여러 기업에서 사용하고 있는 기술입니다.

![image](https://user-images.githubusercontent.com/96224311/167643534-838074fd-cfa6-46da-8ee5-97c8eda498f0.png)


# 뷰(View) 
- 뷰는 상태를 표현한다.
- 뷰 컨트롤러나 셀도 모두 뷰에 해당된다.
- 뷰는 사용자의 인터렉션을 추상화하여 리액터에 전달하고, 리액터에서 전달받은 상태를 각각의 뷰 컴포넌트에 바인드합니다.

- View 프로토콜을 적용하면 뷰를 정의할 수 있습니다. DisposeBag 속성과 bind(reactor:) 메서드를 필수로 정의해야 합니다.

```swift 
import ReactorKit
import RxSwift

class UserViewController: UIViewController, View {
  var disposeBag = DisposeBag()

  func bind(reactor: UserViewReactor) {
  }
}

``` 
- 이 프로토콜을 정의하면 reactor 속성이 자동으로 생성됩니다. 
- 이 속성에 새로운 값이 지정되면 bind(reactor:) 메서드가 자동으로 호출됩니다. 
- 이곳에는 사용자 인터랙션을 리액터에 바인드하거나, 리액터의 상태를 각각의 뷰 컴포넌트에 바인드하는 코드를 작성합니다.

# 리액터(Reactor)
- 뷰의 상태를 관리한다.
- 뷰에서 액션을 전달받으면 비즈니스 로직을 수행한 뒤 상태를 변경하여 다시 뷰에 전달합니다.
- 리액터는 UI레이어에서 독립적이기 때문에 비교적 테스트하기 쉽습니다.

