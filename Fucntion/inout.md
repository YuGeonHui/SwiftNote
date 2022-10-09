# inOut
- copy-in copy-out
- 함수 매개 변수는 기본적으로 상수(Constant)입니다.
- 함수 매개 변수의 값을 해당 함수의 본문 내에서 변경하려고 하면 compile-time 오류가 발생합니다.
- 함수에서 매개 변수의 값을 수정하고 함수 호출이 종료된 후에도 변경 사항을 유지하려면 inout 파라미터를 사용하면 됩니다.

```swift
import UIKit

// In-Out Parameters

struct User {
    var userId: Int?
    let name: String
}

// compile 에러를 막기 위한 값 복사 방법
func saveUserWithCopy(_ user: User) -> User {
    
    // code to save the user
    var copyUser = user
    copyUser.userId = 100
    
    return copyUser
}

// inout 키워드를 사용한 파라미터 
func saveUser(_ user: inout User) {

    // code to save the user
    user.userId = 100
}

// inout 키워드를 사용할때, 내부에서 변경할 수 있는 인수가 들어가야 한다.
var user = User(name: "John Doe")
saveUserWithCopy(user)
saveUser(&user)

print(user)
```
