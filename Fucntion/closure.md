## closure

```swift 
import UIKit

let hello: (String) -> () = { name in
    print("Hello \(name)!")
}

hello("Mary Doe")

let pow: (Int, Int) -> Int = {
    $0 * $1
}

let result = pow(5,3)
print(result)

func getPoest() -> [String] {
    
    var posts: [String] = []
    
    DispatchQueue.main.asyncAfter(deadline: .now() + 2) {
        posts = ["Hello World", "Introduction to Closures"]
    }
    
    return posts
}

print(getPoest()) // [] 출력 : 완료되지 않은 상황에서 return을 해버렸기 때문이다.



// 함수 내부에서 클로저를 전달하는 방법
// 함수를 다른 함수에 전달 할때 @escpaing 키워드가 필요하다.
// 비동기적으로 수행하는 모든 작업은 해당 특정 함수에 클로저를 전달해야 한다.
func getPosts(completion: @escaping ([String]) -> ())  {
    
    var posts: [String] = []
    
    DispatchQueue.main.asyncAfter(deadline: .now() + 2) {
        posts = ["Hello World", "Introduction to Closures"]
        completion(posts)
    }
    
}

getPosts { (posts) in
    print(posts)
}
```
