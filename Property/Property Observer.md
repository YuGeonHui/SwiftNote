## Property Observer 

- Property Observer를 정의해서 프로퍼티의 값을 모니터링 할 수 있다.
- didSet, willSet으로 사용 할 수 있다.
- didSet 구문을 통해, 값이 전달되 었을 때 해당 구문이 실행됨을 알 수 있다. (defer문으로 마지막에 url을 넣어줌)

```swift 
import UIKit


struct Website {
    
    init(url: String) {
        
        defer { self.url = url }
        
        self.url = url
    }
    
    var url: String {
        
        didSet {
            url = url.addingPercentEncoding(withAllowedCharacters: .urlHostAllowed) ?? url
        }
    }
    
}

var website = Website(url: "www.movies.com/?search=Lord of the Rings")
//website.url = "www.movies.com/?search=Lord of the Rings"
print(website)

// www.movies.com%2F%3Fsearch=Lord%20of%20the%20Rings
```
