## Optional and Booleans

- RawRepresentable을 사용하여, raw value를 커스텀 해보자
- 아래와 같은 enum이 존재할때, true, false, nil에 대한 처리를 하고 싶은경우 사용한ㄷ.

```swift
import UIKit


enum UserAgreement: RawRepresentable {
    case accepted
    case rejected
    case notSet
    
    init(rawValue: Bool?) {
        switch rawValue {
            case true?: self = .accepted
            case false?: self = .rejected
            default: self = .notSet
        }
    }
    
    var rawValue: Bool? {
        switch self {
            case .accepted: return true
            case .rejected: return false
            case .notSet: return nil
        }
    }
    
}

let userAgreement = UserAgreement(rawValue: nil)

switch userAgreement {
    case .accepted:
        print("accepted")
    case .rejected:
        print("rejected")
    case .notSet:
        print("notSet")
}
```
